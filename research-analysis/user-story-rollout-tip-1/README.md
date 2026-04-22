# User Story Rollout Tip

> ## Objective
Convert the feature list and user stories into an implementation sequence that can be executed by backend, frontend, database, automation

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Technical Implementation Plan: User Story Rollout

## Objective
Convert the feature list and user stories into an implementation sequence that can be executed by backend, frontend, database, automation, and security workstreams without creating downstream rework.

## Planning Assumptions
- Existing auth, article generation, saved-post, and connect foundations should be reused where they already exist.
- New work should extend the current FastAPI backend, Next.js frontend, Supabase schema, and Playwright-based publishing integrations.
- Features are grouped into delivery slices that each produce a usable outcome while preserving a clean dependency chain.

## Delivery Order
1. Foundation: workspace, idea, and content lifecycle schema
2. Idea intake, backlog, and scoring experience
3. AI ideation workflows: angles, selection, interview, and voice capture
4. Trend detection and competitor gap discovery
5. Core drafting and editing controls
6. Research grounding, citations, plagiarism, and refresh workflows
7. Multi-channel adaptation engine
8. Brand voice, multi-brand workspaces, and personalization
9. Review, approvals, RBAC, comments, and version history
10. Publishing integration foundation and guarded publish flow
11. Scheduling calendar, posting cadence, and IndexNow automation
12. Media enrichment and SEO optimization
13. Analytics, predictive scoring, AI visibility, and copy intelligence
14. Collaboration, client workflows, and agency management
15. Governance, compliance, auditability, and terminology enforcement
16. Monetization hooks and sponsored content controls
17. External integrations, public API, enterprise SSO, and sitemap updates

## Implementation Phases

### 1. Foundation: workspace, idea, and content lifecycle schema
Purpose: Establish the shared data model and backend contracts needed by all later idea, draft, adaptation, approval, and publishing features.

Covers:
- Shared content object model across ideas, drafts, adaptations, approvals, schedu

*[truncated — see source for full prompt]*