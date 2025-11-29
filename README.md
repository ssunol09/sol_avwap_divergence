# SOL/USDT Anchored VWAP Divergence Study

I had a simple motivation for this project, which was to see with real data wether the trading concepts 
my cousin taught me actually had statistical relevance. He introduced me to utilizing various indicators
such as Fibonacci retracements, Fixed Volume Profile  and—most importantly for this study—Anchored
VWAP levels and momentum divergences. These tools create important zones and signals to help us identify 
potential reversals on the chart. 

For this quant project, I decided to focus solely on AVWAP and divergences as those are two of the most 
relevant ones in our trading method, and also the ones that could be cleanly implemented into code whitout
overcomplicating the analysis. My goal in this project wasn't to build a full trading system, but rather 
to test whether these ideas actually behave the way they seem to do on TradingView: do AVWAP zones act as 
support/resistance levels, and do divergences nearthose levels actually lead to strong reversals?

This project answers that question by turning a persona, chart-based approach into something quantifiable, 
measurable, and backed by statistics. 

---

## 🔍 Project Overview

- 1H OHLCV data (CryptoCompare), resampled to 4H  
- AVWAP anchored at the December 26, 2022 capitulation low  
- ±2σ volatility bands to define reaction zones  
- Swing-high/low detection  
- RSI & MFI divergences (swing-to-swing)  
- Filtered bull/bear “setups” based on:  
  - divergence  
  - proximity to AVWAP zone  
  - overbought/oversold conditions  
- Forward returns measured at 4H, 1D, 3D, 1W horizons  
- Includes statistical tests and full performance evaluation  

---

## 📄 Full Report (Recommended)

For the complete write-up, charts, tables, results, and interpretations:

👉 **[Download the Final PDF Report]([reports/sol_avwap_divergence_report](https://github.com/ssunol09/sol_avwap_divergence/blob/main/reports/sol_avwap_divergence_report.pdf))**

This is the polished 5–7 page research paper summarizing the entire project.

---

## 📓 Notebook

The full methodology and code are in:

👉 `notebooks/01_sol_avwap_divergence.ipynb`

This includes data download, AVWAP calculation, divergence logic, and the entire analysis pipeline.

---

## 📁 Repository Structure
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
├── requirements.txt
└── README.md
```

--- 

## ▶️ How to Run

Clone and install dependencies:

```bash
git clone https://github.com/ssunol09/sol_avwap_divergence.git
cd sol_avwap_divergence
pip install -r requirements.txt
```
Run the notebook:
```
jupyter notebook notebooks/01_sol_avwap_divergence.ipynb
```
---

## 🎯 Purpose

My goal was to take the trading ideas I actually use and test them in a clean and systematic way. 
By turning actual chart-based ideas into something quantifiable, this project serves as a link between 
what I've been learning in trading and what I'm learning in FinTech.

## Author - Sebastián Suñol

If you’re interested in crypto research or systematic technical trading — feel free to reach out.
