---
icon: shield-check
description: ERC20/ERC721/ERC1155 代币授权与取消授权操作指南
---

# 代币授权与取消授权

> **TokenTools 是一款区块链工具箱，支持 ETH、BSC等超多公链，提供可视化的代币授权管理功能，帮助用户安全地管理代币授权、检测风险授权记录并及时取消不必要的授权。**

> **点击加入 [TokenTools 官方交流群](https://t.me/tokentool_app) 交流反馈**

> **推荐使用电脑版谷歌浏览器 + MetaMask 插件钱包进行操作。**
> **手机用户也可以在 TP 钱包-发现-输入官网链接进行操作。**

---

## 一、什么是代币授权（Approve）

代币授权是指用户将指定代币的使用权限授予某个智能合约地址，使该合约能够在授权额度范围内代替用户操作代币。这是 ERC20 标准中 `transferFrom()` 机制的核心前提。

常见应用场景：

- DEX 交易（PancakeSwap、Uniswap）
- 添加流动性
- NFT 市场交易
- 质押（Stake）与挖矿（Farm）
- 自动化交易机器人
- 第三方 DApp 调用

---

## 二、操作入口

打开 [TokenTools 自定义授权页面](https://tokentools.app/approve/eth)，进入页面后请确认当前钱包已连接，并切换到对应网络（如 BSC Mainnet、Ethereum Mainnet、Arbitrum、Polygon 等）。

---

## 三、页面功能说明

### 左侧快捷授权区域

系统内置了常用协议的授权入口，点击 `GET` 即可自动填充对应合约地址：

| 协议 | 说明 |
| --- | --- |
| Uniswap V2 | Uniswap V2 Router |
| Uniswap V3 | Uniswap V3 Router |
| OpenSea Offer | OpenSea NFT 授权 |
| PancakeSwap | PancakeSwap Router |

### 右侧授权面板

支持两种资产类型：**Token** 和 **NFT**（含 ERC721、ERC1155），默认选择 Token。

---

## 四、Token 授权操作步骤

#### 1、选择资产类型

在右侧面板选择 **Token**。

#### 2、选择操作类型

选择 **授权** 或 **取消授权**：

- **授权**：允许目标合约使用当前代币
- **取消授权**：将授权额度设置为 0，用于撤销风险授权

#### 3、填写代币地址

输入需要授权的代币合约地址，例如：

- USDT (BSC)：`0x55d398326f99059fF775485246999027B3197955`
- CAKE (BSC)：`0x0E09FaBB73Bd3Ade0a17ECC321FD13a19e81cE82`

#### 4、填写授权合约地址

输入需要获得授权的智能合约地址，例如：

- PancakeSwap V2 Router：`0x10ED43C718714eb63d5aA57B78B54704E256024E`
- Uniswap V2 Router：`0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D`

#### 5、检查授权状态

点击**检查授权状态**，系统将读取链上授权记录，显示当前授权额度、授权对象和授权状态。

如果显示 `MAX_UINT256`（即 `115792089237316195423570985...`），表示当前为**无限授权**。

#### 6、确认操作

点击**确认操作**，钱包将弹出签名窗口。核对 Gas Fee、授权对象和授权额度无误后，点击**确认**，等待区块确认完成即可。

---

## 五、取消授权操作

操作流程与授权类似，选择 **取消授权** 后，填写代币地址和授权合约地址，点击确认即可。钱包会执行 `approve(spender, 0)`，将授权额度归零。

> ⚠️ **安全建议**：定期检查并清理历史授权记录，对于不再使用的 DApp 或可疑合约，应及时取消授权。

---

## 六、NFT 授权操作

NFT 授权支持 **ERC721** 和 **ERC1155** 两种标准。切换至 NFT 模式后：

| 授权类型 | 对应方法 | 说明 |
| --- | --- | --- |
| 单个 NFT 授权 | `approve()` | 仅授权某个 NFT |
| 全部 NFT 授权 | `setApprovalForAll()` | 授权整个 NFT 集合 |

操作流程：选择 NFT → 输入 NFT 合约地址 → 输入授权对象地址 → 检查授权状态 → 确认操作。

---

## 七、授权状态说明

| 状态 | Allowance | 说明 |
| --- | --- | --- |
| 未授权 | = 0 | 当前合约无权限操作代币 |
| 有限授权 | = 指定数量（如 1000 USDT） | 只能操作对应额度 |
| 无限授权 | = MAX_UINT256 | 授权对象可无限使用该代币 |

---

## 八、常见授权地址（BSC）

- **PancakeSwap V2 Router**：`0x10ED43C718714eb63d5aA57B78B54704E256024E`
- **PancakeSwap V3 Router**：`0x13f4EA83D0bd40E75C8222255bc855a974568Dd4`
- **WBNB**：`0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c`
- **USDT (BSC)**：`0x55d398326f99059fF775485246999027B3197955`

---

## 九、常见问题

**Q1：为什么交易前必须授权？**

因为 ERC20 标准规定，`transferFrom()` 方法必须获得持币人授权后才能执行，DEX 和 DeFi 协议依赖此机制完成代币兑换、添加流动性等操作。

**Q2：授权失败怎么办？**

请检查以下事项：
- 钱包余额是否足够支付 Gas 费
- 代币地址是否正确
- 授权地址是否正确
- 网络是否切换到正确的链

**Q3：授权后还能撤销吗？**

可以。选择**取消授权**操作即可撤销，将授权额度重新设置为 0。

**Q4：无限授权安全吗？**

存在风险。如果授权给恶意合约，理论上对方可以通过 `transferFrom()` 转走你的全部代币。建议：
- 仅授权给可信协议和已验证的官方合约
- 定期使用 [TokenTools 批量取消授权](https://tokentools.app/approve/eth) 检查授权记录
- 不使用时及时取消不必要的授权

---

## 十、安全提示

- ⚠️ 请务必确认授权对象为**官方合约地址**，谨防钓鱼网站伪造合约
- ⚠️ 不要向陌生 DApp 进行无限授权
- ⚠️ 授权前请核对：代币地址、合约地址、网络环境
- ⚠️ 建议定期使用 TokenTools 检查并清理历史授权记录

> 原文链接：[https://docs.tokentools.app/other/approve](https://docs.tokentools.app/other/approve)
>
> 更多安全知识：
> [https://medium.com/zengo/unicats-go-phishing-eaf39ff9da64](https://medium.com/zengo/unicats-go-phishing-eaf39ff9da64) — UniCats 钓鱼分析
>
> [https://www.lianzixun.cn/news/9562620.html](https://www.lianzixun.cn/news/9562620.html) — 转账授权钓鱼，控制你的钱包
