# DISPLAY DATE FALLBACK SPEC

> ## Overview
`display_published_date` must never be NULL. It defaults to `scheduled_publish_date` and supports intelligent fallback with activity loggi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Display Published Date Fallback Specification

## Overview
`display_published_date` must never be NULL. It defaults to `scheduled_publish_date` and supports intelligent fallback with activity logging.

## Database Schema Changes

### 1. Add NOT NULL Constraint with Default
```sql
-- Migration: Add NOT NULL constraint to blogs.display_published_date
ALTER TABLE public.blogs
  ADD CONSTRAINT display_published_date_not_null 
  CHECK (display_published_date IS NOT NULL);

-- Backfill existing rows with NULL display_published_date
UPDATE public.blogs
  SET display_published_date = COALESCE(scheduled_publish_date, CURRENT_DATE)
  WHERE display_published_date IS NULL;

-- Add column default for future inserts
ALTER TABLE public.blogs
  ALTER COLUMN display_published_date SET DEFAULT CURRENT_DATE;
```

### 2. Update Triggers for Fallback Logic

#### handle_blog_before_write() - INSERT path
```plpgsql
-- Add before INSERT logic:
if new.display_published_date is null then
  new.display_published_date := coalesce(new.scheduled_publish_date, current_date);
end if;
```

#### audit_blog_changes() - Track display_date changes
```plpgsql
-- Add after INSERT/UPDATE logic:
-- Only log if user EXPLICITLY set display_date different from scheduled_date (not default fallback)
if tg_op = 'INSERT' and new.display_published_date is distinct from new.scheduled_publish_date then
  insert into public.blog_assignment_history (blog_id, changed_by, event_type, field_name, new_value)
  values (new.id, auth.uid(), 'display_date_override', 'display_published_date', new.display_published_date::text);
end if;

-- On UPDATE: log all display_date changes
if tg_op = 'UPDATE' and new.display_published_date is distinct from old.display_published_date then
  insert into public.blog_assignment_history (blog_id, changed_by, event_type, field_name, old_value, new_value)
  values (new.id, auth.uid(), 'display_date_changed', 'display_published_date', old.display_published_date::text, new.display_published_date

*[truncated — see source for full prompt]*