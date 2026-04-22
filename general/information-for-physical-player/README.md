# Information For Physical Player

> This document describes how physical player devices (like p3a) should interact with the Makapix Club API and MQTT broker.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Makapix Club - Physical Player Integration Guide

This document describes how physical player devices (like p3a) should interact with the Makapix Club API and MQTT broker.

## Overview

Physical players are devices that display pixel art from Makapix Club. They:
1. **Provision** themselves with the API to get a registration code
2. Display the registration code on their screen for the owner to enter on the website
3. **Connect to MQTT** to receive commands and report status
4. Execute commands (swap artwork, show specific artwork)
5. Report their status periodically

---

## 1. Player Provisioning (Registration Flow)

### Step 1: Device Calls Provision Endpoint

When the player boots up for the first time (or needs re-registration), it should call:

```
POST https://makapix.club/api/player/provision
Content-Type: application/json

{
  "device_model": "p3a",
  "firmware_version": "1.0.0"
}
```

Both fields are optional but recommended for tracking.

### Step 2: API Returns Registration Details

**Response (201 Created):**

```json
{
  "player_key": "550e8400-e29b-41d4-a716-446655440000",
  "registration_code": "A3F8X2",
  "registration_code_expires_at": "2025-01-29T12:15:00Z",
  "mqtt_broker": {
    "host": "makapix.club",
    "port": 8883
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `player_key` | UUID | Unique identifier for this player. **Store this permanently.** Used as MQTT username. |
| `registration_code` | String (6 chars) | Display this to the user. Uppercase alphanumeric, excludes ambiguous chars (0, O, I, 1, L). |
| `registration_code_expires_at` | ISO 8601 datetime | Code expires in **15 minutes**. |
| `mqtt_broker.host` | String | MQTT broker hostname. |
| `mqtt_broker.port` | Integer | MQTT broker port (TLS). |

### Step 3: Display Registration Code

The player should display the 6-character `registration_code` prominently on its screen so the owner can enter it on the Makapix Club website.

**Example display:**
```
┌───

*[truncated — see source for full prompt]*