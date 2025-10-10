# 📊 MacroPulseDashboard

**MacroPulseDashboard** is a **macro-financial risk monitoring tool** built for TradingView in Pine Script (v6).  
It aggregates high-frequency and macroeconomic indicators into a structured, visual dashboard that helps identify **periods of rising systemic stress, tightening liquidity, and cyclical market inflection points**.

The dashboard brings together signals from **credit, volatility, yield curves, sentiment, and market breadth**, combining technical and fundamental dimensions into a unified, data-driven “macro pulse” of market health.

<img width="2382" height="1681" alt="image" src="https://github.com/user-attachments/assets/5a7af836-54cd-4f47-bc9e-3aff0e68f45f" />

---

## 🧠 Theoretical Background

Financial markets are forward-looking, but macro and credit conditions often deteriorate beneath the surface long before price corrections appear.  
**MacroPulseDashboard** is designed to capture those *precursor signals*, combining insights from **economic theory, credit risk modeling, and technical market structure**.

### Key Principles

1. **Credit leads equities.**  
   - Widening credit spreads (especially in high-yield markets) often precede equity drawdowns by weeks or months.  
   - This reflects tightening financial conditions, lower risk appetite, and rising default probabilities.

2. **Volatility transmits stress.**  
   - Rising volatility (VIX, MOVE, VSTOXX) represents repricing of risk across asset classes.  
   - When bond and equity vol move together, systemic correlations increase, often a hallmark of liquidity shocks.

3. **Yield curve as a monetary signal.**  
   - Inversion (short rates above long rates) reflects restrictive policy and slowing growth expectations.  
   - A subsequent *steepening* from deep inversion often marks the transition to recession.

4. **Breadth and concentration matter.**  
   - When only a few stocks sustain market performance (narrow leadership), the structural fragility of the market rises.  
   - Broad participation is typically a sign of robust, healthy risk-taking.

5. **Liquidity drives cycles.**  
   - Indicators like NFCI and SLOOS quantify the ease or tightness of credit.  
   - Liquidity contractions precede slowdowns, while easing conditions mark recovery phases.

6. **Intermarket correlation = risk convergence.**  
   - Cross-asset metrics (credit, vol, equities, rates) often synchronize before major corrections, which can be a sign of declining diversification benefit.

---

## 🎯 Purpose and Use

MacroPulseDashboard aims to:
- **Quantify** macro stress using observable, high-quality data.
- **Visualize** market fragility and liquidity tightening in real time.
- **Bridge** the gap between economic fundamentals and technical market behavior.
- **Educate** traders on macro relationships, with built-in tooltips explaining each metric.

It’s not a trading signal generator; it’s a **situational awareness tool**.  
Think of it as your *market seismograph*, tracking tremors before the quake.

---

## ⚙️ Key Metrics

### 🇺🇸 United States Core Set
| Category | Metric | What It Reflects |
|-----------|---------|------------------|
| **Credit Risk** | HY & IG OAS | Funding stress and corporate credit spread widening |
| **Volatility** | VIX, VXN, MOVE | Cross-asset uncertainty and market repricing speed |
| **Yield Curve** | 10y–3m | Policy tightness and forward recession probability |
| **Breadth** | % Above 200DMA | Market participation and internal strength |
| **Concentration** | SPY/RSP Ratio | Leadership narrowness, fragility indicator |
| **Liquidity** | NFCI, SLOOS | Credit conditions and lending environment |
| **Sentiment** | Put/Call Ratio, SKEW | Hedging behavior and tail-risk demand |

### 🇪🇺 European Extension
| Category | Metric | What It Reflects |
|-----------|---------|------------------|
| **Volatility** | VSTOXX (FVS1!) | Eurozone market volatility |
| **Credit Stress Proxy** | IHYG / IEAC | Spread proxy for Euro corporate risk |
| **Yield Curve** | DE10Y–DE02Y | ECB policy slope and Eurozone growth expectations |
| **Leadership** | VGK / EZU | Concentration in EU equities |

---

## 📈 Dashboard Structure

### 🧭 Status Box
Summarizes the current macro regime:
- Overall **status** (Low / Monitor / Caution / High Risk)
- **Composite risk score (0–100)**
- **Drivers** — which sectors are contributing most to risk
- A short **summary** explaining current market tone

### 💡 Main Dashboard
Each row includes:
- Metric name  
- Live value  
- Z-score (vs historical range)  
- Trend (▲ rising / ▼ falling / → stable)  
- Color-coded risk state  
- Source symbol  
- Educational note *(optional)*  
- Tooltip *(always available on hover over the metric)*  

---

## 🧮 Scoring and Model Logic

1. Each metric is normalized into a **z-score** (standard deviations from its historical mean).  
2. Metrics are classified by directionality (e.g., high VIX = bad; high %>200DMA = good).  
3. Each is assigned a status:  
   - 🟢 Stable / No concern  
   - 🟡 Monitor  
   - 🟠 Caution  
   - 🔴 High risk  
4. Group-level scores are calculated (Credit, Vol, Curve, etc.) and averaged.  
5. A **Composite Risk Score** (0–100) aggregates across groups, producing a unified signal.  

---

## 🧩 Using MacroPulseDashboard

1. Add the script to your chart via the Pine Editor.  
2. Set timeframe to **1D** (macro data generally updates daily or weekly).  
3. Choose your anchor points (top-left, bottom-right, etc.).  
4. Optionally enable:
   - **EU metrics** for transatlantic stress comparison  
   - **Note column** for quick learning  
   - **Compact mode** for tighter view  

---

## 🔔 Alerts
The script includes built-in alert conditions that trigger when:
- Credit or volatility enter red zone  
- Yield curve or breadth deteriorate sharply  
- Financial conditions or lending tighten significantly  

---

## 📊 Interpretation Example

| Scenario | Typical Dashboard Pattern |
|-----------|----------------------------|
| **Early-cycle expansion** | Low spreads, steep yield curve, strong breadth |
| **Mid-cycle complacency** | Narrow leadership, low vol, flat curve |
| **Late-cycle tension** | Curve inversion, rising vol, tightening NFCI |
| **Crisis phase** | HY & IG stress, synchronized red signals across credit/vol/liquidity |

---

## 🧰 Technical Notes

- Built in **Pine Script v6**
- Optimized for **daily timeframes**
- Uses `request.security()` for cross-symbol pulls  
- Tooltip text supplied via `table.cell(..., tooltip=note)`  
- Adjustable font sizes, layout anchors, and compact mode  

---

## 📜 License
MIT License — free to use, modify, and redistribute.  
Please reference **MacroPulseDashboard** when sharing or adapting the work.

---

## ⚠️ Disclaimer
MacroPulseDashboard is for **educational and analytical use only**.  
It does **not constitute financial advice** or guarantee predictive accuracy.  
Use in conjunction with professional judgment and other risk management tools.

---

## 🧠 Author Notes
MacroPulseDashboard was created to help traders and analysts **quantify and visualize macro-financial stress** using open data.  
It blends **economic fundamentals** (credit, curve, liquidity) with **technical context** (breadth, volatility, sentiment) and turns these complex market dynamics into intuitive, data-driven insight.

