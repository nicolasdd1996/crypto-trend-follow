# Crypto Trend-Following Strategies with Cross-Market Risk Management

This repository contains a complete research and backtesting pipeline for **trend-based crypto strategies**, with a focus on **Bitcoin and high-liquidity altcoins**. The framework combines data scraping, strategy development, and performance analysis using macro and crypto-native signals.

---

## Data Sources

### 1. Historical Market Cap Snapshots
We scrape monthly snapshots from [CoinMarketCap](https://coinmarketcap.com/historical/), capturing the top cryptocurrencies by market capitalization on the **first day of each month**.  
To ensure liquidity, we filter out coins with **market cap below $100M**.

### 2. Daily OHLCV from Binance
We download **daily OHLCV data** from Binance (spot and perpetual markets) for each coin listed in the snapshots. This provides a time-aware, liquidity-filtered universe of tradeable assets.

---

## Strategy Overview

### 1. **BTC Risk-Off Model**
A defensive overlay designed to reduce or eliminate exposure to Bitcoin based on:
- **Trend-following signals on BTC** (e.g. moving average slope)
- A **cross-market risk model** combining:
  - Breadth signals from the **S&P 500** (Advance-Decline, New High–New Low, VIX z-score)
  - High-yield **credit spread stress**, evaluated using a Thomas Count-style logic

BTC exposure is reduced whenever:
- The equity model enters a **risk-off regime**, or
- BTC shows persistent **negative trend**

---

### 2. **Long-Only Altcoin Trend Strategy**
This strategy selects a subset of altcoins with the **strongest positive trend** signals (momentum-based), drawn from the top coins by market cap.

- Position sizing is **risk-adjusted** using recent asset volatility.
- The portfolio is scaled to maintain a **target volatility** at the aggregate level.
- No short positions are taken; cash is held when opportunities are weak.

---

### 3. **Long/Short Altcoin Trend Strategy**
A cross-sectional momentum strategy that goes:
- **Long** the strongest-trending altcoins
- **Short** the weakest-trending ones

- Position sizes are volatility-scaled, with the goal of achieving balanced and consistent risk.
- Maintains a **net exposure close to neutral**, while capturing relative strength differentials.

---

## Evaluation

Strategies are analyzed using:
- Core performance metrics: **CAGR, Sharpe Ratio, Max Drawdown**
- **Rolling statistics** and **drawdown charts**
- Visual comparisons against benchmark strategies (e.g. BTC buy & hold)
