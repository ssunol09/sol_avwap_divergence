# SOL/USDT – Anchored VWAP & Divergence Study (4H)

This project analyzes how well an **Anchored VWAP + ±2σ bands**, combined with **RSI/MFI divergences**, has worked as a swing trading framework for **SOL/USDT on the 4H timeframe** since late 2022.

The goal is to test a simple idea:

> When SOL trades around its anchored VWAP zone and momentum shows clear divergences,  
> do those zones actually offer repeatable long/short opportunities?

---

## 1. Background & Motivation

I’m an NJIT FinTech student who got into trading through my cousin.  
He has been teaching me a discretionary system around it which includes but is not reduced to:

- **Anchored VWAP**
- **Upper / lower VWAP bands**
- **Bullish / bearish divergences**
- **Overbought / oversold conditions**

I used this project to **take that discretionary idea and quantify it**:

- Does AVWAP really behave like a “fair value / reaction zone” on SOL?
- Are divergences near those zones actually meaningful?
- Is the system biased more to the long side (buying dips) or the short side (fading tops)?

This repo is essentially a **research backtest** of the concepts we use in live trading.

---

## 2. Project Overview

**Symbol:** SOL/USDT  
**Timeframe:** 1H data resampled to 4H  
**Sample:** ~Dec 2022 (cycle low) → Nov 2025  
**Data source:** [CryptoCompare](https://min-api.cryptocompare.com/)

Core components:

1. **Anchored VWAP (AVWAP)** from the major weekly low in December 2022  
2. **Dynamic bands**: AVWAP ± 2 standard deviations of price–VWAP deviation  
3. **Swing highs/lows**: fractal-style pivots on 4H  
4. **Momentum & flow**: RSI(14), MFI(14)  
5. **Swing-to-swing divergences** on RSI/MFI  
6. **Zone filters**: only keep divergences that happen near AVWAP or its bands, and in OB/OS conditions  
7. **Forward returns**: evaluate how signals perform over 4h, 1d, 3d, and 1w horizons  

---

## 3. Repository Structure

```text
sol-avwap-divergence/
│
├─ notebooks/
│   └─ 01_sol_avwap_divergence.ipynb   # Full analysis pipeline
│
├─ figures/
│   ├─ sol_avwap_divergences.png       # Main chart: AVWAP + bands + bull/bear setups
│   └─ (other PNGs used in the report)
│
├─ reports/
│   └─ sol_avwap_divergence_report.pdf # Final project write-up
│
├─ data/
│   └─ README.md                       # Data is fetched on the fly from CryptoCompare
│
├─ README.md
└─ requirements.txt
