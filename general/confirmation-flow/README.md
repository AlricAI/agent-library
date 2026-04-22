# Confirmation Flow

> ## Overview

The confirmation flow is the core UX innovation — a biometric payment approval that works from the terminal without requiring a browser.


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Confirmation Flow

## Overview

The confirmation flow is the core UX innovation — a biometric payment approval that works from the terminal without requiring a browser.

## macOS Touch ID Integration

### Swift Helper Binary

A compiled Swift binary (`bin/touchid-confirm`) handles the biometric interaction:

```
agent-pay CLI (Node.js)
    │
    ├── execFile("bin/touchid-confirm", [
    │     "--service", "Linear",
    │     "--amount", "$8/mo",
    │     "--method", "Visa ****4242"
    │   ])
    │
    ▼
touchid-confirm (Swift)
    │
    ├── LAContext.evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics)
    │
    ├── macOS presents Touch ID dialog:
    │   ┌─────────────────────────────────────┐
    │   │  Touch ID                            │
    │   │                                     │
    │   │  Confirm $8/mo payment to Linear    │
    │   │  using Visa ****4242                │
    │   │                                     │
    │   │  [Cancel]          [Use Password]   │
    │   └─────────────────────────────────────┘
    │
    ├── User touches fingerprint sensor
    │
    ▼
    stdout → {"success": true, "service": "Linear", "amount": "$8/mo"}
```

### Fallback Chain

1. **Touch ID** — Primary (`.deviceOwnerAuthenticationWithBiometrics`)
2. **System password** — If Touch ID unavailable (`.deviceOwnerAuthentication`)
3. **Error** — If no auth method available, return error JSON

### Binary Interface

**Input:** Command-line arguments
```
touchid-confirm --service "Linear" --amount "$8/mo" --method "Visa ****4242"
```

**Output:** JSON to stdout
```json
// Success
{"success": true, "service": "Linear", "amount": "$8/mo"}

// Failure
{"success": false, "error": "User canceled authentication"}
```

**Exit codes:**
- `0` — Authentication completed (check `success` field for result)
- `1` — System error (no auth method available)

### Timeout

The Swift binary has no timeout — it waits for the user to complete or cancel the Touch ID prompt. The Node.js cal

*[truncated — see source for full prompt]*