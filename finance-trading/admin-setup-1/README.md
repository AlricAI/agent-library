# ADMIN SETUP

> This guide explains how to set up and manage admin users in the PACT marketplace.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Admin Setup Guide

This guide explains how to set up and manage admin users in the PACT marketplace.

## Table of Contents

- [Creating the First Admin](#creating-the-first-admin)
- [Admin Capabilities](#admin-capabilities)
- [Audit Logging](#audit-logging)
- [Security Considerations](#security-considerations)

---

## Creating the First Admin

For security reasons, admin accounts cannot be created through the public signup form. Instead, you must promote an existing user to admin role via the database.

### Step 1: Create a Regular Account

1. Go to the PACT signup page (`/signup`)
2. Create an account with a secure email and password
3. You can choose either "buyer" or "farmer" role initially

### Step 2: Find the User's UUID

Option A - Via Supabase Dashboard:
1. Go to your Supabase project dashboard
2. Navigate to **Authentication** > **Users**
3. Find the user and copy their UUID

Option B - Via SQL Query:
```sql
SELECT id, email, role FROM public.profiles WHERE email = 'your-email@example.com';
```

### Step 3: Promote to Admin

1. Open the Supabase SQL Editor
2. Open the seed script: `supabase/seed-admin.sql`
3. Replace `YOUR_USER_UUID_HERE` with the actual UUID
4. Run the script

**Example:**
```sql
DO $$
DECLARE
    target_user_id UUID := 'a1b2c3d4-e5f6-7890-abcd-ef1234567890';
BEGIN
    UPDATE public.profiles
    SET 
        role = 'admin',
        is_verified = true,
        updated_at = now()
    WHERE id = target_user_id;
    
    RAISE NOTICE 'User promoted to admin.';
END $$;
```

### Step 4: Verify

```sql
SELECT id, email, role, is_verified FROM public.profiles WHERE role = 'admin';
```

### Step 5: Access Admin Dashboard

1. Log in with the promoted account
2. You will be redirected to `/admin`

---

## Admin Capabilities

Admins have access to the following actions:

### User Management
| Action | Description |
|--------|-------------|
| Update User Role | Change a user's role (buyer/farmer/admin) |
| Suspend User | Temporarily disable a user a

*[truncated — see source for full prompt]*