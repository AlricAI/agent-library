# DASHBOARD

> **File:** `viz/dashboard/app.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DASHBOARD.md — Live IER Dashboard Specification

**File:** `viz/dashboard/app.py`
**URL:** `http://localhost:8050`
**Technology:** Plotly Dash 2.17
**Update frequency:** Refreshes automatically after each P8 pipeline run (daily)

---

## 1. Layout

The dashboard has four panels arranged in a 2×2 grid with a header bar.

```
┌─────────────────────────────────────────────────────────────────────┐
│  HEADER: "The Oracle Gap — Live Dashboard"                          │
│  Selector: [Class: BTC 5-min ▼]  [Tax: Italy ▼]  [Alpha: 1.0 ▼]   │
├──────────────────────────────┬──────────────────────────────────────┤
│  PANEL 1: IER Time-Series    │  PANEL 2: (p, α) Return Heatmap     │
│  (scatter + rolling mean)    │  (diverging colorscale)             │
├──────────────────────────────┼──────────────────────────────────────┤
│  PANEL 3: Break-Even Banner  │  PANEL 4: Oracle Bounds Summary     │
│  (plain-language text)       │  (R_L1, R_L2, ΔR_timing stats)     │
└──────────────────────────────┴──────────────────────────────────────┘
```

---

## 2. Panel Specifications

### Panel 1: IER Time-Series

**Chart type:** Plotly `go.Scatter` with two traces:
1. **Raw IER** (per slot): markers, opacity 0.3, size 4, color by quality_flag (green=0, yellow=1)
2. **7-day rolling mean**: solid line, bold, color = NAVY

**X axis:** Date (slot t0_utc)
**Y axis:** IER value. Range: [−0.5, 1.5]. Add horizontal dashed line at y=0 (red) and y=1 (green).

**Hover:** Show on hover: `date, IER, R_L2, R_crowd, volume_usd, n_trades`

**Annotations:**
- If IER z-score > 2σ from rolling mean: add star marker at that point
- Title: `f"Information Efficiency Ratio — {class_code} — {tau_label}"`

### Panel 2: (p, α) Expected Return Heatmap

**Chart type:** Plotly `go.Heatmap`

**X axis:** α values [0.0, 0.1, 0.25, 0.5, 0.75, 0.9, 1.0]
**Y axis:** p values [0.50, 0.55, 0.60, ..., 0.95, 1.00]
**Z values:** E[R_net](p, α) — computed from the median (q₀, q*) over the trailing 7 days

**Color scale:** Diver

*[truncated — see source for full prompt]*