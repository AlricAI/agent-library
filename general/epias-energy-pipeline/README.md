# EPIAS Energy Pipeline

> ## Architecture

```mermaid
flowchart LR
    subgraph raw [Raw Layer - Python]
        RT[epias_realtime_generation]
        DPP[epias_dpp_first_versi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# EPIAS Energy Market Pipeline

## Architecture

```mermaid
flowchart LR
    subgraph raw [Raw Layer - Python]
        RT[epias_realtime_generation]
        DPP[epias_dpp_first_version]
        MCP[epias_mcp]
        SMP[epias_smp]
    end
    subgraph staging [Staging Layer - SQL]
        GD[epias_generation_daily]
        FVA[epias_forecast_vs_actual]
        MPD[epias_market_prices_daily]
    end
    subgraph reports [Reports Layer]
        APP[streamlit_app]
    end
    RT --> GD
    RT --> FVA
    DPP --> FVA
    MCP --> MPD
    SMP --> MPD
    GD --> APP
    FVA --> APP
    MPD --> APP
```



## Directory Structure

```
epias-energy/
├── pipeline.yml
└── assets/
    ├── raw/
    │   ├── requirements.txt
    │   ├── epias_realtime_generation.py
    │   ├── epias_dpp_first_version.py
    │   ├── epias_mcp.py
    │   └── epias_smp.py
    ├── staging/
    │   ├── epias_generation_daily.sql
    │   ├── epias_forecast_vs_actual.sql
    │   └── epias_market_prices_daily.sql
    └── reports/
        ├── requirements.txt
        └── streamlit_app.py
```

## EPIAS API Authentication

Every Python asset needs a TGT (Ticket Granting Ticket) for API access. Credentials are in `[.bruin.yml](.bruin.yml)` as generic secrets (`epias_username`, `epias_password`), accessible via `os.environ` in Bruin Python assets.

```python
def get_tgt():
    url = "https://giris.epias.com.tr/cas/v1/tickets"
    data = f"username={os.environ['epias_username']}&password={os.environ['epias_password']}"
    headers = {"Content-Type": "application/x-www-form-urlencoded", "Accept": "text/plain"}
    resp = requests.post(url, data=data, headers=headers)
    resp.raise_for_status()
    return resp.text.strip()
```

API calls use `POST` with JSON body, TGT in header, dates in ISO-8601 Turkish timezone (`2025-03-03T00:00:00+03:00`).

## Pipeline Config

- **Pipeline name**: `epias-energy`
- **Schedule**: `daily`
- **Start date**: `"2025-03-01"`
- **Default connection**: `bruin-playground-arsalan`

## R

*[truncated — see source for full prompt]*