# LAUNCH V2.0 Yield Score

> > Launch target: 2026-04-30 (~2 weeks from spec, dev complete 2026-04-17).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Pulse v2.0 — Yield Score Launch Pack

> Launch target: 2026-04-30 (~2 weeks from spec, dev complete 2026-04-17).
> Killer feature: cost-to-code yield (`$0.42 / commit` per provider).

---

## 1. Pre-launch checklist

### Code

- [x] Stages 0–7 shipped and pushed to main
- [x] Migration `migrate_v0.14_yield_score.sql` applied to prod
- [x] Migration `migrate_v0.15_track_git_activity.sql` applied to prod
- [x] CLI Pulse Bar builds clean on macOS 13
- [x] Swift tests: 13 yield + 186 existing = 199 passing
- [x] Python tests: 18 yield + existing suite passing
- [ ] Bump app marketing version to 2.0 (Info.plist, project.pbxproj)
- [ ] Bump helper version constant to 2.0
- [ ] Smoke test on a fresh user account with no prior data
- [ ] Smoke test on Jason's primary account (real data, expect Yield Card to populate within 1 sync cycle of enabling toggle)

### Distribution

- [ ] Archive + upload macOS build via Xcode → ASC
- [ ] Archive + upload iOS build via Xcode → ASC
- [ ] Update `appstore/description.txt` with Yield Score paragraph
- [ ] Update `appstore/whats-new-v2.0.txt` (template below)
- [ ] Capture 1 Yield Card screenshot at iPhone 6.7" + Mac 1280×800

### Comms

- [ ] Final blog post (draft below)
- [ ] Tweet thread (draft below)
- [ ] Demo video (script below)
- [ ] DM 5 power users 24h before public launch
- [ ] Schedule HN Show post for the morning of launch (Tuesday or Wednesday best)

---

## 2. App Store "What's New" copy

> CLI Pulse 2.0 introduces **Yield Score** — your AI spend per git commit.
>
> See exactly which AI tool is producing code worth its subscription. Cursor at $1.67 / commit vs Codex at $0.32 / commit? Now you'll know.
>
> Everything stays on-device until you opt in. Only hashed metadata leaves your Mac — never your code, messages, or diffs.
>
> Pro feature. Enable in Settings → Privacy → Track git activity.

---

## 3. Blog post draft

**Title:** I built a tool to find out if Cursor is worth $20/month. Then I open-sourced the math.

*[truncated — see source for full prompt]*