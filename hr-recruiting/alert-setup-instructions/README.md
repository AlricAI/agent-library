# ALERT SETUP INSTRUCTIONS

> ## Quick Setup

**Run the interactive setup script:**
```bash
./scripts/setup_alerts.sh
```

This will walk you through both Telegram and Uptime Kuma 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔔 Atlas Alert System Setup Instructions

## Quick Setup

**Run the interactive setup script:**
```bash
./scripts/setup_alerts.sh
```

This will walk you through both Telegram and Uptime Kuma configuration.

## Manual Setup Instructions

### 📱 Telegram Bot Setup

1. **Create Bot with BotFather:**
   - Open Telegram and message [@BotFather](https://t.me/BotFather)
   - Send: `/newbot`
   - Name: `Atlas Monitoring Bot`
   - Username: `atlas_monitoring_[your_name]_bot`
   - **Copy the bot token** (format: `1234567890:ABCdefGHIjklMNOpqrsTUVwxyz`)

2. **Get Your Chat ID:**
   - Start a chat with your new bot
   - Send any message (like "hello")
   - Open: `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
   - Find `"chat":{"id":NUMBERS}` and **copy those numbers**

3. **Add to Atlas `.env` file:**
   ```bash
   TELEGRAM_BOT_TOKEN=your_bot_token_here
   TELEGRAM_CHAT_ID=your_chat_id_here
   ```

### 🔔 Uptime Kuma Setup (RPI)

1. **Create Push Monitor:**
   - Open your Uptime Kuma dashboard on RPI
   - Click "Add New Monitor"
   - Select "Push" type
   - Name: `Atlas Transcript Processing`
   - **Copy the Push URL** (format: `http://your-rpi-ip:3001/api/push/xxxxx`)

2. **Add to Atlas `.env` file:**
   ```bash
   UPTIME_KUMA_URL=http://your-rpi-ip:3001/api/push/xxxxx
   ```

## Testing

```bash
# Test Telegram only
python3 scripts/notify.py --test

# Send manual test message
python3 scripts/notify.py --msg "Atlas is working!" --title "Test Alert"

# Test the watchdog system
python3 maintenance/enhanced_progress_watchdog.py
```

## What You'll Get

### Alert Types

1. **Stall Alerts** (when transcript processing stops):
```
🚨 Atlas Alert: Transcript Processing Stalled

Episodes: 16,936
Transcriptions: 5
Last Activity: 45 minutes ago
Latest: 2025-09-10 18:51:33

Restart Results:
✅ atlas.service: restarted
✅ atlas-watchdog.timer: restarted
```

2. **Recovery Alerts** (when processing resumes):
```
✅ Atlas Recovery: Transcript Processing Recovered

Processing has 

*[truncated — see source for full prompt]*