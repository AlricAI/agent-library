# Workflows

> This document describes the key workflows in the YouAndINotAI platform and their implementation details.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Core Business Workflows

This document describes the key workflows in the YouAndINotAI platform and their implementation details.

## Table of Contents

- [User Registration and Authentication](#user-registration-and-authentication)
- [Profile Creation and Verification](#profile-creation-and-verification)
- [Discovery and Matching](#discovery-and-matching)
- [Communication](#communication)
- [Safety Features](#safety-features)
- [Payment Processing](#payment-processing)
- [Event and Volunteering Coordination](#event-and-volunteering-coordination)
- [Charitable Revenue Distribution](#charitable-revenue-distribution)

## User Registration and Authentication

### Registration Flow

1. User visits registration page
2. User provides email, password, and display name
3. System validates input:
   - Email format validation
   - Password strength requirements
   - Unique email check
4. System creates user account with hashed password
5. System sends verification email
6. User clicks verification link
7. System activates account
8. User is redirected to login page

### Login Flow

1. User enters email and password
2. System validates credentials:
   - Email exists in database
   - Password matches hash
3. System generates JWT token
4. Token is returned to client
5. Client stores token for authenticated requests

### Password Reset Flow

1. User requests password reset with email
2. System verifies email exists
3. System generates reset token
4. System sends reset email with token
5. User clicks reset link
6. User enters new password
7. System validates and updates password
8. User redirected to login

## Profile Creation and Verification

### Profile Setup

1. User completes basic profile information
2. User adds profile picture
3. User answers verification questions
4. User selects interests and preferences

### Identity Verification

1. User initiates verification process
2. System presents verification challenges:
   - SMS verification
   - Email confirmation
   - Payme

*[truncated — see source for full prompt]*