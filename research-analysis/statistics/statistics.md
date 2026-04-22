---
name: Statistics
description: **Data source:** Oops.
model: claude-sonnet-4-5
---
# Variants

**Data source:** Oops.csv (562 opportunities)  
**Overall win rate:** 35.4%

---

## Output 1 — Persona Normalization (Function × Seniority)

Personas with n ≥ 15 that materially change outcomes:

| Function | Seniority | n | Win rate | Lift vs overall (pp) |
|----------|-----------|---|----------|----------------------|
| Marketing | Director | 21 | 52.4% | +17.0 |
| Other | VP | 26 | 46.2% | +10.8 |
| IT/Tech | Director | 48 | 45.8% | +10.4 |
| Marketing | VP | 16 | 43.8% | +8.4 |
| IT/Tech | Manager | 23 | 26.1% | -9.3 |
| IT/Tech | IC | 16 | 25.0% | -10.4 |
| Other | Director | 38 | 23.7% | -11.7 |
| Other | Manager | 128 | 21.9% | -13.5 |

**Pattern:** Director/VP outperform; Manager/IC underperform → different framing (less "strategy," more "execution + unblockers").

---

## Output 2 — LinkedIn Channel Fit

**Direct Sales - LinkedIn only (n=119). Overall LinkedIn win rate: ~18.5%.**

| Function | Primary Service | n | Win rate | 95% Wilson CI | Recommendation |
|----------|-----------------|---|----------|---------------|----------------|
| Marketing | Creative | 11 | 54.5% | 28.0–78.7 | **RUN** (best-fit pocket) |
| Marketing | Marketing Services | 11 | 27.3% | 9.7–56.6 | TEST (sharpen offer) |
| Other | Marketing Services | 14 | 21.4% | 7.6–47.6 | TEST |
| Other | Data & Analytics | 12 | 8.3% | 1.5–35.4 | DON'T RUN |
| Other | Custom Dev | 30 | 6.7% | 1.8–21.3 | DON'T RUN |

---

## Target Lists (Function × Seniority × Service × Industry)

### Segment A: LinkedIn → Marketing × Creative

| Function | Seniority | Service | Industry | n | Win% | 95% CI |
|----------|-----------|---------|----------|---|------|--------|
| Marketing | Director | Creative | Software | 3 | 66.7 | 20.8–93.9 |
| Marketing | Manager | Creative | Software | 8 | 50.0 | 21.5–78.5 |

**Build list:** Marketing Director/VP/Manager, Creative intent or past engagement.

---

### Segment B: Email + LinkedIn → IT/Tech Director

| Function | Seniority | Service | Industry | n | Win% | 95% CI |
|----------|-----------|---------|----------|---|------|--------|
| IT/Tech | Director | Data & Analytics | Agriculture | 2 | 100 | 34.2–100 |
| IT/Tech | Director | Modern Workplace | Energy, Utilities, Waste | 3 | 66.7 | 20.8–93.9 |
| IT/Tech | Director | Modern Workplace | Business Services | 2 | 50.0 | 9.5–90.5 |
| IT/Tech | Director | Modern Workplace | Healthcare | 2 | 50.0 | 9.5–90.5 |
| IT/Tech | Director | Modern Workplace | Manufacturing | 2 | 50.0 | 9.5–90.5 |
| IT/Tech | Director | Custom Dev | Government | 2 | 100 | 34.2–100 |

**Build list:** IT Director, Director of IT, CIO; prioritize Energy, Healthcare, Business Services, Manufacturing.

---

### Segment C: Email → Data & Analytics (Director+)

| Function | Seniority | Service | Industry | n | Win% | 95% CI |
|----------|-----------|---------|----------|---|------|--------|
| IT/Tech | Director | Data & Analytics | Agriculture | 2 | 100 | 34.2–100 |
| IT/Tech | Director | Data & Analytics | Healthcare | 1 | 100 | — |
| Finance | C-level | Data & Analytics | Insurance | 1 | 100 | — |
| Other | VP | Data & Analytics | Finance | 1 | 100 | — |

**Build list:** Director+, Ops/Finance/IT (not analysts); avoid generic "we do analytics" framing.

---

Regenerate: `python3 scripts/persona_normalization.py` (from repo root)