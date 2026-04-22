# Event Log Encryption Design

> ## Why This Exists

For moor to be a viable Discord/Slack alternative, it needs persistent event logging with the same
features users expect:

- See e

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Event Log Encryption Design

## Why This Exists

For moor to be a viable Discord/Slack alternative, it needs persistent event logging with the same
features users expect:

- See events from the past
- See events that happened when you weren't at the console
- See events that happened while you were on another device/client

**The problem**: Without encryption, this creates a privacy nightmare where admins have unfettered
access to all user communications in plaintext. Discord and Slack likely have admin keys that
decrypt all content. We can do better.

**Design goal**: Provide meaningful protection against realistic threats (lazy sysadmin browsing
database files, stolen backups, improper disposal) without pretending to solve unsolvable problems
(compromised server, in-memory attacks).

**Key principle**: Having _some_ encryption is vastly better than having _zero_ encryption. Perfect
is the enemy of good enough.

## Overview

This document describes the end-to-end encryption architecture for MOO narrative event logs. The
system provides:

- **Encryption at rest** using age (modern file encryption with X25519/ChaCha20-Poly1305)
- **Per-user encryption** with user-chosen passwords (separate from MOO login)
- **Deterministic key derivation** enabling cross-device access (same password = same keys)
- **Client-side decryption** enabling E2E protection
- **Mandatory for history** - events cannot be logged to history without encryption setup

**What this offers**: End-to-end encryption of historical events - neither web-host nor daemon can
read plaintext events. Protects against filesystem access, stolen backups, and compromised server
components.

### Client Support

**Web client**: Full E2E encryption support via age.js in browser. Password-derived keys stored in
localStorage. This is the reference implementation.

**Telnet client**: Does not support retrieving encrypted history or providing encryption keys.
Telnet clients only see live, real-time events as they occur 

*[truncated — see source for full prompt]*