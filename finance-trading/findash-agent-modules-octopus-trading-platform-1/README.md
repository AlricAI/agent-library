# Findash Agent Modules (Octopus Trading Platform)

> description: Findash/Octopus 11-agent architecture; apply when editing agent modules or orchestrator. globs: src/core/intelligence_orchestrator.py, src/data_processing/**/*.py, src/analytics/**/*.py, src/strategies/**/*.py, src/prediction/**/*.py, src/risk/**/*.py, src/backtesting/**/*.py, src/realt

## System Prompt
---
description: Findash/Octopus 11-agent architecture; apply when editing agent modules or orchestrator.
globs: src/core/intelligence_orchestrator.py, src/data_processing/**/*.py, src/analytics/**/*.py, src/strategies/**/*.py, src/prediction/**/*.py, src/risk/**/*.py, src/backtesting/**/*.py, src/realtime/**/*.py, src/portfolio/**/*.py, src/alternative_data/**/*.py, src/infrastructure/market_data*.py, src/api/endpoints/agents*.py
alwaysApply: false
---

# Findash Agent Modules (Octopus Trading Platform)

You are working in a codebase that implements **11 orchestrated AI agents** (M1–M11). Respect each agent’s responsibility and code locations so changes stay consistent and pipeline-safe.

## Agent → Code Map

| Agent ID | Name | Code Paths | Capabilities |
|----------|------|------------|--------------|
| **M1** | Data Collector | `src/data_processing/` (scraping/, ingestion/, collection_tasks), `src/infrastructure/market_data_*.py`, `src/services/market_data_service.py` | web_scraping, api_fetching, market_data, validation |
| **M2** | Data Warehouse | `src/database/`, `src/analytics/warehouse.py` | data_storage, retrieval, validation, indexing |
| **M3** | Real-time Processor | `src/realtime/`, `src/api/endpoints/realtime.py`, `src/api/endpoints/websocket*.py`, `src/infrastructure/market_data_consumer_service.py` | stream_processing, real_time_analysis, alerts, WebSocket |
| **M4** | Strategy Agent | `src/strategies/` (strategy_agent, signal_fusion) | strategy_execution, signal_generation, backtesting |
| **M5** | ML Models | `src/training/`, `src/api/routes/ml_models.py` | prediction, classification, deep_learning |
| **M6** | Risk Manager | `src/risk/`, `src/compliance/` | risk_assessment, portfolio_optimization, compliance |
| **M7** | Price Predictor | `src/prediction/` (advanced_prediction_agent, prophet_service) | time_series_forecasting, prophet, neural_networks |
| **M8** | Paper Trader | `src/trading/` (simulated execution) | simulated_trading, execution

*[truncated — see source for full prompt]*