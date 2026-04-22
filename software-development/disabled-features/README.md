# DISABLED FEATURES

> This document explains the automated features that have been disabled in the Discord bot system while preserving all code for future re-enabling.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Disabled Discord Bot Features

This document explains the automated features that have been disabled in the Discord bot system while preserving all code for future re-enabling.

## 🚫 Disabled Features

### 1. System Announcements

**What was disabled:**
- Automated system announcements about coach dynamics and irritation levels
- Posted to #general channel with coach relationship updates
- Triggered during episode scene progression

**Schedule that was disabled:**
- **After scenes 5, 11, 17, and 23** (every 6 scenes)
- Announcements included coach irritation data from `story-arcs.json`
- Format: "📢 The AF System Update" with coach dynamics

**Files modified:**
- `lib/discord/eventMessages.ts` - Lines 378-386: Commented out system announcement triggers
- `lib/discord/sceneFramework.ts` - Lines 1196-1209: Commented out system announcement calls

### 2. ForReal Announcements  

**What was disabled:**
- Automated announcements explaining the ForReal feature
- Posted to #forreal channel with usage instructions
- Triggered twice per episode cycle

**Schedule that was disabled:**
- **After scenes 1 and 12** (twice per 24-scene episode)  
- Content explained "for real though:" command usage
- Format: "FOR REAL THOUGH" with feature instructions

**Files modified:**
- `lib/discord/eventMessages.ts` - Lines 388-396: Commented out ForReal announcement triggers

### 3. Episode Scene Progression

**What still works:**
- Episode generation and scene playback continue normally
- Watercooler chats every 15 minutes
- Coach interactions and conversations
- All manual commands (!help, !forreal, etc.)

## ✅ Still Working

### Discord Bot Features that remain active:
- **Watercooler chats** - Automated every 15 minutes
- **Manual coach interactions** - All !commands work
- **ForReal conversations** - Feature works, just no auto-announcements
- **Episode generation** - Story progression continues
- **Coach personalities** - All AI responses functional
- **Administrative commands** - A

*[truncated — see source for full prompt]*