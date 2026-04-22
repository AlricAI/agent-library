# Tweet Automation Notes

> ## Planning Process

### 1. Understanding the Existing System

**Repository Analysis:**
- This is a Quartz 4.5.0 digital garden publishing system
- Co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tweet Automation: Planning & Implementation Notes

## Planning Process

### 1. Understanding the Existing System

**Repository Analysis:**
- This is a Quartz 4.5.0 digital garden publishing system
- Content lives in `content/` directory as Obsidian-compatible markdown files
- Reflections are daily blog posts at `content/reflections/YYYY-MM-DD.md`
- The site is built with TypeScript/esbuild and deployed via GitHub Pages
- Existing CI/CD: push to `main` → build Quartz → deploy to GitHub Pages

**Key Insight:** The Enveloppe plugin performs **one-way sync** from the user's Obsidian
vault to this GitHub repository. Any changes committed directly to the repo would be
overwritten on the next Enveloppe publish. Therefore, to persist changes to a note, we must
write to the **Obsidian vault**, not to the git repository.

**Read vs Write paths:**
- **Reading**: We read the reflection from the checked-out repo (it's the published copy)
- **Writing**: We write the tweet embed to the Obsidian vault via Headless Sync
- The user reviews the change in Obsidian and publishes it to GitHub via Enveloppe

### 2. Analyzing Existing Tweet Embeds

**Pattern Discovery:**
- 80+ reflection files already contain embedded tweets
- Section header: `## 🐦 Tweet` (singular, at end of file)
- Embed format: Standard Twitter blockquote with `data-theme="dark"`
- Always includes the Twitter widgets.js script tag
- Tweet content follows a consistent pattern: title + emoji tags + URL

**Example from 2026-02-05.md:**
```html
## 🐦 Tweet
<blockquote class="twitter-tweet" data-theme="dark"><p lang="en" dir="ltr">
2026-02-05 | 👥 Many ⚔️ Will 🧠 Know 🌪️ Chaos 📚📺

📚 Book Series | 🌌 Sci-Fi Exploration | ⛈️ Leadership in Turmoil
https://t.co/mXLn8dlc56</p>&mdash; Bryan Grounds (@bagrounds)
<a href="https://twitter.com/bagrounds/status/...">February 7, 2026</a>
</blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
```

### 3. API Selection Decisions

#### Tw

*[truncated — see source for full prompt]*