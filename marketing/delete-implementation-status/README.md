# DELETE IMPLEMENTATION STATUS

> ## Current state

### Implemented REST delete endpoints
- **Social Posts**: `DELETE /api/social-posts/[id]` (`src/app/api/social-posts/[id]/route.ts`)

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Delete Functionality Implementation Status

## Current state

### Implemented REST delete endpoints
- **Social Posts**: `DELETE /api/social-posts/[id]` (`src/app/api/social-posts/[id]/route.ts`)
- **Ideas**: `DELETE /api/ideas/[id]` (`src/app/api/ideas/[id]/route.ts`)
- **Legacy ideas endpoint (retired)**: `DELETE /api/ideas/[id]/delete` now returns `410 Gone` and no longer proxies requests.

### Not yet implemented as REST endpoint
- **Blogs**: `DELETE /api/blogs/[id]` does **not** currently exist.
- Blog delete operations are currently executed from UI surfaces through direct Supabase mutations, with database RLS as the hard authorization boundary.

## Behavior by resource

### Social posts
- Requires `delete_social_post` permission at API boundary.
- Defense-in-depth ownership check in route: creator or admin only.
- Published posts are blocked (`status === "published"`).
- Idempotent success behavior:
  - If record does not exist, route returns `200` with `"Post already deleted"`.
  - If record is deleted, route returns `200` with `deletedPostId` and `deletedPostTitle`.

### Ideas
- Requires `delete_idea` permission at API boundary.
- Defense-in-depth ownership check in route: creator or admin only.
- No published-state guard for ideas.
- Idempotent success behavior:
  - If record does not exist, route returns `200` with `"Idea already deleted"`.
  - If record is deleted, route returns `200` with `deletedIdeaId` and `deletedIdeaTitle`.
- Legacy compatibility note:
  - `DELETE /api/ideas/[id]/delete` is retired and always returns `410 Gone`.
  - Clients must call `DELETE /api/ideas/[id]`.

### Blogs
- No dedicated API delete route yet.
- Database RLS policies enforce delete safety:
  - creator/admin only
  - published blogs blocked (`publisher_status = 'completed'`)
- Linked social posts are not a hard DB delete blocker; `social_posts.associated_blog_id` uses `ON DELETE SET NULL`.

## Database safety layer
- `prevent_delete_published_social_posts` policy blocks

*[truncated — see source for full prompt]*