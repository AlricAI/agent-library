# TOOLS

> Reference patterns for RiderBeacon, Supabase Realtime, friend dots, APNs, and rally points.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Social Riding Engineer

Reference patterns for RiderBeacon, Supabase Realtime, friend dots, APNs, and rally points. Read sections on demand — do not load all of this upfront.

---

## 1. Supabase Table Migrations (Reference Only — Do Not Auto-Run)

These are the canonical schemas. Apply via `mcp__supabase__apply_migration` when the tables do not yet exist.

### rider_beacons

```sql
CREATE TABLE IF NOT EXISTS public.rider_beacons (
  id            UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id       UUID NOT NULL REFERENCES auth.users(id) ON DELETE CASCADE,
  lat           DOUBLE PRECISION NOT NULL,   -- rounded to 5 decimals at service layer
  lng           DOUBLE PRECISION NOT NULL,   -- rounded to 5 decimals at service layer
  heading       DOUBLE PRECISION,            -- degrees, 0-360, nullable
  speed         DOUBLE PRECISION,            -- m/s, nullable
  ride_id       UUID,                        -- nullable — null means exploring, not on a ride
  updated_at    TIMESTAMPTZ NOT NULL DEFAULT now()
);

-- One row per user, upserted on every update
CREATE UNIQUE INDEX IF NOT EXISTS rider_beacons_user_id_idx ON public.rider_beacons(user_id);

-- TTL enforcement: rows older than 30s are considered offline
-- Application layer checks: now() - updated_at > 30s → treat as offline

-- RLS
ALTER TABLE public.rider_beacons ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Authenticated users can read all beacons"
  ON public.rider_beacons FOR SELECT
  TO authenticated USING (true);

CREATE POLICY "Users can upsert their own beacon"
  ON public.rider_beacons FOR INSERT
  TO authenticated WITH CHECK (user_id = auth.uid());

CREATE POLICY "Users can update their own beacon"
  ON public.rider_beacons FOR UPDATE
  TO authenticated USING (user_id = auth.uid());

CREATE POLICY "Users can delete their own beacon"
  ON public.rider_beacons FOR DELETE
  TO authenticated USING (user_id = auth.uid());
```

### rally_points

```sql
CREATE TABLE IF NOT EXISTS pu

*[truncated — see source for full prompt]*