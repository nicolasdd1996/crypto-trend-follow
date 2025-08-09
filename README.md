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

# Cryptocurrency Trading Strategies

This notebook outlines three trend-following strategies applied to the cryptocurrency market.  
The **first** is the base strategy, while the **second** and **third** are enhancements designed to improve robustness and adaptability.

---

## 1. **Trend on Most Liquid Cryptos by Market Cap** *(Base Strategy)*  
A trend-following approach that trades only the most liquid cryptocurrencies by market capitalization.  
It combines **EWMAC** (Exponential Weighted Moving Average Crossover) signals and **Breakout** signals, tested across multiple time windows for greater robustness.  

- **Continuous positioning:** exposure is proportional to the strength of the signal, avoiding the binary (long/flat) approach.  
- **Risk management:** each position is volatility-scaled to target a fixed **portfolio volatility**.

---

## 2. **Trend with Market Regime Risk-Off Filter** *(Enhancement 1)*  
Based on Strategy 1 but with an added **risk-off filter** according to market regime.  
In unfavorable environments (bearish or sideways markets), pure trend-following tends to underperform, so the filter reduces or removes exposure to protect capital.

---

## 3. **Cross-Asset Trend with Hedging and Execution Optimization** *(Enhancement 2)*  
Similar to Strategy 1 but with two major optimizations:  

1. **Hedging / Market Neutrality:** use of short positions in correlated assets to hedge directional risk and maintain near-zero net exposure.  
2. **Execution optimization:**  
   - Use of **limit orders** instead of market orders to reduce fees.  
   - Application of **ATR** (Average True Range) to optimize average entry price, balancing the trade-off between execution probability and favorable pricing.

