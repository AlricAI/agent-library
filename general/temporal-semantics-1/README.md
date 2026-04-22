# Temporal Semantics

> Defines time handling and period logic to ensure consistent matching across domains.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Temporal Semantics

Defines time handling and period logic to ensure consistent matching across domains.

## Timezones and Instants

- All instants use `DateTime` with explicit timezone; UTC is recommended for storage. If local business rules depend on local time, retain the original zone.
- Conversions: For comparisons, convert to a canonical zone while preserving local semantics when bucketizing.

## Effective Windows

- Representation: `[effective_from, effective_to)` — to is exclusive; `nil` means open-ended.
- Membership: `t ∈ window` iff `effective_from <= t` and `(effective_to == nil or t < effective_to)`.
- Overlap: Two windows overlap if `a.start < b.end and b.start < a.end` treating `nil` as +∞.

## Bucketization

- Day bucket: Local midnight-to-midnight per employee/location timezone.
- Week bucket: ISO week (`{year, week}`) by local timezone unless jurisdiction requires otherwise.
- Boundary crossings: Split shifts/facts deterministically at boundaries, allocating proportional hours/amounts.

## DST Handling

- Spring forward: Missing hour reduces shift length; no phantom hours are added.
- Fall back: Repeated hour counts twice if worked; compute using zoned `DateTime.diff/3`.
- Display vs compute: Always compute using timezone-aware arithmetic; display can be localized.

## Period Keys

- Day: `{:day, tz, date}` where `date` is local date in `tz`.
- Week: `{:week, tz, year, iso_week}`.
- Custom periods can extend this tuple with a tagged atom.

## Overlap With Windows

- When joining by effectiveness (e.g., PayRate ↔ TimesheetEntry), require non-empty overlap between the entry interval and the rate window.
- Mid-period changes yield multiple derived facts split by overlap proportion.