---
layout: page
title: Quantitative Investment Strategies in Cryptocurrency Markets
description: Algorithmic trading and portfolio optimization
img: assets/img/crypto-trading.jpg
importance: 11
category: other
---

## Overview

A course project analyzing and implementing quantitative trading strategies for cryptocurrency markets, exploring market dynamics, strategy backtesting, and the importance of strategy adaptation in volatile asset classes.

## Course Context

Advanced Topics in Machine Learning and Data Science  
Duration: September - December 2022

## Research Objectives

1. Understand cryptocurrency market microstructure and dynamics
2. Develop and implement quantitative trading strategies
3. Backtest strategies on historical data with realistic parameters
4. Evaluate performance metrics and risk-adjusted returns
5. Analyze strategy robustness across market regimes

## Market Analysis

### Cryptocurrency Characteristics
- **24/7 Trading**: No market closure, continuous price discovery
- **High Volatility**: Bitcoin: 50-100% annual volatility vs. 15-20% S&P 500
- **Retail-Driven**: High impact of retail trading and social media
- **Emerging Patterns**: New asset class with evolving dynamics
- **Limited History**: Shorter historical data than traditional assets

### Dataset
- **Assets**: Bitcoin (BTC), Ethereum (ETH), major altcoins
- **Timeframe**: 2018-2022 (including COVID crash, bull runs)
- **Frequency**: 1-minute, 1-hour, daily candles
- **Features**: OHLCV + order book data when available

## Strategy Development

### Strategy 1: Momentum-Based Trading
- **Logic**: Buy when 20-day momentum > threshold, sell when < -threshold
- **Implementation**: SMA/EMA crossovers, momentum indicators
- **Backtest Results**:
  - Return: 25-40% annually (market dependent)
  - Sharpe: 0.8-1.2
  - Max Drawdown: 30-45%

### Strategy 2: Mean Reversion
- **Logic**: Identify overbought/oversold conditions, trade reversals
- **Implementation**: Bollinger Bands, RSI divergence
- **Backtest Results**:
  - Return: 15-30% annually
  - Sharpe: 0.6-0.9
  - Max Drawdown: 20-35%

### Strategy 3: Ensemble Approach
- **Combine multiple signals**: Momentum + mean reversion + volume
- **Weighted voting**: Higher confidence signals given more weight
- **Backtest Results**:
  - Return: 30-50% annually
  - Sharpe: 1.0-1.5
  - Max Drawdown: 25-40%

## Key Findings

### Strategy Adaptation Importance
- **Market Regime Changes**: Strategies that work in 2021 failed in 2022
- **Trend Following Problem**: Works in bull markets, disastrous in crashes
- **Parameter Sensitivity**: Small threshold changes dramatically affect returns
- **Dynamic Adjustment**: Necessary for consistent out-of-sample performance

### Performance Metrics
- **Sharpe Ratio**: Risk-adjusted return metric
- **Sortino Ratio**: Downside volatility penalization
- **Maximum Drawdown**: Worst-case loss from peak
- **Win Rate / Profit Factor**: Win/loss trade statistics
- **Calmar Ratio**: Return per unit of drawdown

## Risk Management

### Position Sizing
- **Kelly Criterion**: Optimal fraction of capital per trade
- **Fixed Fractional**: 2-5% risk per trade
- **Dynamic**: Adjusted based on volatility

### Stop Loss & Take Profit
- **Stop Loss**: 2-3% below entry (prevent catastrophic losses)
- **Take Profit**: 3-5% above entry (lock in gains)
- **Trailing Stops**: Move stop with price to protect profits

### Portfolio Allocation
- **Diversification**: 5-10 cryptocurrencies across different categories
- **Correlation Analysis**: Minimize asset correlations
- **Rebalancing**: Quarterly or volatility-triggered

## Portfolio Optimization

### Efficient Frontier
- Maximized Sharpe ratio for given return target
- Minimum variance portfolios
- Risk-return tradeoff visualization

### Results
- **Historical Returns**: 8-12% annualized (on holdings)
- **With Trading**: 20-35% annualized (high volatility period dependent)
- **Correlation**: Bitcoin correlation to altcoins: 0.3-0.7

## Lessons Learned

1. **Market Dynamics Matter**: Cryptocurrency markets are fundamentally different from traditional markets
2. **Strategy Drift**: Strategies must adapt to changing market conditions
3. **Over-Optimization Risk**: Backtested performance often exceeds real-world returns
4. **Volatility is a Feature**: High volatility provides trading opportunities but requires risk management
5. **Transaction Costs**: Often overlooked, can consume significant profits
6. **Regime Detection**: Identifying market regimes crucial for strategy switching

## Technical Stack

- **Language**: Python
- **Libraries**: pandas, numpy, scikit-learn, TA-Lib
- **Backtesting**: Backtrader, PyAlgoTrade
- **Data**: Binance API, CoinGecko API
- **Visualization**: Matplotlib, Plotly

## Visualizations & Results

- Strategy equity curves and underwater plots
- Portfolio composition and rebalancing decisions
- Risk metrics across time windows
- Market regime identification plots
- Performance attribution analysis

## Code & Resources

- **GitHub**: [arnold117](https://github.com/arnold117)
- **Course Materials**: NUS Graduate School

## Timeline

- **Start**: September 2022
- **End**: December 2022
- **Duration**: 4 months
- **Presentation**: December 2022
