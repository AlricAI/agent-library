# CODE SIGNING

> This document explains how code signing and notarization are configured for the Local Operator UI application.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Signing and Notarization Guide

This document explains how code signing and notarization are configured for the Local Operator UI application.

## Overview

Code signing is essential for distributing desktop applications as it:

- Verifies the authenticity of the application
- Prevents tampering with the application
- Improves user trust
- Is required by modern operating systems (especially macOS and Windows)

## Configuration

### Environment Variables

The following environment variables are used for code signing:

#### For All Platforms

- `CSC_CONTENT`: Base64-encoded signing certificate (p12 file)
- `CSC_KEY_PASSWORD`: Password for the signing certificate

#### For macOS Specific

- `APPLE_ID`: Your Apple Developer ID
- `APPLE_ID_PASSWORD`: App-specific password for your Apple ID
- `APPLE_TEAM_ID`: Your Apple Developer Team ID
- `NOTARIZE`: Set to "true" to enable notarization (optional)

### How It Works

1. **Certificate Preparation**:
   - The CI/CD pipeline decodes the base64-encoded certificate (`CSC_CONTENT`) into a p12 file
   - The path to this file is set as `CSC_LINK` for electron-builder

2. **Build Process**:
   - The application is built using `pnpm dist:mac`, `pnpm dist:win`, or `pnpm dist:linux`
   - electron-builder automatically signs the application using the provided certificate

3. **Notarization (macOS only)**:
   - After signing, the `scripts/notarize.js` script is executed (configured in package.json)
   - This script submits the app to Apple for notarization using `notarytool` (via `@electron/notarize`)
   - The notarization process requires `APPLE_ID`, `APPLE_ID_PASSWORD`, and `APPLE_TEAM_ID`

## Setting Up for Local Development

1. **Create a `.env.build` file** in the project root with the following variables:

   ```
   # GitHub Token (for publishing releases)
   GH_TOKEN=your_github_token

   # macOS Code Signing
   APPLE_ID=your_apple_id@example.com
   APPLE_ID_PASSWORD=your_app_specific_password
   APPLE_TEAM_ID=your_team_i

*[truncated — see source for full prompt]*