---
icon: money-bill-trend-up
---

# Orca 创建/移除流动性教程

[Orca](https://www.orca.so/) 是 Solana 链上较为知名的去中心化交易平台之一。相比 Raydium，Orca 上创建流动性池的成本更低（通常少于 0.5 SOL）。此外，许多用户更倾向于在 Orca 上创建 **USDC 交易对**，因为相比于 SOL 池，USDC 池能有效降低无常损失，不受 SOL 价格波动影响。

## ⚠️ 使用 Orca 创建池子的注意事项

- 一些自动化交易机器人无法识别 Orca 上的新流动性池，可能无法进行挂单或交易操作。
- OKX Web3 钱包的 Swap 功能对 Orca 流动性抓取存在延迟，可能短时间内不支持 Orca 上的新池子。
- Orca 创建的 LP（流动性凭证）是一种 NFT，撤销（销毁）时步骤相对复杂。

---

## 🧪 创建流动性池步骤

1. 打开 Orca 官方创建页面：[https://www.orca.so/create-pool](https://www.orca.so/create-pool)  
2. 填写相关代币信息：

![img](../.gitbook/assets/sol/Orca.jpg)

- **Token A：** 你发行的代币，请填写正确的合约地址进行搜索
- **Token B：** 交易对代币，如 USDC、USDT、SOL 等
- **Fee Tier（手续费率）：** 建议选择 **0.2%**，过低的费率可能导致交易体验不佳
- **Initial Price（初始价格）：** 假设你创建的是某代币对 SOL 的池子，该值表示“1 个代币等于多少 SOL”
- **Liquidity Range（流动性范围）：** 可选 FULL（全价区间）或 CUSTOM（自定义价格区间）。建议选择 **FULL**，操作更简单，类似于传统 AMM 模式（如 PancakeSwap V2）

3. 填写完成后，输入两种代币的数量，如下图所示：

![img](../.gitbook/assets/sol/Orca2.jpg)

4. 确认价格和数量无误后，点击 **Create Pool（创建池子）**，钱包会弹出交易确认，签名并支付 gas 即可完成。

---

## 👀 如何查看已创建的池子？

1. 打开 Orca 流动性页面：[https://v1.orca.so/liquidity](https://v1.orca.so/liquidity)  
2. 连接钱包（如果已经连接则会自动识别）

![img](../.gitbook/assets/sol/Orca3.png)

3. 点击页面上的 **Portfolio（资产组合）**，稍等几秒即可看到你已创建的池子：

![img](../.gitbook/assets/sol/Orca4.png)  
![img](../.gitbook/assets/sol/Orca5.png)

---

## 💧 如何撤回流动性？

1. 在 Portfolio 页面中，点击你想操作的交易对  
2. 选择 **Withdraw（提取）** 来撤回池中资产  
   - 如果想继续添加代币，可以选择 **Deposit（存入）**

![img](../.gitbook/assets/sol/Orca6.png)

3. 选择要提取的比例，点击 **Withdraw** 并确认钱包交易即可完成：

![img](../.gitbook/assets/sol/Orca7.png)

---

## 🙋 常见问题

- 创建池子时手续费多少？  
  通常在 **0.2–0.5 SOL** 之间，根据网络拥堵情况可能会浮动。

- Orca 的 LP 是什么形式？  
  LP 是以 **NFT 形式存在**，可在钱包或 Orca 的资产面板中查看和管理。

---

如在使用过程中遇到问题，欢迎加入我们的官方 Telegram 社区获取帮助：  
📢 [https://t.me/tokentool_app](https://t.me/tokentool_app)
