# BUILD INSTRUCTIONS

> ## Prerequisites

- Node.js 18+ and npm
- Expo CLI: `npm install -g expo-cli eas-cli`
- Android SDK (for local builds) or use EAS (cloud builds)
- Jav

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Flovey MVP - Build Instructions

## Prerequisites

- Node.js 18+ and npm
- Expo CLI: `npm install -g expo-cli eas-cli`
- Android SDK (for local builds) or use EAS (cloud builds)
- Java 17+ (for local Gradle builds)

## Option 1: Build APK/AAB via EAS (Recommended)

### Setup

```bash
cd flovey
npm install --legacy-peer-deps
eas login  # Login with your Expo account
eas init   # Initialize EAS project
```

### Build Preview APK

```bash
eas build --platform android --profile=preview
```

This creates a debug APK for testing.

### Build Production AAB

```bash
eas build --platform android --profile=production
```

This creates an Android App Bundle for Google Play Store submission.

**Output:** Builds are downloaded automatically or available in your EAS dashboard.

---

## Option 2: Local Build (Requires Java 17 + Android SDK)

### Setup

```bash
cd flovey
npm install --legacy-peer-deps
npx expo prebuild --platform android --clean
```

### Build APK

```bash
cd android
./gradlew assembleRelease
```

**Output:** `android/app/build/outputs/apk/release/app-release.apk`

### Build AAB

```bash
cd android
./gradlew bundleRelease
```

**Output:** `android/app/build/outputs/bundle/release/app-release.aab`

---

## Option 3: Expo Managed Development Build

### Build Development Client

```bash
eas build --platform android --profile=preview --dev-client
```

Then run:

```bash
eas build:run --platform android
```

This creates a customizable development app for testing with live reload.

---

## Testing the APK

### Installation

```bash
adb install path/to/app-release.apk
```

Or drag and drop into Android emulator.

### Running

App appears as "Flovey" in your app drawer. Launch and verify:
- ✅ Splashscreen shows "🌱 Flovey"
- ✅ Home screen renders "Parent-Child Money Learning App MVP"
- ✅ App is responsive

---

## Production Release Checklist

Before submitting to Google Play:

- [ ] Bump version in `app.json` (e.g., `"version": "0.1.0"`)
- [ ] Update `versionCode` in `

*[truncated — see source for full prompt]*