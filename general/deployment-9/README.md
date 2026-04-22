# DEPLOYMENT

> ## System Overview
- **Name:** ReggieStarr RS-80 POS System
- **Version:** 1.0.0
- **Platform:** Android 7.0+ (API 23+)
- **Target:** SUNMI V2 Pro, PA

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ReggieStarr RS-80 Deployment Checklist

## System Overview
- **Name:** ReggieStarr RS-80 POS System
- **Version:** 1.0.0
- **Platform:** Android 7.0+ (API 23+)
- **Target:** SUNMI V2 Pro, PAX A920, PAX A80

## Current Status: ✅ BUILD READY

### Core Features Implemented
- ✅ Calculator-style keypad (0-9, 00, C, +/-, decimal)
- ✅ Three modes: QTY, PLU, PRICE
- ✅ Product database with Room
- ✅ Cart management with real-time totals
- ✅ Tax calculation (8.25% configurable)
- ✅ Checkout dialog with payment types
- ✅ ESC/POS thermal printer integration
- ✅ Sample product seeding

### Architecture
```
app/src/main/java/com/ps/pos/
├── MainActivity.kt           # Entry point
├── RS80Application.kt        # App initialization
├── POSRepository.kt          # Data repository
├── data/
│   ├── AppDatabase.kt        # Room database
│   ├── entities/             # Product, Transaction, LineItem
│   └── dao/                  # Data access objects
├── ui/
│   ├── screens/
│   │   ├── RegisterScreen.kt    # Main register UI
│   │   └── CheckoutDialog.kt    # Payment dialog
│   ├── components/
│   │   └── CalculatorKeypad.kt # Calculator layout
│   └── theme/
│       ├── Color.kt, Theme.kt, Type.kt
├── viewmodel/
│   └── RegisterViewModel.kt   # Business logic
├── utils/
│   └── TaxCalculator.kt       # Tax utilities
└── services/
    └── PrinterService.kt      # ESC/POS printing
```

## Build Instructions

### Prerequisites
```bash
# Install Android SDK
sdkmanager "platforms;android-34"
sdkmanager "build-tools;34.0.0"

# Or use Gradle wrapper
./gradlew --version
```

### Debug Build
```bash
cd /root/.openclaw/workspace/reggiestarr-rs80
./gradlew assembleDebug
```
**Output:** `app/build/outputs/apk/debug/app-debug.apk`

### Release Build
```bash
# Create keystore (first time only)
keytool -genkey -v -keystore reggiestarr.keystore -alias rs80 -keyalg RSA -keysize 2048 -validity 10000

# Build release
./gradlew assembleRelease
```
**Output:** `app/build/outputs/apk/release/app-release

*[truncated — see source for full prompt]*