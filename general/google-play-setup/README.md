# Google Play Setup

> Step-by-step guide for setting up your app in Google Play Console.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Google Play Console Setup Guide

Step-by-step guide for setting up your app in Google Play Console.

## Prerequisites

- ✅ Google Play Developer Account (verified)
- ✅ Signed AAB file: `app.mazeledazzle-Signed.aab`
- ✅ App descriptions and store listing text
- ✅ Privacy policy document
- ⏳ Screenshots (2-8 images)
- ⏳ Feature graphic (1024x500px)
- ⏳ Support email address

---

## Step 1: Access Google Play Console

1. Go to https://play.google.com/console
2. Sign in with your verified Google account
3. Accept the Developer Distribution Agreement if prompted

---

## Step 2: Create New App

1. Click **"Create app"** button
2. Fill in the details:

### App Details
- **App name**: Mazele Dazzle
- **Default language**: English (United States)
- **App or game**: App
- **Free or paid**: Free
- **Declarations**:
  - ✅ Check: Developer Program Policies
  - ✅ Check: US export laws

3. Click **"Create app"**

---

## Step 3: Complete Dashboard Tasks

Google Play Console uses a task-based system. Complete each required task:

### 3.1 Set Up Your App

#### Store Settings → Main Store Listing

**App details:**
- **App name**: Mazele Dazzle - Maze Generator
- **Short description** (80 chars max):
  ```
  Create and share custom mazes. Perfect for puzzles, education, and fun!
  ```
- **Full description** (4000 chars max):
  ```
  [Copy from docs/store-listing.md - Full Description section]
  ```

**Graphics:**
- **App icon**: 512 x 512 px (upload from app or recreate)
  - Use: `src/PuzzleDazzle/Resources/AppIcon/appicon.svg` (export as PNG at 512x512)
  
- **Feature graphic**: 1024 x 500 px **(REQUIRED)**
  - Create using Canva, Figma, or design tool
  - Include: App name, tagline, maze visual
  
- **Phone screenshots**: 2-8 images **(REQUIRED)**
  - Take screenshots on your phone
  - Show: Generation screen, Settings, maze examples
  - Dimensions: Minimum 320px, maximum 3840px
  
- **Tablet screenshots**: Optional (can add later)

**Categorization:**
- **App category**: Puzzle

*[truncated — see source for full prompt]*