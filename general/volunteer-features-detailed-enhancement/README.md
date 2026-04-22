# Volunteer Features Detailed Enhancement

> ## Overview

This document provides comprehensive design specifications that enhance the existing volunteer features of the YouAndINotAI platform. The

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Detailed Volunteer Features Enhancement Specification

## Overview

This document provides comprehensive design specifications that enhance the existing volunteer features of the YouAndINotAI platform. These enhancements focus on deepening user engagement through personalized discovery, rich impact visualization, and community-driven volunteering while maintaining strict adherence to platform values and legal compliance.

## Enhanced Component Specifications

### VolunteerOpportunityCard Component (Detailed)

#### Extended Props Specification

| Prop Name         | Type                         | Required    | Description                                   |
| ----------------- | ---------------------------- | ----------- | --------------------------------------------- | ----------- | ---- | --- | ---------------------------------- |
| opportunity       | EnhancedVolunteerOpportunity | Yes         | Complete opportunity data with impact metrics |
| onSignup          | Function                     | Yes         | Handler for expressing interest               |
| onViewDetails     | Function                     | Yes         | Handler for detailed view                     |
| onShare           | Function                     | No          | Handler for social sharing                    |
| currentUserStatus | 'registered'                 | 'confirmed' | 'attended'                                    | 'completed' | null | No  | Current user's participation stage |
| showImpactBadge   | Boolean                      | No          | Display children's impact projection          |
| accessibilityMode | Boolean                      | No          | Enhanced accessibility features enabled       |

#### EnhancedVolunteerOpportunity Structure

```typescript
interface EnhancedVolunteerOpportunity {
  id: string;
  title: string;
  organization: {
    name: string;
    verified: boolean;
    rating: number; // 1-5 stars
  };
  category: {
    primary: 'kids' | 'elderly' | 'environ

*[truncated — see source for full prompt]*