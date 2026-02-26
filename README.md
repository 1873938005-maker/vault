# Vault Hardhat Skeleton

这是一个最小的 Hardhat 项目骨架，用于实现一个 EVM Vault：接收稳定币（如 USDC/USDT），根据 NAV 为用户铸造 Vault token 的参考实现。

包含：
- 合约：`Vault.sol`, `VaultToken.sol`, `INAVPriceFeed.sol`, `MockStable.sol`, `MockNav.sol`
- 部署脚本：`scripts/deploy.js`
- 测试：`test/vault.test.js`

快速运行（在项目根目录 PowerShell 中）：

```powershell
npm install
npx hardhat test
```

注意事项：
- NAV 接口使用 18 decimals 表示每个 VaultToken 的价格。
- 稳定币可能是 6 decimals（如 USDC），合约已做统一换算到 18 decimals。
- `mintFor` 允许 relayer（或 owner）在检测到直接转账到合约地址后，使用 `depositId` 幂等地为用户铸造代币。
