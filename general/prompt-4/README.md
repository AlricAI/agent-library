# Prompt

> Build a new pipeline for **AI Energy Paradox — Is AI eating the clean energy transition?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Build a new pipeline for **AI Energy Paradox — Is AI eating the clean energy transition?**

**Context:** Utilize Bruin MCP and Bruin CLI, reference Bruin docs. Follow @AGENTS.md strictly — these are the rules for this repo. If you are about to break any rule in AGENTS.md, stop and ask for clarification and permission before proceeding.

### Thesis

Renewables overtook coal globally for the first time in H1 2025 (34.3% vs 33.1%). But AI data center energy demand is projected to double by 2030 (415 TWh → 945 TWh). Ireland's data centers already consume 21% of national electricity. AI-optimized servers alone are forecast to go from 93 TWh to 432 TWh. The question: are AI's energy demands canceling out the gains from the renewable transition?

This pipeline combines global electricity generation data, AI/data center energy consumption estimates, EV adoption figures, and energy commodity prices to quantify the paradox and show where the tipping points are — by country, by year, and by energy source.

---

### Data sources

#### 1. Ember Global Electricity Data (primary)

- **What:** Annual and monthly electricity generation by source, capacity, demand, and emissions for 215 countries
- **Access:** Free API at `https://ember-energy.org/data/api/` — also available as bulk CSV downloads from `https://ember-climate.org/data-catalogue/yearly-electricity-data/`
- **License:** CC-BY-4.0
- **Freshness:** Updated biweekly; 2024 complete for 88 countries covering 93% of global demand
- **Key fields:**
  - Country, year (annual data back to 2000+)
  - Generation by source (TWh): coal, gas, oil, nuclear, hydro, wind, solar, bioenergy, other renewables
  - Total generation, total demand
  - Capacity (GW) by source
  - CO2 emissions from electricity (MtCO2)
  - Emissions intensity (gCO2/kWh)
  - Share of generation by source (%)
- **Endpoints to try:**
  - `/electricity-generation/yearly` — generation by country, year, source
  - `/electricity-generation/monthly` — monthly granularity

*[truncated — see source for full prompt]*