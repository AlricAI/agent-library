# DEMO GUIDE

> This guide gives you **three ways** to show the Octopus (Findash) platform to investors — from zero-install (best) to full local run.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Demo Guide for Stakeholders (Fundraising)

This guide gives you **three ways** to show the Octopus (Findash) platform to investors — from zero-install (best) to full local run.

---

## Option A: Live demo URL (recommended)

**Best for stakeholders: one link, no install.**

1. **Deploy the app** (you do this once):
   - **Frontend:** Deploy to [Vercel](https://vercel.com) (connect GitHub repo, deploy `frontend-nextjs` or root with correct build settings).
   - **Backend:** Deploy to [Render](https://render.com), [Railway](https://railway.app), or similar (use `Dockerfile.fastapi` or Python runtime; add PostgreSQL and Redis from their dashboards).
   - Set **environment variables** on both (see repo `config/env.example`). On the frontend, set `NEXT_PUBLIC_API_URL` to your backend URL (e.g. `https://your-api.onrender.com`).

2. **Share the frontend URL** with stakeholders, e.g.:
   - `https://findash-demo.vercel.app`  
   Or your custom domain.

3. **Stakeholders:** Open the link in a browser. No install, no dependencies.

**Suggested flow during the call:**  
Dashboard → Command Center (Options tab) → show decision tools (IV, Greeks, quick strategies) → Trade / Strategies → optionally Bots or Reports.

---

## Option B: One-command local run (Docker)

**For due diligence or when a live URL isn’t ready.** Stakeholders need Docker Desktop installed.

1. **Install:** [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Mac/Windows/Linux).

2. **Clone and run:**
   ```bash
   git clone https://github.com/massoudsh/Findash.git
   cd Findash
   docker compose -f docker-compose-core.yml up -d
   ```
   Wait 1–2 minutes for API, frontend, DB, and Redis to start.

3. **Open in browser:**
   - **App:** http://localhost:3000  
   - **API docs:** http://localhost:8011/docs  

4. **Stop when done:**
   ```bash
   docker compose -f docker-compose-core.yml down
   ```

**Note:** The frontend is built with `NEXT_PUBLIC_API_URL=http://localhost:8000` in the Dockerfile

*[truncated — see source for full prompt]*