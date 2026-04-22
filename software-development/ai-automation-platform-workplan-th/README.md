# AI AUTOMATION PLATFORM WORKPLAN TH

> ## 0) Context (CODEX /CREATE_PLATFORM_WORK)
- **Initiative:** Aetherium Cross-Tool AI Automation Platform
- **Scope:** Intent ingestion, planner engin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Automation Platform Work Plan (Zapier + AI) — Intent → Workflow ข้ามเครื่องมือ

## 0) Context (CODEX /CREATE_PLATFORM_WORK)
- **Initiative:** Aetherium Cross-Tool AI Automation Platform
- **Scope:** Intent ingestion, planner engine, execution runtime ผ่าน Vessels, intent templates, reusable automations, Akashic ledger audit layer, SRE/Ops controls
- **Drivers:** reliability, latency ที่คาดการณ์ได้, security/compliance, devex สำหรับการเพิ่ม integration ใหม่เร็วขึ้น, ต้นทุนต่อ automation run ต่ำลง
- **Current state (as-is):** มีโครงสร้าง governance, vessel abstraction, และ ledger primitives อยู่แล้ว แต่ยังไม่มี orchestration ที่ครบวงจรจาก intent → plan → execute แบบข้ามเครื่องมือพร้อมมาตรฐาน audit เดียวกัน
- **Target state (to-be):** แพลตฟอร์มที่รับ intent, สร้างแผนงานอัตโนมัติ, dispatch งานไปยังหลายเครื่องมือผ่าน Vessels, รองรับ approval/policy gates และบันทึกทุก event ลง Akashic ledger เพื่อ trace + audit ได้ end-to-end
- **Constraints:**
  - SLO: P95 orchestration latency < 2.5s (plan) และ < 8s (first execution action)
  - Availability: 99.9% สำหรับ orchestration API
  - Budget: จำกัดค่า inference + integration API ต่อ run
  - Timeline: 3 เฟส (12 สัปดาห์)
  - Compliance: auditability, least privilege, data retention policy
- **Dependencies:** ทีม platform/backend, security/compliance, product ops, vendor APIs (Slack/Google Workspace/DB/CRM), LLM provider

---

## 1) Workstreams

### WS1 — Architecture
**เป้าหมาย:** สถาปัตยกรรม Intent-Orchestration ที่แยก concerns ชัดเจน (Trigger, Plan, Execute, Observe, Govern)

- นิยาม service boundaries: `Intent Gateway`, `Planner Service`, `Execution Orchestrator`, `Vessel Connectors`, `Akashic Ledger Writer`, `Policy/Approval Engine`
- กำหนด event model กลางและ correlation IDs สำหรับ trace ข้าม service
- ออกแบบ state machine ของ workflow run (Received → Planned → Approved → Running → Compensating/Completed/Failed)

### WS2 — Protocol
**เป้าหมาย:** มาตรฐานสัญญาข้อมูลสำหรับ intent templates, workflow plans, execution actions

*[truncated — see source for full prompt]*