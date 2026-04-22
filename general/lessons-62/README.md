# LESSONS

> Append new entries at the top.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Lessons Learned — Map Rendering Expert

Append new entries at the top. See `vault/agents/skills/lessons-learned-loop.md` for format.

---

2026-04-09 — BM4 online path also forced to offline-style (the REAL final fix)

Bug: BM3 fixed the `isConnected=false` code path but left the `isConnected=true` path still returning remote URLs (openfreemap liberty, CARTO dark-matter). On Steve's real device with WiFi, NetworkMonitor.isConnected reported true but the remote style JSON endpoints were unreachable — same failure mode as BM1/BM2, just hidden behind a branch we didn't fix.
Fix: In MapStyleManager.swift, make MapStyle.outdoor.styleURL() ALWAYS return dirtsync-offline-style regardless of isConnected. Also force useNavDarkTheme branch and useFreeRiderDarkTheme branch to always use bundledDarkFallbackURL (already pointing at offline post-BM3). Every code path that could return a remote URL is now neutralized unless the user explicitly picks Satellite/Hybrid/GoogleSatellite/Standard.
Why: Trust in `NetworkMonitor.isConnected` as a signal for "can the app reach a specific remote endpoint" is a lie. isConnected just means "the phone has some kind of network interface up." It does NOT mean openfreemap.org, cartocdn.com, or any specific CDN is reachable. Captive portals, DNS failures, ATS blocks, slow first-load, regional CDN outages — any of these can cause a true-isConnected state to still fail a remote style fetch.
Architecture rule: for the default user experience, never depend on a remote URL that can fail silently. Use a bundled style for default. Offer remote-dependent styles as explicit opt-ins (Settings picker) for users who want them and accept the risk.
Test pattern: For every remote-dependent code path, write a test that exercises the online branch (no `--force-offline`) AND asserts visual correctness. BM3's offline test alone missed this because it only covered the disconnected path. BM4's testBM4_OnlineModeAlsoRendersTrailsFromOfflineStyle does the same pixel a

*[truncated — see source for full prompt]*