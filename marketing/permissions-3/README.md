# PERMISSIONS

> ## Overview

Sighthound Content Relay uses a comprehensive permission system with **92 total permissions** across 4 roles:
- **Admin**: All permission

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Permission System Documentation

## Overview

Sighthound Content Relay uses a comprehensive permission system with **92 total permissions** across 4 roles:
- **Admin**: All permissions (76 delegable + 9 admin-locked = 85 total)
- **Writer**: 28 permissions by default
- **Publisher**: 23 permissions by default
- **Editor**: 17 permissions by default

Permissions control what authenticated users can do within the application. They are enforced at three levels:
1. **Database (RLS)**: Row-level security policies
2. **API**: Endpoint-level permission checks
3. **UI**: Feature hiding/disabling based on permissions

## Permission Categories

### Blog Management (15 permissions)

**Creation & Editing**
- `create_blog` — Create new blog drafts
- `edit_blog_metadata` — Edit blog cover image, featured image, metadata
- `edit_blog_title` — Edit blog title
- `edit_blog_description` — Edit blog description
- `edit_tags` — Add/remove blog tags
- `edit_blog_category` — Set blog category
- `edit_internal_notes` — Add internal notes not visible to readers
- `edit_external_links` — Add external links and resources

**Archival**
- `archive_blog` — Archive blog to hidden state
- `restore_archived_blog` — Restore archived blog
- `view_archived_blogs` — View archived blog list
- `delete_blog` — Hard delete blogs (admin-locked)

**Operations**
- `duplicate_blog` — Create copy of blog

**Workflow Fields** (ownership-based, not permission-gated)
- `edit_google_doc_link` — Update Google Doc link (ownership enforced by RLS)

### Writing Workflow (6 permissions)

- `start_writing` — Begin writing stage
- `pause_writing` — Pause writing work
- `submit_draft` — Submit draft for review
- `request_revision` — Request writer revisions
- `edit_writer_status` — Manually set writer stage (admin-like)
- `view_writing_queue` — Access writer queue

### Publishing Workflow (6 permissions)

- `start_publishing` — Begin publishing stage
- `complete_publishing` — Mark blog as published
- `edit_publisher_sta

*[truncated — see source for full prompt]*