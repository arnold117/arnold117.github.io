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

Investigation of four quantitative trading strategies on cryptocurrency markets (Binance ETH-USDT perpetual contract). Demonstrates that traditional financial strategies require significant parameter optimization to succeed in crypto: unoptimized long-term strategies lost -3% to -20%, while optimized versions gained +9% to +21%.

## Problem Statement

Cryptocurrency markets differ fundamentally from traditional finance: 24/7 trading, extreme volatility (10-20% daily swings), no circuit breakers, and immature market structure. Can established quantitative strategies from traditional finance work in crypto, and how critical is parameter optimization?

## Methodology

### Strategy Selection & Testing

**Short-term** (1-hour bars, May 9-14, 2020):
1. SMA Crossover: Moving average signals
2. EWMAC: Volatility-adjusted EMA crossover

**Long-term** (daily bars, May 1-Aug 1, 2020):
3. Trend Following: Donchian + EMA + ATR stop
4. MA Trend Following: EMA crossover + ATR stop

**Optimization**: Grid search (9-2,880 combinations) maximizing Sharpe Ratio, parallel execution across CPU cores

## Results

**Key Finding**: Parameter optimization transforms losses into profits

| Strategy | Unoptimized | Optimized | Improvement |
|----------|-------------|-----------|-------------|
| SMA Crossover | +4.40% | +6.25% | +42% |
| EWMAC | +6.13% | +10.68% | +74% |
| Trend Following | -3.13% ❌ | +9.53% ✓ | +304% |
| MA Trend Following | -20.84% ❌ | +21.26% ✓ | +202% |

**Best Performer**: MA Trend Following (21.26% in 3 months, Sharpe 1.996)

## Applications

- Systematic crypto trading with optimized parameters
- Risk management via ATR-based position sizing
- Portfolio diversification with quantitative strategies
- Backtesting framework for strategy validation

## Achievements & Recognition

### Key Metrics
- 4 strategies tested, all profitable after optimization
- 2,880 parameter combinations evaluated (max)
- 21.26% return in 3 months (best strategy)
- All optimized strategies beat 8.3% inflation and 7.15% conservative investments

### Technical Stack
Python, Backtrader, pandas, numpy, matplotlib, multiprocessing

## Team & Collaboration

**Institution**: College of Optoelectronic Engineering (Now: School of Instrument Science and Optical Engineering), National Chung Hsing University

**References**:
- Carver, R. (2015). *Systematic Trading*
- Clenow, A. (2013). *Following the Trend*

## Timeline

**Duration**: September - December 2022 (4 months)
