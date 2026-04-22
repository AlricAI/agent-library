# WASTE FEEDER README

> ## 🗑️ Captain's Waste Management System

### What This Is
Every 30 minutes, Miles' brain collects "waste" (kidney bladder data, noise signatures, fai

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Miles → Mortimer Waste Pipeline

## 🗑️ Captain's Waste Management System

### What This Is
Every 30 minutes, Miles' brain collects "waste" (kidney bladder data, noise signatures, failed patterns, etc.) and emails it to you. You then feed this to Mortimer's brain for processing.

---

## 📧 PART 1: WASTE EMAILER (Runs on Miles VPS)

**Location:** `/root/.openclaw/workspace/scripts/waste_emailer.py`

**What it does:**
- Checks Miles' kidneys every 30 minutes
- Packages waste data as JSON
- Emails it to `Antonio.hudnall@gmail.com`
- Subject: `🗑️ Miles Brain Waste Drop — YYYY-MM-DD HH:MM UTC`

**Email contains:**
- Plain text summary (bladder level, QMD cycles, signal quality, etc.)
- `miles_waste.json` attachment (full data)
- Any queued sespool items

**Cron schedule:** Every 30 minutes (next run in ~30 min)

---

## 🧠 PART 2: MORTIMER FEEDER (Runs on YOUR side)

**Location:** Download `mortimer_feeder.py` to wherever Mortimer's brain runs.

**Setup:**
```bash
# Download the script to your Mortimer VPS
wget https://your-storage/mortimer_feeder.py
# OR copy from Miles' email attachment

# Make executable
chmod +x mortimer_feeder.py
```

**Usage:**

```bash
# Single file feed (when you get an email)
python3 mortimer_feeder.py --input miles_waste.json

# Watch mode (auto-feed when new files appear)
python3 mortimer_feeder.py --watch --watch-dir ./incoming_waste

# Custom Mortimer endpoint (if not localhost:7474)
python3 mortimer_feeder.py --input miles_waste.json --brain-endpoint http://mortimer-ip:7474
```

**Feed Modes:**
- `auto` (default): Tries HTTP → Socket → File (in order)
- `http`: POSTs to Mortimer's HTTP endpoint
- `socket`: Sends via Unix socket `/tmp/mortimer_brain.sock`
- `file`: Writes to `./mortimer_input/` for Mortimer to read

---

## 📁 Workflow

```
[Every 30 min]
     ↓
[Miles Brain] → [Kidneys Full?] → [Email JSON to Captain]
                                     ↓
                              [Captain receives email]
                          

*[truncated — see source for full prompt]*