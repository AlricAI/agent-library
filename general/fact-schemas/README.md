# Fact Schemas

> This document defines canonical shapes for facts (WMEs) ingested by the engine and facts derived by rules.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fact Schemas — Canonical WMEs and Derived Facts

This document defines canonical shapes for facts (WMEs) ingested by the engine and facts derived by rules. These schemas aim to be stable across use cases and optimized for Alpha/Beta discrimination.

## Conventions

- IDs: `id` is a stable string or integer. Referential fields end with `_id`.
- Time: Use `DateTime` with timezone for instants; `Date` for all-day items; effective windows use `[effective_from, effective_to)` (to is exclusive).
- Keys: Discriminating keys used by Alpha indexes include `type`, `employee_id`, `location`, dates, and scenario identifiers.
- Precision: Monetary amounts use `Decimal`.
- Structs: Example Elixir structs shown for clarity; maps with equivalent keys are also accepted.

## Core WMEs

- Employee
  - Fields: `id`, `role`, `location`, `union`, `employment_type`, `effective_from`, `effective_to`
  - Example:
    - `%Employee{id: "e1", role: :nurse, location: "CA/SF", union: :u123, employment_type: :hourly, effective_from: ~U[2025-01-01 00:00:00Z], effective_to: nil}`
- TimesheetEntry
  - Fields: `id`, `employee_id`, `start_at`, `end_at`, `hours` (optional; computed if nil), `project_id`, `cost_center`, `approved?`
  - Example: `%TimesheetEntry{id: "t1", employee_id: "e1", start_at: dt("2025-02-10T09:00-08:00[America/Los_Angeles]"), end_at: dt("2025-02-10T17:30-08:00[America/Los_Angeles]"), project_id: "p1", cost_center: "c10", approved?: true}`
- PayRate
  - Fields: `id`, `employee_id` | `role`, `rate_type` (:hourly | :salary), `base_rate` (Decimal), `effective_from`, `effective_to`
  - Example: `%PayRate{id: "r1", role: :nurse, rate_type: :hourly, base_rate: D.new("45.00"), effective_from: dt("2025-01-01Z"), effective_to: nil}`
- OvertimePolicy
  - Fields: `id`, `jurisdiction` | `union`, `threshold_hours`, `multiplier`, `period` (:daily | :weekly), `effective_from`, `effective_to`
- Holiday
  - Fields: `id`, `date` (Date), `location`, `premium_multiplier`
- ShiftDifferential
  - Fie

*[truncated — see source for full prompt]*