# Runbook Reliability

> ## 🚨 Emergency Response Guide

### If Transcript Processing Stalls

**Symptoms:**
- `make status` shows 0 transcriptions or old timestamps
- Episodes

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Reliability Runbook

## 🚨 Emergency Response Guide

### If Transcript Processing Stalls

**Symptoms:**
- `make status` shows 0 transcriptions or old timestamps
- Episodes > 0 but no new transcripts in 30+ minutes

**Immediate Actions:**
```bash
# 1. Check status
make status

# 2. Restart services
make restart

# 3. Monitor logs
make logs

# 4. Run smoke test
make smoke
```

**If Still Failing:**
```bash
# Check database connectivity
python3 scripts/db_introspect.py

# Test worker manually
python3 scripts/fixed_transcript_worker.py --limit 1

# Check disk space
df -h

# Check memory
free -h
```

### Service Recovery Commands

**Atlas Main Service:**
```bash
sudo systemctl restart atlas.service
sudo systemctl status atlas.service
journalctl -u atlas.service -f
```

**Watchdog Service:**
```bash
sudo systemctl restart atlas-watchdog.timer
sudo systemctl status atlas-watchdog.timer
journalctl -u atlas-watchdog -f
```

**Transcript Discovery:**
```bash
sudo systemctl restart atlas-discovery.timer
sudo systemctl status atlas-discovery.timer
journalctl -u atlas-discovery -f
```

## 📊 Health Check Commands

### Quick Status Check
```bash
make status
```

### Detailed Diagnostics
```bash
# Database health
python3 scripts/db_introspect.py

# Processing stats with details
python3 atlas_status.py --detailed

# Recent logs
make logs

# System resources
htop
df -h
```

### Manual Testing
```bash
# Test transcript worker
python3 scripts/fixed_transcript_worker.py --limit 2

# Test watchdog
python3 maintenance/enhanced_progress_watchdog.py

# Test notifications (requires Telegram setup)
python3 scripts/notify.py --test
```

## 🔧 Common Issues & Solutions

### "No transcriptions found"
**Cause:** Worker saving to wrong table or not running
**Solution:**
```bash
# Use fixed worker (saves to transcriptions table)
python3 scripts/fixed_transcript_worker.py --limit 5

# Check if old content exists
sqlite3 data/atlas.db "SELECT COUNT(*) FROM content WHERE content_type='podcast

*[truncated — see source for full prompt]*