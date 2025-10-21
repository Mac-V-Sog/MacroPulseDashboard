# 📊 MacroPulseDashboard

**MacroPulseDashboard** is a **macro-financial risk monitoring tool** for TradingView (Pine Script v6).
It aggregates key indicators into a structured dashboard to surface **systemic stress, liquidity tightness, and late-cycle risk**.

The dashboard blends **credit, volatility, yield curve, sentiment, and breadth** into a unified, data-driven “macro pulse” of market health.

<img width="1095" height="539" alt="image" src="https://github.com/user-attachments/assets/79e292c2-903b-4c3c-9883-4958bbc6d4a1" />

---

## 🧠 Theoretical Background

Financial conditions often deteriorate beneath the surface before prices crack. This tool tracks those **precursor signals** from credit, curves, vol, and market internals to frame risk regimes and inflection risk.

**Principles**

1. **Credit leads equities** — widening HY/IG OAS precedes equity drawdowns.
2. **Volatility transmits stress** — synchronized equity/bond vol spikes signal liquidity shocks.
3. **Yield curve = policy impulse** — deep inversion → restrictive policy; re-steepening often precedes recession.
4. **Breadth & concentration** — narrow leadership = fragile risk taking.
5. **Liquidity drives cycles** — NFCI/SLOOS tighten before activity slows.
6. **Cross-asset convergence** — rising correlations reduce diversification right when you want it most.

---

## 🎯 Purpose and Use

* **Quantify** macro stress with normalized metrics.
* **Visualize** risk drivers at a glance.
* **Educate** via built-in **tooltips** explaining each metric and column.

It’s not a trade signal generator; it’s **situational awareness**—a market seismograph for tremors before the quake.

---

## ⚙️ Key Metrics

### 🇺🇸 United States (Core)

| Category                 | Metric                      |
| ------------------------ | --------------------------- |
| **Credit**               | HY OAS, IG OAS              |
| **Volatility**           | VIX, VXN, (MOVE if enabled) |
| **Yield Curve**          | 10y–3m (bps)                |
| **Breadth**              | % S&P above 200DMA          |
| **Concentration**        | SPY / RSP                   |
| **Liquidity/Conditions** | NFCI, SLOOS                 |
| **Options Sentiment**    | Put/Call (CPC), SKEW        |

### 🇪🇺 European (Optional)

| Category         | Metric                |
| ---------------- | --------------------- |
| **Volatility**   | VSTOXX future (FVS1!) |
| **Credit Proxy** | IHYG / IEAC           |
| **Yield Curve**  | DE10Y – DE02Y (bps)   |

> Note: The previously listed EU leadership pair is **not** in this version and has been removed.

---

## 📈 Dashboard Structure

### 🧭 Top Header (Merged)

* **Composite Risk** (0–100%) with color-coded background
* Plain-language **Status**: “No immediate concern”, “Caution”, “High risk”, “Severe”
* **US reds / ambers** counts
* **EU included/excluded** indicator
* **Tooltip** explaining how the composite is computed and when the denominator changes

### 💡 Main Table (6 columns)

* **Metric** — instrument/series (tooltip shows the detailed note & last-update age)
* **Value** — latest reading (cell background reflects risk bucket)
* **Z** — z-score vs history (lookback = input `lenDaily`)
* **Trend** — **dZ** over `trendLook` bars with arrow (↑ if > +0.15, ↓ if < −0.15, – otherwise)
* **Risk** — plain text bucket label
* **Symbol** — data source symbol(s)

> There is **no Notes column** anymore. Notes are shown via **tooltips** on hover.

---

## 🧮 Scoring & Logic

* **Z-scores**: `z = (x − mean) / stdev` over `lenDaily` bars.
* **Status buckets**:

  * **Regime-aware** (default): rolling percentiles over `pctLen` bars
  * **Fixed thresholds** (optional): static amb/red cutoffs per metric
* **Group scores** (Credit, Vol, Curve, Breadth, Sentiment, Conditions; optional **Funding**, optional **Banks**)

  * Each group = max of its constituents (0, 1, or 2)
* **Composite**: `(sum of group scores / denominator) × 100%`

  * **Denominator auto-adjusts** if Funding/Banks/EU are toggled on/off
* **EU metrics** include proper **dZ** (no longer NA)

**Note on sparse series (FRED/curves):** If no new data printed within `trendLook` bars, dZ may be 0.00 (unchanged). This is expected for low-frequency series.

---

## 🧰 Using MacroPulseDashboard

1. Add the script in **Pine Editor** and **apply to chart**.
2. Recommended timeframe: **1D** (many series update daily/weekly).
3. Inputs:

   * **Regime-aware thresholds** (on by default)
   * **Z-score & Trend lookbacks** (`lenDaily`, `trendLook`)
   * **Optional pillars**: Funding (TED, DXY), Banks (KRE/SPY, BKX/SPY)
   * **EU metrics**: Vol, Credit, Curve
   * **UI — Table**:

     * **Table text size** (tiny/small/normal/large)
     * **Table corner** (Top/Bottom × Left/Right)

---

## 🔔 Alerts

**State (entering red):**

* Credit, Volatility, Yield Curve, Breadth, Options Sentiment, Conditions
* (Optional) Funding, (Optional) Banks

**Rate-of-Change (fast moves):**

* Credit widening, Volatility spike, Breadth drop, Funding tightens, Banks weakening

Configure from **Add Alert → Condition → this script → choose alert name**.

---

## 📊 Interpretation Examples

| Scenario              | Typical Pattern                                             |
| --------------------- | ----------------------------------------------------------- |
| Early-cycle expansion | Low spreads, steep curve, strong breadth                    |
| Mid-cycle complacency | Narrow leadership, low vol, flat curve                      |
| Late-cycle tension    | Curve inversion, rising vol, tightening NFCI/SLOOS          |
| Crisis phase          | HY/IG stress + synchronized red across credit/vol/liquidity |

---

## 🧩 Technical Notes

* Pine Script **v6**
* Cross-symbol pulls via `request.security()` (no lookahead, no gaps)
* Tooltips on:

  * **Top header** (composite explanation)
  * **Column headers**: **Value**, **Z**, **Trend**
  * **Every metric row** (note with last-update age & input TF)
* Z lookback default: **156 bars**; Trend lookback default: **10 bars**
* Optional EU metrics are **off** by default

---

## 📜 License

MIT — use, modify, and redistribute freely. Please reference **MacroPulseDashboard** if you adapt it.

---

## ⚠️ Disclaimer

For **educational/analytical use** only. Not financial advice. Use alongside professional judgment and robust risk management.

---

## 🧠 Author Notes

Built to help traders/analysts **quantify and visualize macro stress** using open, high-quality data—bridging macro fundamentals and market microstructure into a crisp, explainable read of risk regimes.
