# SECURITY AUDIT

> **Date:** April 3, 2026
**Team:** Team A (Security, Supabase, Auth)
**Status:** Remediated

---

## 1. Exposed Secrets in Git History

The `.env` file

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Audit Report — Reese Reviews

**Date:** April 3, 2026
**Team:** Team A (Security, Supabase, Auth)
**Status:** Remediated

---

## 1. Exposed Secrets in Git History

The `.env` file was committed to the repository in commit `21fbdf41` (initial creation) and remained tracked through commit `6249c8d` and beyond. The following secrets were exposed in the public git history:

| Secret | Type | Risk Level | Action Required |
| :--- | :--- | :--- | :--- |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | Supabase anon/public key | **Medium** | Rotate recommended; this is a public-facing key but grants RLS-scoped access |
| `VITE_SUPABASE_URL` | Supabase project URL | **Low** | Public by design, but confirms project identity |
| `VITE_SUPABASE_PROJECT_ID` | Supabase project ID | **Low** | Public identifier |
| `VITE_OPENROUTER_API_KEY` | OpenRouter API key | **HIGH** | **Must rotate immediately** — grants full API access and incurs billing |

### Rotation Recommendations

1. **OpenRouter API Key** — Go to [openrouter.ai/keys](https://openrouter.ai/keys), revoke the exposed key `sk-or-v1-413334f6...`, and generate a new one. Update the `.env` on the production server.

2. **Supabase Anon Key** — The anon key is designed to be public (embedded in client-side code). However, since it was committed alongside the project URL, an attacker could craft requests. Ensure Row Level Security (RLS) policies are properly configured on all tables. Consider rotating via Supabase Dashboard > Settings > API if desired.

3. **Supabase Service Role Key** — Verify this key was **never** committed. It was not found in the `.env` file, which is correct. The service role key must only exist on the server.

---

## 2. Hardcoded Secrets in Source Code

| File | Secret | Risk | Remediation |
| :--- | :--- | :--- | :--- |
| `src/contexts/AuthContext.tsx` | `VALID_PASSWORD = "WizOz#123"` | **HIGH** — plaintext password in client JS bundle | Replaced with Supabase Auth; fallback password moved to env var |

*[truncated — see source for full prompt]*