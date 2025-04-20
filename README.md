# 📈 Crypto Trend-Following Strategies with Cross-Market Risk Management

This repository contains a complete research and backtesting pipeline for **trend-following strategies in crypto markets**, focused primarily on **Bitcoin and top altcoins**. It integrates historical data collection, strategy development, and performance evaluation.

---

## 🔍 Key Components

### 1. Historical Market Cap Snapshots
We scrape historical monthly snapshots from [CoinMarketCap](https://coinmarketcap.com/historical/), capturing the top-ranked cryptocurrencies by market capitalization on the **first day of each month**.

Coins with a market cap below **$100 million** are filtered out to ensure sufficient liquidity.

---

### 2. Daily OHLCV Data from Binance
For every coin in the snapshot that is listed on **Binance** (spot or perpetual futures), we fetch its historical **daily OHLCV data** via Binance’s official API.

This builds a robust, time-aware universe of liquid assets for analysis.

---

## ⚙️ Implemented Strategies

### 1. BTC Trend-Following with Risk Management
- Long-only and Long/Short strategies based on **BTC trend signals**
- Optional **risk-off overlay** using macro risk signals from the equity market (see below)

### 2. Cross-Sectional Momentum (Top Coins)
- **Long-only momentum** strategy: goes long the top-ranked coins by trailing performance
- **Long/Short momentum** strategy: goes long the strongest and short the weakest coins
- Both strategies use **risk-adjusted position sizing** based on asset volatility to target portfolio-level volatility

---

## 📉 Cross-Market Risk Overlay (Equity Breadth Model)
A defensive model derived from the **S&P 500** helps detect **macro risk-off regimes**, combining:
- Breadth indicators (Advance-Decline, New High–New Low, VIX z-score)
- High-yield credit spread stress (via a Thomas Count-like method)

When the model detects stress in equities, **BTC exposure is reduced**, reflecting the strong correlation during high-volatility periods.

---

## 📊 Backtesting & Evaluation

All strategies are evaluated with:
- Core metrics: CAGR, Sharpe Ratio, Max Drawdown
- Rolling performance and drawdown charts
- Strategy vs. benchmark comparisons (e.g., BTC buy & hold)

---

## 🛠️ Dependencies

This project uses:

- `pandas`, `numpy`, `plotly`, `selenium`, `tqdm`, `requests`
- `webdriver-manager` (for ChromeDriver automation)
- `statsmodels`, `scikit-learn` (for modeling and analytics)

---

## 📁 Project Structure

---

## 📁 Project Structure

