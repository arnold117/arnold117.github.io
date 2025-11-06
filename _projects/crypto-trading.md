---
layout: page
title: Quantitative Investment Strategies in Cryptocurrency Markets
description: Research on profitability of different investment strategies in cryptocurrency trading
# img: assets/img/crypto-trading.jpg
importance: 11
category: other
toc:
  sidebar: left
---

## Overview

A comprehensive course project investigating the performance of four quantitative trading strategies in cryptocurrency markets. The study explores whether traditional financial market strategies can be directly applied to cryptocurrency trading, and demonstrates the critical importance of parameter optimization for strategy profitability.

## Research Objectives

1. Implement and backtest quantitative trading strategies on cryptocurrency markets
2. Investigate whether existing strategies with common parameters work directly in crypto markets
3. Optimize strategy parameters using grid search methodology
4. Compare profitability across different strategy types and market conditions
5. Evaluate the necessity of parameter adaptation for sustainable performance

## Methodology

### Investment Product Selection

**Selected**: Binance ETH-USDT-SWAP perpetual contract (1x leverage)
- High liquidity and volatility
- 24/7 trading, no price limits
- Lower fees than spot trading

### Strategy Selection

**Short-term Strategies** (1-hour bars):
1. **SMA Crossover**: Moving average crossover signals
2. **EWMAC**: Volatility-adjusted EMA crossover from *Systematic Trading*

**Long-term Strategies** (daily bars):
3. **Trend Following**: Donchian Channels + EMA filter from *Following the Trend*
4. **MA Trend Following**: Simplified EMA crossover variant

### Backtesting Setup

- **Short-term period**: May 9-14, 2020 (price: -0.27%)
- **Long-term period**: May 1 - Aug 1, 2020 (price: +31.83%)
- **Commission**: 0.04% (Binance taker fee)
- **Initial capital**: $10,000 (short-term), $20,000 (long-term)

## Strategy Implementation & Results

### Strategy 1: SMA Crossover

**Logic**: Golden cross (fast MA > slow MA) signals uptrend

**Results** (May 9-14, 2020):
- Unoptimized: +4.40%, Sharpe 0.269, Annualized 267.95%
- **Optimized**: +6.25%, Sharpe 0.837, Annualized 253.47%
- Best params: MA128/MA256

### Strategy 2: EWMAC

**Logic**: Volatility-adjusted EMA crossover with forecast capping at [-20, 20]

**Results** (May 9-14, 2020):
- Unoptimized: +6.13%, Sharpe 0.406, Annualized 372.81%
- **Optimized**: +10.68%, Sharpe 0.806, Annualized 433.13%
- Best params: EWMAC64/EWMAC1024

### Strategy 3: Trend Following (Clenow)

**Logic**: Donchian breakout + EMA confirmation + ATR trailing stop

**Results** (May 1 - Aug 1, 2020):
- Unoptimized: **-3.13%**, Sharpe -0.502 ❌
- **Optimized**: +9.53%, Sharpe 1.267, Annualized 38.66%
- Best params: EMA132/528, DC33/132, ATR528

### Strategy 4: MA Trend Following

**Logic**: EMA crossover + trend filter + ATR trailing stop

**Results** (May 1 - Aug 1, 2020):
- Unoptimized: **-20.84%**, Sharpe -3.377 ❌
- **Optimized**: +21.26%, Sharpe 1.996, Annualized 86.22%
- Best params: EMA168/840, MA42/168, ATR840

## Key Findings

### Parameter Optimization is Critical

**Short-term strategies** showed resilience but benefited from optimization:
- SMA Crossover: +4.40% → +6.25% (+42% improvement)
- EWMAC: +6.13% → +10.68% (+74% improvement)

**Long-term strategies FAILED without optimization**:
- Trend Following: -3.13% → +9.53% (**+304% turnaround**)
- MA Trend Following: -20.84% → +21.26% (**+202% turnaround**)

### Performance Summary

| Strategy | Unoptimized | Optimized | Grid Search |
|----------|-------------|-----------|-------------|
| SMA Crossover | +4.40% | +6.25% | 9 combinations |
| EWMAC | +6.13% | +10.68% | 9 combinations |
| Trend Following | -3.13% ❌ | +9.53% ✓ | 270 combinations |
| MA Trend Following | -20.84% ❌ | +21.26% ✓ | 2,880 combinations |

All optimized strategies beat inflation (8.3%) and conservative investments (max 7.15% APY).

## Risk Management

### Position Sizing (Long-term Strategies)
```
Max Loss = Capital × Risk Factor (0.2%)
Position Size = Max Loss / ATR
```

### Trailing Stop Loss
```
Stop Price = Entry ± (ATR × 3)
```
- Moves with favorable price action
- Locks in profits while allowing trend continuation

### Entry/Exit Rules
- **Trend Following**: Donchian breakout + EMA confirmation
- **MA Trend Following**: EMA crossover + trend filter

## Conclusions

1. **Parameter adaptation is essential**: Direct application of traditional parameters to crypto markets often causes losses

2. **Optimization enables profitability**: All four strategies became profitable after proper parameter tuning

3. **Strategy resilience varies**: Short-term strategies more robust; long-term strategies require careful optimization

4. **Best performer**: MA Trend Following (21.26% in 3 months, Sharpe 1.996)

### Practical Implications
- Always backtest before deployment
- Monitor and adjust parameters regularly  
- Consider market regime changes
- Be aware of overfitting risks

## Technical Implementation

**Stack**: Python, Backtrader, pandas, numpy, matplotlib, multiprocessing

**Grid Search**: Exhaustive parameter search optimized by Sharpe Ratio
- Parallel execution across all CPU cores
- 9 to 2,880 parameter combinations per strategy

**Key References**:
- Carver, R. (2015). *Systematic Trading*
- Clenow, A. (2013). *Following the Trend*
- Murphy, J.J. (1999). *Technical Analysis of the Financial Markets*

## Project Timeline

September - December 2022 (4 months)  
College of Optoelectronic Engineering (Now: School of Instrument Science and Optical Engineering), NCHU
