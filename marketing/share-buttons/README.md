# Share Buttons

> ## 📋 Overview

🔗 Share buttons allow readers to easily share website pages on social media platforms, via text message, email, or by copying the lin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔗 Share Buttons — Social Media Sharing for Website Pages

## 📋 Overview

🔗 Share buttons allow readers to easily share website pages on social media platforms, via text message, email, or by copying the link.

## 🎯 Goals

- 🚀 Make it effortless for readers to share content they enjoy
- 🔒 Respect reader privacy: no third-party tracking scripts or SDKs
- ⚡ Stay lightweight: use intent URLs and native URI schemes
- 🎨 Maintain visual consistency with the Solarized theme
- 🧩 Follow the existing Quartz component architecture
- 📱 Work well on both desktop and mobile devices

## 🏗️ Architecture

### 🧱 Component Structure

- 📦 `quartz/components/ShareButtons.tsx` — the Quartz component rendering share button markup
- 🎨 `quartz/components/styles/shareButtons.scss` — styles for the share button layout
- ⚙️ `quartz/components/scripts/shareButtons.inline.ts` — client-side JavaScript for Copy Link clipboard handling, Native Share feature detection, and SPA navigation

### 🔧 Intent URL Patterns

| 🌐 Platform | 🔗 URL Pattern | 📝 Notes |
|---|---|---|
| 🦋 Bluesky | `https://bsky.app/intent/compose?text={text}` | URL included in text body |
| 🐘 Mastodon | `https://mastodon.social/share?text={text}` | Hardcoded to mastodon.social |
| 🐦 Twitter/X | `https://twitter.com/intent/tweet?text={text}` | Same combined text as other platforms |
| 💬 SMS | `sms:?&body={text}` | Native URI scheme; opens messaging app |
| 📧 Email | `mailto:?subject={title}&body={text}` | Opens default mail client |
| 🔗 Copy Link | JavaScript clipboard API | Copies page URL with visual feedback |
| 📲 Native Share | Web Share API | Progressive enhancement; shown only when supported |
| 📘 Facebook | `https://www.facebook.com/sharer/sharer.php?u={url}` | URL-only sharing |
| 💼 LinkedIn | `https://www.linkedin.com/sharing/share-offsite/?url={url}` | URL-only sharing |
| 🟠 Reddit | `https://www.reddit.com/submit?url={url}&title={title}` | URL and title as separate parameters |
| 📱 WhatsApp |

*[truncated — see source for full prompt]*