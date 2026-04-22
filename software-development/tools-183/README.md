# TOOLS

> ## Available Tools
- Bash (SSH to Mini, xcodebuild, xcrun simctl, gws, git, gh)
- Forge API (read issues, post comments, update status)
- File read/wr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Feature Builder

## Available Tools
- Bash (SSH to Mini, xcodebuild, xcrun simctl, gws, git, gh)
- Forge API (read issues, post comments, update status)
- File read/write/edit (via SSH to Mini for Swift code)

## The Factory (Mac Mini)

### Connection
```bash
ssh dirtsyncmini@100.125.184.57
```
- Tailscale IP, always available
- Xcode 26.4
- iPhone 17 simulator, iOS 26.4

### Simulator
```bash
SIM=1C53DE6B-2574-43FF-BF29-C1C5ACF5A526

# Boot simulator
xcrun simctl boot $SIM 2>/dev/null

# Shutdown simulator
xcrun simctl shutdown $SIM

# Reboot (if launch fails)
xcrun simctl shutdown $SIM && sleep 2 && xcrun simctl boot $SIM

# Install app
APP=$(find ~/Library/Developer/Xcode/DerivedData -name "DirtSync.app" \
  -path "*/Debug-iphonesimulator/*" -maxdepth 8 | head -1)
xcrun simctl install $SIM "$APP"

# Launch with test flags (bypasses auth, onboarding, location dialog)
xcrun simctl launch $SIM app.dirtsync.DirtSync --uitesting --uitesting-navigate

# Terminate app
xcrun simctl terminate $SIM app.dirtsync.DirtSync

# Screenshot
xcrun simctl io $SIM screenshot ~/screenshot.png

# Set GPS location (lat,lon)
xcrun simctl location $SIM set 37.7283,-81.6708
```

### --uitesting Bypasses (CRITICAL)
When launching with `--uitesting`, the app skips:
1. **Auth** — `AuthManager` sets fake `User.mock()`, no Supabase login
2. **Onboarding** — `RootView` sets `showOnboarding = false`
3. **Location dialog** — `LocationManager` skips `requestWhenInUseAuthorization()` and `startUpdatingLocation()`

These bypasses let the app reach the map without human interaction.

## Build Commands

### Clean build
```bash
cd /Users/dirtsyncmini/DirtSync/DirtSync
xcodebuild clean build -scheme DirtSync \
  -destination "platform=iOS Simulator,name=iPhone 17" \
  2>&1 | tail -20
```

### Run specific test suite
```bash
cd /Users/dirtsyncmini/DirtSync/DirtSync
xcodebuild test -scheme DirtSync \
  -destination "platform=iOS Simulator,name=iPhone 17" \
  -only-testing:DirtSyncUIT

*[truncated — see source for full prompt]*