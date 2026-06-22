# Quantitative Trading Research System

Multi-strategy algorithmic trading system built in Python across the full S&P 500 universe with live paper trading execution via Alpaca API.

## Strategies

### 1. Trend Following — 200-Day Moving Average
- **Universe:** Diversified ETF universe (10 assets)
- **Signal:** Hold when price > 200-day MA, go to cash when below
- **Rebalance:** Monthly
- **Key results:** 13.0% CAGR | 0.76 Sharpe | -23.7% max drawdown vs 14.7% SPY

### 2. Cross-Sectional Momentum Rotation
- **Universe:** Full S&P 500 (~480 liquid stocks)
- **Signal:** 6-month return rank, skip-1 month (Jegadeesh & Titman 1993), buy top 10
- **Rebalance:** Monthly
- **Regime detection:** Reduces momentum exposure 50% in bear markets (SPY below 200d MA)
- **Key results:** 43.5% CAGR | 1.39 Sharpe | -27.1% max drawdown vs 14.0% SPY

### 3. Mean Reversion — Z-Score
- **Universe:** Full S&P 500 (~480 liquid stocks)
- **Signal:** Buy 10 most oversold stocks when 20-day Z-score < -1.5
- **Rebalance:** Daily
- **Key results:** 20.2% CAGR | 0.74 Sharpe | 52.9% win rate vs 14.7% SPY

## Methodology
- Walk-forward validation (70/30 train/test split) to prevent overfitting
- Kelly criterion for optimal capital allocation
- Volatility-adjusted position sizing
- Regime detection module for bear market protection
- Smart rebalancing with minimum trade threshold
- Separate Alpaca paper trading account per strategy 
  for clean performance isolation

## Tech Stack
Python, pandas, NumPy, yfinance, plotly, alpaca-py
