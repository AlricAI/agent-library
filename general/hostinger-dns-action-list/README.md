# Hostinger Dns Action List

> Last updated: 2026-04-14

This is your punch list for Hostinger DNS. Everything below goes under
**Hostinger → Domains → coherencedaddy.com → DNS / Na

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hostinger DNS — What to Add Right Now

Last updated: 2026-04-14

This is your punch list for Hostinger DNS. Everything below goes under
**Hostinger → Domains → coherencedaddy.com → DNS / Nameservers → Manage DNS
Records**. You only need to touch one zone — `coherencedaddy.com` — because
every subdomain we care about is a CNAME under that zone.

## Current DNS state (verified 2026-04-14)

All 6 existing subdomains already resolve and serve `200 OK`:

| Subdomain | Status | Serves |
|---|---|---|
| `coherencedaddy.com` (apex + www) | ✅ live | Next.js landing (Vercel) |
| `directory.coherencedaddy.com` | ✅ live | Directory home (Vercel, middleware rewrite) |
| `freetools.coherencedaddy.com` | ✅ live | 523+ free tools (Vercel, middleware rewrite) |
| `token.coherencedaddy.com` | ✅ live | Daddy Token migration (Vercel, middleware rewrite) |
| `law.coherencedaddy.com` | ✅ live | Coherence Law (Vercel, middleware rewrite) |
| `optimize-me.coherencedaddy.com` | ✅ live | YourArchi / OptimizeMe (Vercel, middleware rewrite) |
| `shop.coherencedaddy.com` | ✅ live | Stripe + Printify shop |
| `partners.coherencedaddy.com` | ❌ not configured | **(needs DNS — see below)** |

**Do not touch any of the ✅ rows — they are already correct. The only action
item is partners.**

---

## Action 1 — Add `partners.coherencedaddy.com` (required for partner expansion)

The partner-network expansion is building a public-facing partner directory
at `partners.coherencedaddy.com`. Hostinger needs one new CNAME record.

### Step 1: Add DNS record in Hostinger

**Hostinger → coherencedaddy.com → DNS/Nameservers → Manage DNS records → Add record**

| Field | Value |
|---|---|
| Type | `CNAME` |
| Name | `partners` |
| Target / Points to | `cname.vercel-dns.com` |
| TTL | `3600` (1 hour) — or whatever Hostinger calls "default" |

Save. Propagation usually takes 1–5 minutes on Hostinger's resolvers, up to 15
minutes worst case.

### Step 2: Add domain in Vercel

After the DNS propagates, go to **Verc

*[truncated — see source for full prompt]*