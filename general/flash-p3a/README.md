# Flash P3a

> Flash the p3a firmware to your Waveshare ESP32-P4 board.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Flash p3a Firmware

Flash the p3a firmware to your Waveshare ESP32-P4 board. This is a one-time process — after the initial flash, all future updates are installed wirelessly via `http://p3a.local/ota`.

---

## Option 1: Web Flasher — Recommended

The easiest way to flash your p3a. No software installation required — just a web browser.

**Requirements:** Chrome 89+ or Edge 89+ (Firefox and Safari don't support WebSerial)

1. Go to the [**p3a Web Flasher**](https://fabkury.github.io/p3a/web-flasher/)
2. Select the firmware version from the dropdown
3. Connect your p3a via USB-C
4. Click **Connect** and select your device from the browser prompt
5. Click **Flash Device**
6. Wait ~2 minutes
7. Done! Your device will automatically reboot into p3a.

The web flasher downloads firmware directly from GitHub and flashes it to your device — works on Windows, macOS, and Linux.

---

## Option 2: p3a Flasher (Windows)

A standalone Windows application for flashing — useful if you don't have Chrome/Edge or prefer an offline tool.

1. Download `p3a-flasher.exe` from the [releases folder](https://github.com/fabkury/p3a/tree/main/release/)
2. Connect your p3a via USB-C
3. Run `p3a-flasher.exe`
4. Click **Flash Device**
5. Wait ~2 minutes
6. Done! Your device will automatically reboot into p3a.

The flasher auto-detects your device and includes the firmware — no installation, configuration or Internet connection needed.

---

## Option 3: Command Line (All Platforms)

For macOS, Linux, or if you prefer the command line. This method gives you full control over the flashing process.

### Step 1: Install Python and esptool

**Windows:**
1. Download Python from [python.org](https://www.python.org/downloads/)
2. During installation, check **"Add Python to PATH"**
3. Open PowerShell and run:
   ```powershell
   pip install esptool
   ```

**macOS:**
```bash
brew install python
pip3 install esptool
```

**Linux:**
```bash
sudo apt install python3 python3-pip
pip3 install esptool
```

#

*[truncated — see source for full prompt]*