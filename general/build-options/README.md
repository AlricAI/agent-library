# BUILD OPTIONS

> ## Current Status: ✅ Feature Complete (v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ReggieStarr RS-80 Build Options

## Current Status: ✅ Feature Complete (v1.0.1)

### Features Implemented
- ✅ **Calculator Keypad** - 0-9, 00, C, +/-, decimal, 3 modes (QTY/PLU/PRICE)
- ✅ **Product Database** - Room with PLU, barcode, categories
- ✅ **Cart Management** - Real-time totals, tax calculation (8.25%)
- ✅ **Checkout Dialog** - Cash/Card/Other payments, change calculation
- ✅ **Product Management** - CRUD UI with search/filter (NEW!)
- ✅ **Printer Service** - ESC/POS thermal printer integration
- ✅ **Sample Data** - 8 products pre-loaded for testing

### Build Options

#### Option 1: Local Android Studio (Recommended)
```bash
# Clone and open
git clone https://github.com/hcindus/AOS-Brain.git
cd AOS-Brain/reggiestarr-rs80

# Open in Android Studio
studio .

# Sync Gradle, then build:
# Build → Build Bundle(s) / APK(s) → Build APK(s)
```

#### Option 2: Command Line (Requires Android SDK)
```bash
cd reggiestarr-rs80

# Set ANDROID_HOME
export ANDROID_HOME=/path/to/android-sdk

# Build debug APK
./gradlew assembleDebug

# Output: app/build/outputs/apk/debug/app-debug.apk
```

#### Option 3: GitHub Actions CI/CD
Create `.github/workflows/build.yml` to auto-build on push:
```yaml
name: Build APK
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      - uses: android-actions/setup-android@v2
      - run: cd reggiestarr-rs80 && ./gradlew assembleDebug
      - uses: actions/upload-artifact@v3
        with:
          name: apk
          path: reggiestarr-rs80/app/build/outputs/apk/debug/*.apk
```

### Next Steps for Deployment

1. **Build APK** using one of the options above
2. **Test on Device** - Transfer to SUNMI V2 Pro or PAX terminal
3. **Configure Printer** - Update PrinterService.kt with your printer IP
4. **Load Products** - Use Product Management screen to add your catalog
5. **Train Staff** - C

*[truncated — see source for full prompt]*