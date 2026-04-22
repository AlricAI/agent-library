# HEARTBEAT

> Run this on every wake.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HEARTBEAT.md — DirtSync Test Runner

Run this on every wake. This is the factory floor procedure.

## 0. Read Your Lessons (MANDATORY — before Read Assignment)

1. Read `LESSONS.md` in this agent directory (`companies/dirtsync/agents/test-runner/LESSONS.md`). Create with header if missing.
2. Scan for entries tagged `xcuitest`, `simctl`, `mini`, `ssh`, or keywords relevant to the current branch/test class.
3. For `Outcome: worked` entries, try those approaches first. For `Outcome: didn't work`, skip them.

See `vault/agents/skills/lessons-learned-loop.md`.

## 1. Read Assignment
- Read the assigned issue and ALL comments
- Identify: branch name, test class to run, what to look for in screenshots
- If no branch specified, use the branch from the iOS Builder's comment

## 2. Sync the Factory

```bash
ssh dirtsyncmini@100.125.184.57 << 'REMOTE'
export PATH="/opt/homebrew/bin:/usr/local/bin:$PATH"
cd /Users/dirtsyncmini/DirtSync

# ALWAYS reset to remote — never git pull
git checkout -- .
git fetch origin
git reset --hard origin/<BRANCH_NAME>

# Apply Mini-specific Ferrostar patch
python3 -c "
with open('DirtSync/DirtSyncApp/Services/FerrostarNavigationService.swift', 'r') as f:
    c = f.read()
if 'drivingSide' not in c:
    c = c.replace('            incidents: []\n        )', '            incidents: [],\n            drivingSide: nil,\n            roundaboutExitNumber: nil\n        )')
    with open('DirtSync/DirtSyncApp/Services/FerrostarNavigationService.swift', 'w') as f:
        f.write(c)
    print('Ferrostar patched')
"
REMOTE
```

## 3. Build

```bash
ssh dirtsyncmini@100.125.184.57 << 'REMOTE'
cd /Users/dirtsyncmini/DirtSync/DirtSync
xcodebuild clean build -scheme DirtSync \
  -destination "platform=iOS Simulator,name=iPhone 17" \
  2>&1 | grep -E "SUCCEEDED|FAILED|error:"
REMOTE
```

**If BUILD FAILED:** Post the error to the issue, mark `blocked`, stop.

## 4. Run Tests

```bash
ssh dirtsyncmini@100.125.184.57 << 'REMOTE'
cd /Users/dirtsyncmini/DirtSync/Di

*[truncated — see source for full prompt]*