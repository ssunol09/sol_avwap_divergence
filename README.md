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
```

--- 

## 4. Methodology (Simple and Clear)

This project is built around one question:  
**Does SOL react consistently around an Anchored VWAP zone, and do divergences help confirm good long/short entries?**

Below is a simple breakdown of how the analysis works.

---

### 4.1 Data & Resampling

- Downloaded **1-hour SOL/USDT OHLCV** from CryptoCompare.
- Converted that into **4-hour candles** by grouping:
  - Open = first hourly open  
  - High = highest high  
  - Low = lowest low  
  - Close = last hourly close  
  - Volume = total volume  

Using 4H helps smooth noise and highlight swing structure.

---

### 4.2 Anchored VWAP & Bands

- Calculated the **Anchored VWAP** starting from the major low on **Dec 26, 2022**  
  (a clear cycle low for SOL).
- Computed the difference between price and VWAP over time.
- Calculated a dynamic standard deviation and used it to build:
  - **Upper band = VWAP + 2σ**  
  - **Lower band = VWAP – 2σ**

These three lines (VWAP + upper/lower bands) form the “**reaction zone**.”

---

### 4.3 Swing Points & Divergences

- Identified **swing highs and swing lows** using a simple fractal method.
- Computed two indicators:
  - **RSI (14)**
  - **MFI (14)**
- Looked for **divergences** between price and the indicators:
  - **Bullish divergence** → price makes lower lows while the indicator makes higher lows  
  - **Bearish divergence** → price makes higher highs while the indicator makes lower highs  

This checks whether momentum is disagreeing with price action.

---

### 4.4 Setup Conditions (What Counts as a Signal)

A setup only counts if multiple conditions line up.

#### **Bullish setup (long idea):**
- Bullish divergence (RSI or MFI)  
- Price is close to VWAP or one of its bands  
- Momentum is oversold  

#### **Bearish setup (short idea):**
- Bearish divergence  
- Price near VWAP or its bands  
- Momentum is overbought  

These rules match the trading style I’ve been developing — especially the focus on VWAP zones.

---

### 4.5 Performance Check

For every valid setup, calculated returns moving forward:

- 4 hours  
- 1 day  
- 3 days  
- 1 week  

Then measured for both long and short setups:

- Number of trades  
- Win rate  
- Average and median returns  
- Standard deviation  
- Simple t-test (mean return vs 0)

This shows whether the setups actually have edge or not.

---

## 5. Key Results (Short Summary)
### **Bullish Setups**

- Show a clear positive edge
- High short-term hit rate (4H)
- Strong 1-week follow-through
- t-tests show statistical significance

**Interpretation**: AVWAP + bullish divergences reliably mark reaction lows

### **Bearish Setups**
- Fewer signals
- Only meaningful on very short horizons (4H)
- Edge decays fast after 1 day

**Interpretation**: bears work best as short-term fades, not long trend moves

### **Overall**

AVWAP + ±2σ bands consistently behaved as fair-value reaction zones for SOL.
Momentum divergences near these zones produced measurable directional expectations.

---

## 6. Notes & Limitations

A few things to keep in mind:

- This study does **not** model fees, slippage, or real execution mechanics.
- The VWAP is anchored at **one** major low (Dec 26, 2022).  
  In real trading, you might anchor VWAP at different points depending on the trend.
- SOL had some strong bullish periods in this dataset, so long setups naturally perform better.
- This is a research project aimed at understanding behavior around VWAP zones —  
  not a live trading system or financial advice.
---

## 7. Author

This project combines my NJIT FinTech coursework with actual concepts I use in trading, learned through working with my cousin.
The idea was to test whether the Anchored VWAP + divergences approach we use actually lead to short-term and long-term gains.

If you’re interested in crypto research or systematic technical trading — feel free to reach out.
