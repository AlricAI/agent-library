---
name: DASHBOARD
description: **File:** `viz/dashboard/app.
model: claude-sonnet-4-5
---
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

**Color scale:** Diverging RdYlGn (red = negative, white = zero/break-even, green = positive)

**Annotations:** Draw a thick white contour line at E[R_net] = 0 (the break-even boundary). This visually shows the break-even curve in (p, α) space.

**Title:** `f"E[R_net](p, α) — {class_code} — {tau_label} — median market conditions"`

### Panel 3: Break-Even Banner

**Chart type:** Plotly `go.Indicator` + large text block

**Content:**
```
To break even in {class_name} markets today
({jurisdiction_name} tax, α = {alpha:.2f}):

You need to be right on more than
{p_star_pct:.1f}%
of your bets.

(Based on the last 7 days of market conditions.
p* range: {p_star_p5*100:.1f}% – {p_star_p95*100:.1f}%)
```

The centre number (`{p_star_pct:.1f}%`) must be large (48px+), bold, and coloured:
- Red if p_star_pct > 80% (very hard to beat this market)
- Amber if 65% < p_star_pct ≤ 80%
- Green if p_star_pct ≤ 65% (accessible to skilled participants)

### Panel 4: Oracle Bounds Summary

**Chart type:** Plotly `go.Bar` (grouped) + stat boxes

**Three grouped bars per alpha value:** R_L1 (α=1), R_L(α), R_L2 (α=0)

Also show as stat boxes (metric cards):

| Metric | Value |
|--------|-------|
| Median R_L1 | `{r_l1_median:.1%}` |
| Median R_L2 | `{r_l2_median:.1%}` |
| Median ΔR_timing | `{delta_r_median:.1%}` |
| Mean IER | `{ier_mean:.3f}` |
| Slots analysed | `{n_slots:,}` |
| Date range | `{start_date} → {end_date}` |

---

## 3. Header Selectors (Callbacks)

All panels update when any selector changes. Use Dash callbacks with `Input` / `Output`.

```python
@app.callback(
    [Output("ier-timeseries", "figure"),
     Output("pnl-heatmap", "figure"),
     Output("breakeven-banner", "children"),
     Output("oracle-summary", "figure")],
    [Input("class-selector", "value"),
     Input("tax-selector", "value"),
     Input("alpha-selector", "value")]
)
def update_all_panels(class_code, tau_label, alpha):
    ...
```

**Selector options:**

| Selector | Options | Default |
|----------|---------|---------|
| Class | `C1: BTC 5-min` (Phase 0; more added in Phase 1) | `C1` |
| Tax | `Gross (0%)`, `UK (20%)`, `Italy (26%)`, `US (37%)` | `Italy (26%)` |
| Alpha | `0.0`, `0.10`, `0.25`, `0.50`, `0.75`, `0.90`, `1.0` | `1.0` |

---

## 4. Data Loading

The dashboard reads from **Redis** (not directly from TimescaleDB) for fast response:

```python
import redis
import json

r = redis.Redis.from_url(os.getenv("REDIS_URL"))

def get_ier_series_cached(class_code: str, tau_label: str, alpha: float) -> list[dict]:
    key = f"ier:{class_code}:{tau_label}:{alpha:.2f}"
    data = r.get(key)
    if data is None:
        return []  # No data yet — show empty chart with "No data" annotation
    return json.loads(data)
```

If Redis is unavailable (pipeline hasn't run yet), all panels should show a graceful "No data available — run the pipeline first" message, not an error.

---

## 5. Running the Dashboard

```bash
# With full stack running:
make dashboard
# → Opens http://localhost:8050

# Or directly:
docker-compose exec dashboard python viz/dashboard/app.py

# In development mode (auto-reload):
DASH_DEBUG=true python viz/dashboard/app.py
```

---

## 6. Static Export (for paper website)

```python
# viz/dashboard/export.py — called by P9 pipeline stage
import dash
app.export_static("paper/dashboard_snapshot.html")
```

The static export captures the dashboard state as of the latest data and is committed to `paper/` for publication.