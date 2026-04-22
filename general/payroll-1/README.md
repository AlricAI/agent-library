# Payroll

> ## Objective

Compute employee pay from timesheets, policies, and rates, including base pay, overtime, and premiums; emit `PayLine` facts suitable for

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Payroll — Use-Case Specification

## Objective

Compute employee pay from timesheets, policies, and rates, including base pay, overtime, and premiums; emit `PayLine` facts suitable for downstream payroll processing. Main focus is processing speed; use calculators for precise time and money maths (see calculators.md).

## Inputs (Facts)

- `Employee` (id, role, location, union, employment_type, effective_from/to)
- `TimesheetEntry` (id, employee_id, start_at, end_at, hours, project_id, cost_center, approved?)
- `PayRate` (id, employee_id or role, rate_type: :hourly|:salary, base_rate, effective_from/to)
- `OvertimePolicy` (id, jurisdiction or union, threshold_hours, multiplier, period: :daily|:weekly)
- `Holiday` (id, date, location, premium_multiplier)
- `ShiftDifferential` (id, window, multiplier or fixed, location/role filters)
- `Deduction`/`EarningRule` (optional adjustments, effective periods)

## Outputs (Derived Facts)

- `PayLine` (employee_id, period_key, component: :base|:overtime|:premium, hours, rate, amount, provenance)
- `PayrollSummary` (employee_id, period_key, gross_amount, breakdown)

## Alpha Network (Single-Fact Filters)

- Filter `TimesheetEntry` by `approved? == true`, date range, `employee_id`.
- Compute payable hours per shift using `time_between(start_at, end_at, :hours)` minus `break_minutes`/60 as applicable; store as a field for downstream joins/accumulations.
- Filter `PayRate` and `OvertimePolicy` by effective period, jurisdiction, role/union.
- Filter `Holiday` and `ShiftDifferential` by location/date/time window.

## Beta Network (Joins and Accumulations)

- Join `TimesheetEntry -> Employee` on `employee_id` to attach role/location.
- Join with applicable `PayRate` using role/employee match and effective window.
- Join with `OvertimePolicy` via jurisdiction/union and effective period.
- Premiums: Join with `Holiday`/`ShiftDifferential` where entry overlaps date/time window; use `overlap_hours/4` to compute premium hours precisely.
-

*[truncated — see source for full prompt]*