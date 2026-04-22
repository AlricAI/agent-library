# CUTOVER

> Migration from Strapi 5 to ivokun CMS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CMS Cutover Plan

Migration from Strapi 5 to ivokun CMS.

## Pre-Migration Checklist

### Infrastructure

- [ ] PostgreSQL database provisioned
- [ ] R2 bucket created with public access configured
- [ ] DNS records prepared (if changing domains)
- [ ] NixOS host configured with `services.ivokun-cms` module
- [ ] Secrets file created with all required environment variables
- [ ] Backup strategy in place for new database

### Strapi Preparation

- [ ] Strapi instance running and accessible
- [ ] API token generated with read access to all content types
- [ ] Note total counts: categories, posts, galleries, media files
- [ ] Identify any content currently in draft state (may need manual review)

### New CMS Preparation

- [ ] Binary built (`bun run build`)
- [ ] Database migrations applied (`bun run db:up`)
- [ ] Admin user created (`bun run seed:admin`)
- [ ] Test login to admin panel works
- [ ] API key generated for frontend

## Migration Steps

### Phase 1: Data Migration (Production Strapi -> New CMS)

```bash
# 1. Run dry-run first to verify
STRAPI_URL=https://strapi.ivokun.com \
STRAPI_TOKEN=your-token \
DATABASE_URL=postgres://... \
bun run migrate:strapi --dry-run

# 2. If dry-run looks good, run full migration
STRAPI_URL=https://strapi.ivokun.com \
STRAPI_TOKEN=your-token \
DATABASE_URL=postgres://... \
R2_ACCESS_KEY_ID=... \
R2_ACCESS_SECRET=... \
R2_ENDPOINT=... \
R2_BUCKET=... \
R2_PUBLIC_URL=... \
bun run migrate:strapi
```

### Phase 2: Verification

Run these queries against the new database:

```sql
-- Count verification
SELECT 'categories' as type, count(*) FROM categories
UNION ALL
SELECT 'posts', count(*) FROM posts
UNION ALL
SELECT 'galleries', count(*) FROM galleries
UNION ALL
SELECT 'media', count(*) FROM media;

-- Check for posts without content
SELECT id, title, slug FROM posts WHERE content IS NULL;

-- Check for media without URLs
SELECT id, filename FROM media WHERE urls IS NULL;

-- Verify published posts
SELECT count(*) FROM posts WHER

*[truncated — see source for full prompt]*