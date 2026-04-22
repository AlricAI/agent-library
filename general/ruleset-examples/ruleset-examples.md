---
name: Ruleset Examples
description: End-to-end examples showing how full rulesets are composed from tenant rules.
model: claude-sonnet-4-5
---
# Ruleset Examples (v0)

End-to-end examples showing how full rulesets are composed from tenant rules. Tenant rules can be materialised from global rule templates or authored from scratch.
Template selection is metadata; the DSL files are just rule text.

## Template: "US Payroll v2025" (read-only, used to create tenant rules)

```dsl
rule "us-daily-overtime" salience: 50 do
  when
    ts: TimesheetEntry(employee_id: e, hours: h, start_at: s)
    policy: OvertimePolicy(period: :daily, threshold_hours: t, multiplier: m)
    guard h > t
  then
    emit PayLine(employee_id: e, period_key: to_day(s), component: :overtime, hours: h - t, rate: m)
end

rule "holiday-premium-global" salience: 20 do
  when
    shift: ScheduledShift(employee_id: e, start_at: s, end_at: f, location: loc)
    hol: HolidayCalendar(location: base_location(loc), date: to_day(s), premium_multiplier: m)
  then
    emit PayLine(employee_id: e, period_key: to_day(s), component: :holiday_premium, hours: duration_hours(s, f), rate: m)
end
```

## Template: "US-CA Labour v2025" (read-only, used to create tenant rules)

```dsl
rule "ca-weekly-overtime" salience: 60 do
  when
    agg: WeeklyHours(employee_id: e, week: w, hours: h)
    policy: OvertimePolicy(period: :weekly, threshold_hours: t, multiplier: m)
    guard h > t
  then
    emit PayLine(employee_id: e, period_key: w, component: :overtime, hours: h - t, rate: m)
end

rule "ca-min-wage" salience: 55 do
  when
    shift: ScheduledShift(employee_id: e, start_at: s, end_at: f, location: "US/CA")
    law: LocationRegulation(location: "US/CA", constraint_type: :min_wage, params: p)
    rate: PayRate(employee_id: e, rate_type: :hourly, base_rate: r)
    guard r < p.min_wage
  then
    emit ComplianceViolation(employee_id: e, period_key: to_day(s), code: "MIN_WAGE", severity: :high, details: "Base #{r} < #{p.min_wage}")
end
```

## Tenant rules: "Acme Corp Overrides v3" (editable by tenant; some created from templates above)

```dsl
rule "tenant-approved-timesheets-only" salience: 90 do
  when
    ts: TimesheetEntry(employee_id: e, approved?: a, start_at: s, end_at: f)
    guard a == true
  then
    emit ProcessingGate(kind: :timesheet_ok, employee_id: e, token: "#{ts.id}")
end

rule "holiday-premium-city-override" salience: 85 do
  when
    shift: ScheduledShift(employee_id: e, start_at: s, end_at: f, location: "US/CA/SF")
    hol: HolidayCalendar(location: "US/CA/SF", date: to_day(s), premium_multiplier: m)
  then
    emit PayLine(employee_id: e, period_key: to_day(s), component: :holiday_premium, hours: duration_hours(s, f), rate: m + 0.25)
end

rule "overtime-weekly-tenant-exception" salience: 95 do
  when
    agg: WeeklyHours(employee_id: e, week: w, hours: h, union: :u123)
    policy: OvertimePolicy(period: :weekly, threshold_hours: t, multiplier: m)
    guard h > t - 4
  then
    emit PayLine(employee_id: e, period_key: w, component: :overtime, hours: h - (t - 4), rate: m)
end
```

## Ruleset assembly (manifest, not DSL)

Templates used to create rules:

- US Payroll v2025 (version: 2025.1)
- US-CA Labour v2025 (version: 2025.2)

Tenant rules:

- Acme Corp Overrides v3 (version: 3)

Order (optional salience offset):

- [US Payroll-derived, US-CA Labour-derived, Tenant Overrides]

Result:

- Parse/validate each tenant rule file → compile to IR fragments → merge into a single IR per ruleset version (see `specs/rulesets.md`).
- Persist compiled IR + manifest; orchestrator loads by ruleset version.