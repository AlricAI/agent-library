# Privacy Features Handoff

> ## Overview

This document provides detailed implementation guidance for the privacy center and data control features designed for YouAndINotAI. It in

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Privacy Features Implementation Handoff

## Overview

This document provides detailed implementation guidance for the privacy center and data control features designed for YouAndINotAI. It includes component specifications, interaction patterns, and technical considerations necessary for accurate implementation while maintaining compliance with privacy regulations.

## PrivacyDashboard Component

### Component Structure

```jsx
<PrivacyDashboard
  userData={object}
  onRequestExport={function}
  onDeleteAccount={function}
  onUpdateSetting={function}
/>
```

### Props Details

- `userData`: PrivacyData object with user's current settings (Object)
- `onRequestExport`: Callback when data export requested (Function)
- `onDeleteAccount`: Callback when account deletion initiated (Function)
- `onUpdateSetting`: Callback when privacy setting changed (Function)

### Visual Implementation

1. **Dashboard Header**
   - Title: "Privacy Center" with help icon
   - Help button linking to detailed privacy documentation
   - Last updated timestamp for settings
   - Quick actions menu (export, delete account)

2. **Data Snapshot Overview**
   - Completion meter showing profile/data completeness
   - Visual: Circular progress chart with percentage
   - Color coding:
     - 0-30%: `--color-error` (red)
     - 31-70%: `--color-warning` (orange)
     - 71-100%: `--color-success` (green)
   - Summary text: "{percentage}% Complete"

3. **Privacy Status Indicators**
   - Profile visibility status with eye icon
   - Data sharing status with share icon
   - Location tracking status with location icon
   - Communication preferences status with message icon
   - Account security status with lock icon

4. **Quick Actions Section**
   - Export My Data button with download icon
   - Delete Account button with trash icon
   - Review Privacy Policy link
   - Third-Party Sharing disclosure link
   - Data Portability options

### Interaction Requirements

- **Real-Time Updates**:
  - Settings chan

*[truncated — see source for full prompt]*