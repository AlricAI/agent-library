# TOOLS

> All commands run on Mac Mini via SSH unless noted.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DirtSync Rider QA Engineer — TOOLS

All commands run on Mac Mini via SSH unless noted. Copy-paste ready.

---

## Mac Mini Access

```bash
ssh dirtsyncmini@100.125.184.57
```

Repo root: `/Users/dirtsyncmini/DirtSync/DirtSync`
GPX tracks: `/Users/dirtsyncmini/DirtSync/DirtSync/DirtSyncUITests/GPXRoutes/`
gws CLI: `/opt/homebrew/bin/gws`

---

## Simulator Management

### Detect booted simulator UUID (ALWAYS use this, never hardcode)
```bash
xcrun simctl list devices booted --json | python3 -c "
import json, sys
data = json.load(sys.stdin)
for runtime, devices in data['devices'].items():
    for d in devices:
        if d['state'] == 'Booted' and 'iPhone 17' in d['name']:
            print(d['udid'])
"
```

### Boot simulator if not booted
```bash
xcrun simctl boot "iPhone 17"
open -a Simulator
```

### Shutdown simulator
```bash
xcrun simctl shutdown $SIM_UUID
```

---

## Git Sync on Mini (CRITICAL — never use git pull)

```bash
cd /Users/dirtsyncmini/DirtSync/DirtSync
git fetch origin
git reset --hard origin/<branch-name>
```

Confirm SHA:
```bash
git rev-parse --short HEAD
```

---

## Ferrostar Patch (MANDATORY after every sync)

```bash
python3 - <<'EOF'
with open("DirtSyncApp/Services/FerrostarNavigationService.swift", "r") as f:
    c = f.read()
c = c.replace(
    '            incidents: []\n        )',
    '            incidents: [],\n            drivingSide: nil,\n            roundaboutExitNumber: nil\n        )'
)
with open("DirtSyncApp/Services/FerrostarNavigationService.swift", "w") as f:
    f.write(c)
print("Ferrostar patch applied")
EOF
```

Verify:
```bash
grep -c "drivingSide" DirtSyncApp/Services/FerrostarNavigationService.swift
# Must be >= 1 or DO NOT PROCEED
```

---

## Build

```bash
xcodebuild clean build \
  -scheme DirtSync \
  -destination "platform=iOS Simulator,name=iPhone 17" \
  2>&1 | tail -30
```

---

## GPX Location Injection

### List available tracks
```bash
ls /Users/dirtsyncmini/DirtSync/DirtSync/DirtSyncUITests/GPXRoutes/*.g

*[truncated — see source for full prompt]*