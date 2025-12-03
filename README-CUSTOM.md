# Contango Custom Position Builder

A powerful, fee-free interface for creating **custom positions** on Contango V2 with any token pair and money market combination.

## 🌐 Live Demo

**GitHub Pages**: [https://ncwardell.github.io/DeTango/](https://ncwardell.github.io/DeTango/)

Access the interface directly from your browser - no installation required!

## 🎯 What Makes This Different?

Unlike the standard Contango UI, this tool lets you:
- ✅ **Create positions with ANY token pair** - not limited to pre-configured pairs
- ✅ **Choose ANY money market** - Aave, Moonwell, Sonne, Seamless, Compound, or custom
- ✅ **Zero UI fees** - Direct smart contract interaction
- ✅ **Multiple wallet support** - Works with Rabby, MetaMask, Coinbase Wallet, and more
- ✅ **Full transparency** - See exactly what parameters are being sent to the contract

## 📁 Files

- **index.html** - Landing page for GitHub Pages
- **contango-custom.html** - Advanced custom position builder (recommended!)

## 🚀 Quick Start

### Option 1: Use GitHub Pages (Easiest)

Simply visit: **[https://ncwardell.github.io/DeTango/contango-custom.html](https://ncwardell.github.io/DeTango/contango-custom.html)**

### Option 2: Run Locally

1. Clone this repository
2. Open `contango-custom.html` in your browser
2. Connect your wallet (Rabby, MetaMask, etc.)
3. Enter token addresses:
   - **Base Token**: The token you want to long/short
   - **Quote Token**: Your collateral/pricing token
4. Select your money market (Aave, Moonwell, etc.)
5. Configure position size and leverage
6. Execute trade!

### Option 2: Simple Interface

Use `contango-direct.html` if you know the exact instrument symbol format used by Contango.

## 🔧 How to Build Custom Positions

### Understanding Token Pairs

A Contango position consists of:
1. **Base Token** - The asset you're trading (e.g., WETH)
2. **Quote Token** - Your collateral (e.g., USDC)
3. **Money Market** - Where the lending/borrowing happens

### Example: WETH/USDC Long on Base

**Base Token (WETH on Base):**
```
0x4200000000000000000000000000000000000006
```

**Quote Token (USDC on Base):**
```
0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
```

**Money Market:** Aave

**Position Side:** Long

**Quantity:** 1.0 (1 WETH)

This creates a leveraged long position on WETH using USDC as collateral.

## 📋 Common Base Chain Token Addresses

### Major Assets
- **WETH**: `0x4200000000000000000000000000000000000006`
- **USDC**: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`
- **DAI**: `0x50c5725949A6F0c72E6C4a641F24049A917DB0Cb`
- **cbETH**: `0x2Ae3F1Ec7F1F5012CFEab0185bfc7aa3cf0DEc22`

### LSTs/LRTs
- **wstETH**: Check BaseScan for current address
- **rETH**: Check BaseScan for current address

**Note:** Always verify token addresses on [BaseScan](https://basescan.org) before trading!

## 🎛️ Position Parameters

### Required Fields

1. **Base Token Address** - The ERC20 token address you want to trade
2. **Quote Token Address** - The ERC20 token address for collateral
3. **Money Market** - The lending protocol to use
4. **Quantity** - Size of your position in base token units
5. **Position Side** - Long (buy) or Short (sell)

### Optional Fields

- **Limit Price** - Maximum price you're willing to pay (0 = market order)
- **Collateral/Cashflow** - Additional collateral to deposit
- **Collateral Currency** - Whether collateral is in base or quote token

## 🔍 How Symbol Generation Works

The interface generates an instrument symbol from your inputs:

```
Format: [BASE_TOKEN_SEGMENT]-[QUOTE_TOKEN_SEGMENT]-[MARKET_ID]
```

**Example:**
- Base: `0x4200...0006` (WETH)
- Quote: `0x8335...2913` (USDC)  
- Market: Aave
- Generated: `42000000-83358900-AAVE`

**Note:** The actual Contango protocol may use a different symbol format. This tool attempts to generate compatible symbols, but you may need to experiment or check the Contango codebase for exact formatting.

## 💡 Supported Money Markets on Base

- **Aave** - Most liquid and widely used
- **Moonwell** - Native Base lending protocol
- **Sonne** - Optimism-originated protocol on Base
- **Seamless** - Native Base protocol
- **Compound** - Classic DeFi lending
- **Custom** - Enter your own market identifier

## 🔐 Wallet Compatibility

This tool uses standard Web3 provider detection and works with:
- ✅ **Rabby Wallet** (detected as "Rabby Wallet")
- ✅ **MetaMask** (detected as "MetaMask")
- ✅ **Coinbase Wallet** (detected as "Coinbase Wallet")
- ✅ **Brave Wallet** (detected as "Brave Wallet")
- ✅ **Frame** (detected as "Frame")
- ✅ Any other Web3-compatible wallet

The interface automatically detects your wallet type and displays it after connection.

## ⚙️ Advanced Usage

### Understanding Contango Mechanics

When you open a position, Contango:
1. Flash loans the required amount
2. Swaps on spot markets (via DEX aggregators)
3. Lends and borrows on the money market
4. Repays the flash loan

This creates a leveraged position without requiring you to manually execute each step.

### Leverage Calculation

Leverage is determined by:
```
Leverage = Position Size / Your Collateral
```

Example:
- Position Size: 10 ETH ($20,000)
- Your Collateral: $2,000
- Leverage: 10x

### Funding Rates (APY/ROE)

Your net APY comes from:
- (+) Lending rate on base token
- (-) Borrowing rate on quote token
- (-) Protocol fees

## 🛡️ Safety & Best Practices

### Before Trading

1. **Verify Token Addresses**
   - Always check on BaseScan
   - Ensure tokens are the actual assets, not scam tokens
   
2. **Understand the Market**
   - Check liquidity on the money market
   - Verify DEX liquidity for the token pair
   
3. **Start Small**
   - Test with small amounts first
   - Understand how positions behave

### Risk Management

- Monitor your **liquidation price**
- Understand that positions can be liquidated if collateral falls below thresholds
- Be aware of **oracle risk** - prices used by money markets may differ from market prices
- Consider **slippage** when entering/exiting positions

## 🔧 Troubleshooting

### "Transaction Failed" Errors

1. **Check token addresses** - Invalid addresses will fail
2. **Verify liquidity** - Insufficient DEX or lending liquidity causes failures
3. **Reduce leverage** - Try a smaller position size
4. **Check allowances** - You may need to approve tokens first (this UI should handle it)

### Wallet Connection Issues

If your wallet isn't connecting:
1. Refresh the page
2. Make sure you're on Base network
3. Try disconnecting and reconnecting
4. Check your wallet extension is enabled

### Symbol Format Issues

If transactions fail with "Invalid symbol" errors:
- The symbol format may need adjustment
- Check the Contango documentation for exact format requirements
- Try using the official UI to see how symbols are structured
- Experiment with different format patterns

## 📊 Monitoring Your Positions

After opening a position:
1. Visit the official [Contango app](https://contango.xyz/)
2. Your position will appear in "Open Positions"
3. Each position is represented as an NFT
4. You can manage, close, or modify positions from there

## 🔗 Resources

- [Contango Protocol](https://contango.xyz/)
- [Contango Docs](https://docs.contango.xyz/)
- [GitHub Repository](https://github.com/contango-xyz/core-v2)
- [BaseScan](https://basescan.org/)
- [Base Bridge](https://bridge.base.org/)

## 📜 Contract Details

- **Proxy Contract**: `0xa6a147946FACAc9E0B99824870B36088764f969F`
- **Network**: Base Chain
- **Chain ID**: 8453
- **Function**: `trade()` via `multicall`

## ⚠️ Important Disclaimers

- **Not Financial Advice**: This tool is for educational purposes
- **Use at Your Own Risk**: Smart contract interactions carry inherent risks
- **Verify Everything**: Always double-check addresses and parameters
- **No Warranties**: This tool is provided as-is with no guarantees
- **Advanced Users Only**: Requires understanding of DeFi mechanics
- **Protocol Fees Apply**: While this UI is free, the Contango protocol charges fees

## 🆘 Getting Help

If you encounter issues:
1. Check the [Contango Discord](https://discord.gg/contango)
2. Review the [official documentation](https://docs.contango.xyz/)
3. Verify your setup matches the examples above
4. Start with small test positions

## 🎓 Learning Resources

New to Contango? Start here:
- [How Contango Works](https://docs.contango.xyz/)
- [Understanding Looping](https://medium.com/contango-xyz/)
- [DeFi Risk Management](https://docs.contango.xyz/resources/faq)

---

**Built for the DeFi community** 🚀

Direct access. No UI fees. Full control.

## 🚀 Deployment

This project is configured for GitHub Pages deployment:

1. Push to your GitHub repository
2. Go to repository Settings → Pages
3. Set source to "Deploy from branch"
4. Select branch (usually `main` or `claude/contango-custom-ui-*`)
5. Select `/` (root) folder
6. Save

Your site will be live at: `https://[username].github.io/[repository-name]/`

### Local Development

Simply open `index.html` or `contango-custom.html` in any modern web browser. No build process required!
