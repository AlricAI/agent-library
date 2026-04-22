# FILE INVENTORY

> | Path | Category | Runtime critical | Risk | Action | Test coverage |
|------|----------|------------------|------|--------|---------------|
| admin/

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend File Inventory

| Path | Category | Runtime critical | Risk | Action | Test coverage |
|------|----------|------------------|------|--------|---------------|
| admin/e2e/api-smoke.spec.ts | test | no | low | keep | e2e |
| admin/e2e/auth-dashboard.spec.ts | test | no | low | keep | e2e |
| admin/e2e/devices.spec.ts | test | no | low | keep | e2e |
| admin/e2e/helpers.ts | test | no | low | keep | e2e |
| admin/e2e/nav-and-pages.spec.ts | test | no | low | keep | e2e |
| admin/e2e/negative-fallback.spec.ts | test | no | low | keep | e2e |
| admin/e2e/release-smoke.spec.ts | test | no | low | keep | e2e |
| admin/e2e/servers-users.spec.ts | test | no | low | keep | e2e |
| admin/e2e/smoke.spec.ts | test | no | low | keep | e2e |
| admin/e2e/telemetry-docker.spec.ts | test | no | low | keep | e2e |
| admin/index.html | core | yes | low | keep | none |
| admin/package.json | config | no | low | keep | none |
| admin/playwright.config.ts | config | no | low | keep | none |
| admin/postcss.config.js | config | no | low | keep | none |
| admin/src/layout/shell.css | style | yes | low | keep | none |
| admin/src/api/client.ts | api | yes | high | keep | none |
| admin/src/api/query-keys.ts | api | yes | low | keep | none |
| admin/src/App.tsx | core | yes | high | keep | none |
| admin/src/charts/chartConfig.ts | util | yes | low | keep | none |
| admin/src/charts/ChartFrame.tsx | component | yes | low | keep | none |
| admin/src/charts/echarts-lite.ts | util | yes | low | keep | none |
| admin/src/charts/EChart.tsx | component | yes | med | keep | none |
| admin/src/charts/presets/opsSparkline.ts | util | yes | low | keep | none |
| admin/src/charts/presets/opsTimeseries.ts | util | yes | low | keep | none |
| admin/src/charts/telemetry/CpuPctChart.tsx | component | yes | low | keep | none |
| admin/src/charts/telemetry/DiskRateChart.tsx | component | yes | low | keep | none |
| admin/src/charts/telemetry/ErrorsPerMinuteChart.tsx | component | yes | low | keep |

*[truncated — see source for full prompt]*