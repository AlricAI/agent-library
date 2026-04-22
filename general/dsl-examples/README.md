# Dsl Examples

> Illustrative rules spanning multiple domains and layered scopes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DSL Examples (v0)

Illustrative rules spanning multiple domains and layered scopes. Scope (tenant/general and any attributes like country/state/city/org_type) is metadata stored with the rule, not part of the DSL text.

## General rules (examples)

```dsl
rule "us-daily-overtime" salience: 50 do
  when
    ts: TimesheetEntry(employee_id: e, hours: h, start_at: d)
    policy: OvertimePolicy(period: :daily, threshold_hours: t, multiplier: m)
    guard h > t
  then
    emit PayLine(employee_id: e, period_key: to_day(d), component: :overtime, hours: h - t, rate: m)
end
```

```dsl
rule "sf-min-wage" salience: 60 do
  when
    shift: ScheduledShift(employee_id: e, start_at: s, end_at: f, location: "US/CA/SF", planned_hours: h)
    law: LocationRegulation(location: "US/CA/SF", constraint_type: :min_wage, params: p)
    rate: PayRate(employee_id: e, rate_type: :hourly, base_rate: r)
    guard r < p.min_wage
  then
    emit ComplianceViolation(employee_id: e, period_key: to_day(s), code: "MIN_WAGE", severity: :high, details: "Base #{r} < #{p.min_wage}")
end
```

```dsl
rule "hospital-overtime-multiplier" salience: 55 do
  when
    pr: PayRate(employee_id: e, rate_type: :hourly, base_rate: r)
    emp: Employee(id: e, employment_type: :hourly, role: role)
    org: OrgType(name: :hospital)
    guard role in ["RN","MD","ER_TECH"]
  then
    emit RateAdjustment(employee_id: e, component: :overtime_multiplier, factor: 1.5)
end
```

## Tenant-specific rules (examples)

```dsl
rule "tenant-shift-premium-night" salience: 40 do
  when
    shift: ScheduledShift(employee_id: e, start_at: s, end_at: f, location: loc)
    guard hour(s) between 22 and 23 or hour(s) between 0 and 5
  then
    emit PayLine(employee_id: e, period_key: to_day(s), component: :premium, hours: hours_between(s, f, :night), rate: 1.2)
end
```

```dsl
rule "tenant-approved-timesheets-only" salience: 90 do
  when
    ts: TimesheetEntry(employee_id: e, approved?: a, start_at: s, end_at: f)
    guard a == true
  the

*[truncated — see source for full prompt]*