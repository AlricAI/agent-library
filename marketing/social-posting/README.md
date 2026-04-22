# Social Posting

> ## 🎯 Overview

📋 Posts to Twitter, Bluesky, and Mastodon with platform-specific APIs and embed generation.
🧠 Implements five progressive text-fitti

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📣 Social Posting — Three-Platform Social Media Pipeline

## 🎯 Overview

📋 Posts to Twitter, Bluesky, and Mastodon with platform-specific APIs and embed generation.
🧠 Implements five progressive text-fitting strategies to respect each platform's character limits.
🔗 Extracts OpenGraph metadata for rich link card embeds on Bluesky.
📝 Builds markdown embed sections for each platform to persist in Obsidian notes.

## 🔍 Content Discovery

📋 Content discovery uses a two-phase strategy to find notes that need social media posting.

### 🎯 Phase 1: Prior Day Reflection Priority

⏰ When the current time is past the posting hour (default 17:00 UTC / 9 AM PST), the system checks for yesterday's reflection.
✅ The prior day's reflection is posted if it has a creative title (not just the date) and has not yet been posted to all configured platforms.
🚫 If the reflection has an untitled (date-only) title, it is skipped.

### 🌐 Phase 2: BFS Content Discovery

🔍 When no prior day reflection is available (or it has already been posted), the system uses breadth-first search starting from the most recent reflection.
📊 BFS follows markdown links and Obsidian wiki links to discover linked content notes.
⏳ Reflections from date D are NOT eligible for posting until the posting hour on D+1. Non-reflection content is always eligible.
🚫 Index pages are never eligible for posting but are still traversed to discover linked content.
📋 At most one note is discovered per configured platform per run.
🔗 BFS always follows links from ALL visited nodes, including ineligible or non-postable content. 📄 This ensures that content reachable only through index pages, private notes, or stubs is still discoverable.

### 📏 Content Filters

🛡️ A note is postable only if it meets all of these criteria:
- 📄 Not an index page (filename is not `index.md`)
- 📂 Not in the changes directory (path does not start with `changes/`)
- 🏷️ Not flagged with `no_social: true` in frontmatter
- 📝 Not an unt

*[truncated — see source for full prompt]*