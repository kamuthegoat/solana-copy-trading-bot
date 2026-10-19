# Ultra-Low Latency Solana Copy Trading Bot (Pump.fun + Raydium V4)

[![Solana](https://img.shields.io/badge/Solana-Mainnet-blue?logo=solana)](https://solana.com)
[![Jito MEV](https://img.shields.io/badge/Jito-MEV_Bundles-green)](https://jito.wtf)
[![Speed](https://img.shields.io/badge/Execution-<50ms-orange)](#performance)
[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](#license)

A modular, high-performance copy-trading engine engineered for the Solana blockchain. Automatically tracks insider/whale wallets and mirrors token swaps across **Pump.fun** and **Raydium AMM V4** with 0-block Jito MEV bundle execution.

---

## Key Features

- **Multi-Wallet Surveillance**: Monitor unlimited target addresses simultaneously via real-time WebSocket / Yellowstone gRPC streams.
- **Smart Protocol Decoding**: Automatically detects and decodes Pump.fun bonding curve purchases and Raydium liquidity pool swaps.
- **Jito MEV Integration**: All mirror transactions are routed directly through Jito Block Engine bundles, completely preventing sandwich attacks and front-running.
- **Automated Sizing**: Fixed SOL allocation or dynamic proportional scaling based on whale position size.
- **Auto-Mirror Sell**: When the target wallet takes profit or exits, the bot automatically closes your mirror position in the same or next block.
- **Sub-50ms Reaction Time**: Built on asynchronous event streams for near-instant execution.

---

## Quickstart

### 1. Requirements
- Python 3.10+
- Solana RPC & WebSocket access (Helius, QuickNode, or Triton recommended for production)

### 2. Installation
```bash
git clone https://github.com/kamuthegoat/solana-copy-trading-bot.git
cd solana-copy-trading-bot
pip install -r requirements.txt
```

### 3. Configuration
Edit `config.json` with your target wallets and risk parameters:
```json
{
  "target_wallets": [
    "9WzDXwBbmkg8ZTbNMqUxvQRAyrZzDsGYdLVL9zYtAWWM",
    "GThUX1Atko4tqhN2NaiTazWSeFWMuiUvfFnyJyUghFMJ"
  ],
  "copy_amount_sol": 0.05,
  "max_sol_per_trade": 0.25,
  "slippage_pct": 5.0,
  "jito_tip_sol": 0.001,
  "auto_sell_with_target": true
}
```

### 4. Run
```bash
python copy_bot.py
```

---

## Architecture Flow

```
[Target Wallet Activity]
         │
         ▼
[WebSocket / Yellowstone gRPC Listener]
         │
         ▼
[Transaction Decoder: Raydium V4 / Pump.fun]
         │
         ▼
[Risk & Slippage Validation]
         │
         ▼
[Jito MEV Bundle Construction + Tip]
         │
         ▼
[Direct Jito Block Engine (0-Block Inclusion)]
```

---

## ⚡ Commercial Pro Edition ($25 USD Lifetime)

Need enterprise-grade performance? The **Pro Edition** includes:
- **Yellowstone gRPC shred stream integration** (< 15ms detection)
- **Multi-region private Jito block engine routing** (Frankfurt, Amsterdam, NY, Salt Lake City)
- **Blacklist / Honeypot filter**: automatically rejects tokens with freeze authority, honeypot traps, or low liquidity.
- **Multi-key distribution**: Spread entries across multiple fresh wallets to avoid on-chain detection.

### Instant Turnkey Purchase:
Transfer **$25 USD** equivalent in SOL, BTC, or ETH to our direct settlement wallets:

- **Solana (SOL):** `3Uiis6Zv8fsxuvANCAvDPU5dGxrnjrGgg4HpN1Pz6HHn`
- **Bitcoin (BTC):** `bc1qm0kwx7ed4g5wzl3rzuu4wdh9lqf00knhs5r778`
- **Ethereum (ETH):** `0xeC7056A6440F36b8616b4bF2B41501AaAd005c9D`

🔗 **Automated Checkout & License Thread:** [https://rentry.co/r2vfsbt4](https://rentry.co/r2vfsbt4)

---

## Disclaimer
*This software is provided for research and quantitative development purposes. Cryptocurrency trading involves substantial financial risk. Configure parameters responsibly.*
