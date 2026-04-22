# SOCIAL INTEGRATION

> How our arcade games integrate the social library for handles, leaderboards, sharing, groups, XP, and streaks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pixelpit Social Integration Guide

How our arcade games integrate the social library for handles, leaderboards, sharing, groups, XP, and streaks.

## Library Location

- **Documentation**: `pixelpit/SOCIAL.md`
- **React Components**: `web/app/pixelpit/components/`
- **Vanilla JS**: `/pixelpit/social.js`

## Available Exports

```tsx
import {
  // Components
  ScoreFlow,
  Leaderboard,
  ShareButtonContainer,
  ShareModal,
  CreateGroupForm,
  GroupTabs,
  StreakBoard,
  CodeInput,
  SettingsPanel,

  // Hooks
  usePixelpitSocial, getGuestName, saveGuestName,
  useScoreSubmit,
  useLeaderboard,
  useProfile,
  useGroups,

  // Types
  type PixelpitUser,
  type LeaderboardEntry,
  type ScoreFlowColors,
  type LeaderboardColors,
  type ProgressionResult,
  type Group,
  type GroupType,
  type GroupsResult,
  type CreateGroupResult,
  type JoinGroupResult,

  // OG Image utilities
  createScoreShareImage,
  BeamDecorations, CatchDecorations, CatTowerDecorations,
  CaveMothDecorations, EmojiDecorations, FlappyDecorations,
  FlipDecorations, RainDecorations, SingularityDecorations,
  SproutRunDecorations, TapBeatsDecorations,
  OG_SIZE,
  CornerAccents, PixelpitBranding, GAME_COLORS,
} from '@/app/pixelpit/components';
```

---

## Feature Comparison

| Feature | SUPERBEAM | BAT DASH | TAPPER | EMOJI BLASTER | CAT TOWER | BEAM |
|---------|-----------|----------|--------|---------------|-----------|------|
| **GAME_ID** | `'superbeam'` | `'batdash'` | `'tapper'` | `'emoji'` | `'cat-tower'` | `'beam'` |
| **Location** | `arcade/superbeam/` | `arcade/batdash/` | `arcade/tapper/` | `arcade/emoji/` | `arcade/cattower/` | `arcade/beam/` |
| **Groups** | Yes | Yes | Yes | No | No | No |
| **ShareModal** | Yes | Yes | Yes | No | No | No |
| **Group Leaderboard** | Yes | Yes | Yes | No | No | No |
| **Group Code URL** | `?pg=CODE` | `?pg=CODE` | `?pg=CODE` | No | No | No |
| **Logout URL** | `?logout` | `?logout` | `?logout` | No | No | No |
| **XP System** | Yes | Yes | Yes | 

*[truncated — see source for full prompt]*