# Safety Features Handoff

> ## Overview

This document provides detailed implementation guidance for the safety features designed for YouAndINotAI. It includes component specific

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Safety Features Implementation Handoff

## Overview

This document provides detailed implementation guidance for the safety features designed for YouAndINotAI. It includes component specifications, interaction patterns, and technical considerations necessary for accurate implementation.

## SafetyDrawer Component

### Component Structure

```jsx
<SafetyDrawer
  open={boolean}
  targetUserId={string}
  targetName={string}
  source={string}
  onClose={function}
  onActionComplete={function}
/>
```

### Props Details

- `open`: Controls visibility of the drawer (Boolean)
- `targetUserId`: ID of user being reported/restricted (String)
- `targetName`: Display name of target user (String)
- `source`: Context where drawer was opened (String)
- `onClose`: Callback when drawer closes (Function)
- `onActionComplete`: Callback when safety action completes (Function)

### Visual Implementation

1. **Drawer Header**
   - Title: "Safety Tools"
   - Close button position: Top right corner
   - Background: `--bg-primary`
   - Text color: `--text-primary`
   - Border bottom: `--border-width-thin` solid `--text-secondary`

2. **Report Concern Section**
   - Section heading: "Report Concern"
   - Report option with icon: "⚠️ Harrassment or Threats"
   - Subtext: "High priority review"
   - Text area placeholder: "Describe what happened"
   - Submit button: "Submit Report"

3. **Immediate Actions Section**
   - Section heading: "Immediate Actions"
   - Block User card with:
     - Icon: "🛡️ Block User"
     - Description: "Stops all contact"
     - Button: "Block Immediately"
   - Mute User card with:
     - Icon: "🔕 Mute User"
     - Description: "Hide messages temporarily"
     - Button: "Mute for 24 Hours"
   - Restrict Visibility card with:
     - Icon: "👁️ Restrict Visibility"
     - Description: "Limit profile access"
     - Button: "Restrict Now"
   - Freeze Conversation card with:
     - Icon: "💬 Freeze Conversation"
     - Description: "Pause messaging"
     - Button: "F

*[truncated — see source for full prompt]*