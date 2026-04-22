# Google Play Billing Setup

> Complete step-by-step guide to get in-app subscriptions working on a real Android device.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Google Play Billing Setup Guide

Complete step-by-step guide to get in-app subscriptions working on a real Android device.

> **Why are prices showing "N/A"?** The billing client connects but product queries return empty results if the subscription products don't exist in Google Play Console, or the app was sideloaded instead of installed through Google Play.

## Prerequisites

- Google Play Developer Account ($25 one-time fee at https://play.google.com/console)
- A signed release AAB/APK of the app
- A real Android device with a Google account

## Overview

The billing flow requires this chain to work:

```
Google Play Console (products configured)
        ↓
App uploaded to a testing track
        ↓
App installed via Google Play (not sideloaded)
        ↓
BillingClient connects → queries products → shows prices
```

If any link is missing, prices will show "N/A".

---

## Step 1: Create the App in Google Play Console

If you haven't already created the app in Google Play Console, follow `docs/google-play-setup.md` first. You need:

- App created in Play Console
- Basic store listing filled in (name, description, screenshots)
- Privacy policy URL set

---

## Step 2: Upload a Signed Release Build

The app must be uploaded to at least the **Internal Testing** track before you can create subscription products.

### Build the release AAB

```powershell
# From the project root on Windows
dotnet publish src/PuzzleDazzle/PuzzleDazzle.csproj -f net9.0-android -c Release
```

The signed AAB will be in:
```
src/PuzzleDazzle/bin/Release/net9.0-android/publish/
```

### Upload to Internal Testing

1. In Google Play Console, go to **Testing > Internal testing**
2. Click **Create new release**
3. Upload your signed AAB file
4. Add release notes (e.g., "Initial billing test")
5. Click **Save** then **Review release** then **Start rollout**

> **Important:** The app's package name in the uploaded AAB must match your `AndroidManifest.xml`. The signing key must be consistent acros

*[truncated — see source for full prompt]*