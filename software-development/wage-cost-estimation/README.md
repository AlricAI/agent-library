# Wage Cost Estimation

> ## Objective

Estimate wage costs (base, overtime, benefits, employer taxes) for planned or actual schedules. Produce `CostEstimate` facts by employee

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Wage Cost Estimation — Use-Case Specification

## Objective

Estimate wage costs (base, overtime, benefits, employer taxes) for planned or actual schedules. Produce `CostEstimate` facts by employee/team/project and time bucket. Use calculators for precise time and Decimal money maths (see calculators.md).

## Inputs (Facts)

- `ScheduledShift` (id, employee_id or role, start_at, end_at, planned_hours, location, project_id, scenario_id)
- `RateCard` (id, role or employee_id, base_rate, premiums, effective_from/to)
- `OvertimePolicy` (as in Payroll; may be role/location specific)
- `HolidayCalendar` (location, date, premium_multiplier)
- `ProjectAssignment` (employee_id, project_id, effective_from/to, cost_center)
- `Scenario` (id, name, parameters; optional toggles for rules)

## Outputs (Derived Facts)

- `CostEstimate` (scope: :employee|:team|:project, scope_id, bucket: :day|:week, hours, base_amount, overtime_amount, premium_amount, total_amount, scenario_id)
- `EstimateSummary` (scenario_id, totals by bucket and scope)

## Alpha Network (Single-Fact Filters)

- Filter `ScheduledShift` by `scenario_id`, date range, location.
- Filter `RateCard`, `OvertimePolicy`, `HolidayCalendar` by effective windows and scope.
- Filter `ProjectAssignment` by effective windows.

## Beta Network (Joins and Accumulations)

- Join `ScheduledShift` → `RateCard` via role/employee and effective period.
- Compute shift hours: `time_between/3` minus `break_minutes`/60 where available.
- Join with `OvertimePolicy` to compute base vs overtime components per bucket using `bucket/2-3` and Decimal ops.
- Join with `HolidayCalendar` and apply premium multipliers for overlapping dates; compute overlap with `overlap_hours/4`.
- Join with `ProjectAssignment` to attribute cost to project/cost centers.
- Accumulate by (scope, scope_id, bucket) to produce `CostEstimate` facts; sum with Decimal ops; apply percentage adds for employer taxes/benefits as separate components when needed.

## Example DS

*[truncated — see source for full prompt]*