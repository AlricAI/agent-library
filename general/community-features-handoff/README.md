# Community Features Handoff

> ## Overview

This document provides detailed implementation guidance for the community engagement and volunteering features designed for YouAndINotAI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Community & Volunteering Features Implementation Handoff

## Overview

This document provides detailed implementation guidance for the community engagement and volunteering features designed for YouAndINotAI. It includes component specifications, interaction patterns, and technical considerations necessary for accurate implementation.

## VolunteerOpportunityCard Component

### Component Structure

```jsx
<VolunteerOpportunityCard
  opportunity={object}
  onSignup={function}
  onDetail={function}
  friendsAttending={array}
/>
```

### Props Details

- `opportunity`: VolunteerData object with opportunity details (Object)
- `onSignup`: Callback when signup button clicked (Function)
- `onDetail`: Callback when detail view requested (Function)
- `friendsAttending`: Array of User objects attending (Array)

### Visual Implementation

1. **Card Container**
   - Background: `--bg-primary`
   - Border: `--border-width-thin` solid `--text-secondary`
   - Border radius: `--border-radius-lg`
   - Padding: `--spacing-4`
   - Box shadow: `--shadow-sm` for elevation

2. **Header Section**
   - Icon based on cause category (e.g., school icon for education)
   - Title: Organization or program name
   - Cause category badge with color coding:
     - Children: `--volunteer-kids` (#FF6B9D)
     - Elderly Care: Amber to Orange (`--volunteer-elderly`)
     - Environment: Emerald to Green (`--volunteer-environment`)
     - Animals: Cyan to Teal (`--volunteer-animals`)
     - Food Bank: Yellow to Amber (`--volunteer-food`)
     - Education: Blue to Indigo (`--volunteer-education`)
     - Healthcare: Red to Pink (`--volunteer-healthcare`)
     - Disaster Relief: Orange to Red (`--volunteer-disaster`)
     - Community: Purple to Violet (`--volunteer-community`)
     - General: Gray to Slate (`--volunteer-general`)

3. **Body Content**
   - Description: Brief summary of opportunity
   - Time commitment: Duration and frequency information
   - Location: Address or general area with distance 

*[truncated — see source for full prompt]*