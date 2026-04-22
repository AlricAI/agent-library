# Community Impact Tracker Component

> ## Component Name

CommunityImpactTracker

## Overview

A visualization component that transparently displays the community's collective impact on chi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CommunityImpactTracker Component Specification

## Component Name

CommunityImpactTracker

## Overview

A visualization component that transparently displays the community's collective impact on children's causes through the platform's contractual revenue disbursement model. This component reinforces trust by showing real outcomes from user interactions.

## Props/State

### Props

| Prop           | Type                                                        | Required | Description                              |
| -------------- | ----------------------------------------------------------- | -------- | ---------------------------------------- |
| impactData     | CommunityImpactData                                         | Yes      | Current impact metrics                   |
| period         | 'daily' \| 'weekly' \| 'monthly' \| 'quarterly' \| 'yearly' | No       | Time period display (default: 'monthly') |
| showProjection | boolean                                                     | No       | Show impact projections (default: true)  |
| compactView    | boolean                                                     | No       | Condensed display mode (default: false)  |
| onDetailView   | Function                                                    | No       | Handler for detailed impact view         |

### CommunityImpactData Interface

```typescript
interface CommunityImpactData {
  timeframe: {
    start: string; // ISO date
    end: string; // ISO date
  };
  financialImpact: {
    totalRevenue: number; // Platform revenue
    childrenSupportDisbursement: number; // Contractual revenue disbursement
    disbursementPercentage: number; // Percentage of revenue
    dollarPerUserHour: number; // Average impact per user hour
  };
  communityEngagement: {
    totalUsers: number;
    activeUsers: number;
    volunteerHours: number;
    communityEvents: number;
    newConnections: number;
  };
  childrenBenefited: {
    directBeneficiaries: number;
    education

*[truncated — see source for full prompt]*