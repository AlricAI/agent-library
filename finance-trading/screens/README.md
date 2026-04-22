# Screens

> This document describes the main screens required for the Marketing Dashboard, based on the feature list and user stories.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Screens Specification for Marketing Dashboard

This document describes the main screens required for the Marketing Dashboard, based on the feature list and user stories. Each screen includes its purpose, key components, and main interactions.

---

## 1. Login & Authentication Screen (LoginScreen.jpg)
**Purpose:** Secure user login, registration, and OAuth provider selection.
**Components:**
- Email/password fields
- Client-side validation (email required + format, password required)
- Inline user-safe error banner for auth failures
- Loading state on submit with duplicate-submit prevention
- OAuth provider buttons (currently visual placeholders)
- Forgot password link
- Registration link
- Firebase Email/Password sign-in integration
**Main Actions:**
- Emit `login_attempt`, `login_success`, `login_failure` auth analytics events
- Redirect authenticated users from `/login` to `/dashboard`
- Redirect to dashboard on successful login

---

## 2. Dashboard (Main Overview)
**Purpose:** Central hub showing content pipeline, stats, and quick actions.
**Components:**
- Content calendar (visual, clickable)
- Idea backlog summary
- Drafts/review queue
- Recent analytics (engagement, performance)
- Quick links to main features
**Main Actions:**
- Navigate to other screens
- View high-level stats

---

## 3. Idea Input & Backlog Screen (IdeaScreen.png)
**Purpose:** Submit new ideas, view and manage idea backlog.
**Components:**
- Free-form idea input box
- Optional dropdowns: tone, audience, format
- List/table of ideas with relevance/timeliness scores. 
- Sort/filter controls
- Trend detection panel (shows trending topics) As well as ability to click into the articles that are relevant.
- Competitor content panel (shows tracked competitor posts/gaps)
- Selected-idea card with a Generate Angles button that routes to `/angles?ideaId=<ideaDocId>`
**Main Actions:**
- Submit/edit/delete ideas
- Sort/filter backlog
- View trends and competitor analysis
- Trigger angles generation

*[truncated — see source for full prompt]*