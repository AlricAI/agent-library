# Week3

> Diya: Created frontend framework for the diff.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Diya: Created frontend framework for the diff. studios, added ImageStudio.tsx + FinanceStudio.tsx, did not push to main yet

# NISHANT

## Weekly Summary
- Week 3 was the first week where planning turned into real implementation work across both the frontend and backend.
- On the frontend, I focused on setting up React Router v6 and building the Protected Route wrapper so the app could reliably redirect unauthenticated users and enforce access control across all studio pages.
- On the backend, I began enabling Row Level Security on the core database tables and drafting the policies that would ensure users could only access data within their own workspace.

## Work Completed
- Set up React Router v6 for all planned app pages including the landing page, pricing page, auth pages, and all studio routes.
- Built the Protected Route wrapper component that checks for an active Supabase session and redirects unauthenticated users to the login page.
- Configured the routing structure so the protected dashboard and studio pages were wrapped inside the auth guard without duplicating layout logic.
- Enabled Row Level Security on all core database tables including workspaces, artifacts, runs, and run steps.
- Drafted initial RLS policies scoped to workspace membership so users could only read and write data associated with their own workspace.
- Began testing session persistence behavior across the new protected routes to ensure auth state was correctly restored after page refreshes.

## Research / Technical Findings
- React Router v6 nested routing with `<Outlet>` makes it straightforward to apply shared layout components to all protected pages without wrapping each one individually.
- Supabase RLS policies work best when written against a workspace membership join table rather than user IDs directly, which makes the access rules more flexible and easier to extend.
- Testing session persistence requires simulating real browser behaviors like page reload and direct URL navigatio

*[truncated — see source for full prompt]*