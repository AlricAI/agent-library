# User Profile Settings Component

> ## Component Name

UserProfileSettings

## Overview

A comprehensive settings interface allowing users to manage their profile information, privacy pr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UserProfileSettings Component Specification

## Component Name

UserProfileSettings

## Overview

A comprehensive settings interface allowing users to manage their profile information, privacy preferences, notification controls, and account configurations. Designed with transparency and user control as core principles to build trust while maintaining accessibility and mobile-first usability.

## Props/State

### Props

| Prop             | Type            | Required | Description                             |
| ---------------- | --------------- | -------- | --------------------------------------- |
| user             | UserProfileData | Yes      | Current user's profile data             |
| onSave           | function        | No       | Callback when user saves changes        |
| onCancel         | function        | No       | Callback when user cancels edits        |
| onDeleteAccount  | function        | No       | Callback to initiate account deletion   |
| onVerifyIdentity | function        | No       | Callback to start identity verification |

### State

| State             | Type    | Description                            |
| ----------------- | ------- | -------------------------------------- |
| editedProfile     | object  | Local copy of profile being edited     |
| activeSection     | string  | Currently visible settings section     |
| isSaving          | boolean | Whether save operation is in progress  |
| saveSuccess       | boolean | Whether last save was successful       |
| saveError         | string  | Error message if save failed           |
| showDeleteConfirm | boolean | Whether delete confirmation is visible |
| showVerifyModal   | boolean | Whether verification modal is visible  |

## Behavior Description

### Initial Load

1. Load current user profile data into editable state
2. Set default active section to "Profile Information"
3. Initialize save states to default values
4. Apply appropriate accessibility attributes

### Interaction Be

*[truncated — see source for full prompt]*