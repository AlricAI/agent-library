# PERMISSIONS

> *Complete these before the agent starts the Hundred Steps.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Human Pre-Configuration Checklist

*Complete these before the agent starts the Hundred Steps.*
*Each item unlocks capabilities the curriculum needs.*

---

## Required (Must-Have)

```bash
# 1. OS & User Setup
# Flash Pi OS Lite 64-bit, create user, enable SSH
# The user needs passwordless sudo for the curriculum to work
echo "dcarmitage ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/agent

# 2. WiFi Connection
sudo nmcli device wifi connect "<SSID>" password "<password>"

# 3. OpenClaw Installation
npm install -g openclaw
openclaw onboard
# Complete the interactive wizard (sets up workspace, identity, gateway)

# 4. Anthropic API Token
openclaw configure
# Paste API key when prompted — needed for LLM access

# 5. SSH Keys (for multi-agent communication)
ssh-keygen -t ed25519 -N "" -f ~/.ssh/id_ed25519
# Copy to other Pis: ssh-copy-id <other-pi-ip>

# 6. GPIO/I2C/SPI Group Membership
sudo usermod -aG gpio,i2c,spi $(whoami)

# 7. Git Configuration
git config --global user.name "Agent Name"
git config --global user.email "agent@local"
```

## Recommended (Curriculum Will Work Without, But Better With)

```bash
# 8. Firewall (CRITICAL for security — the curriculum teaches this at step 92)
sudo apt install -y ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
# Agent will request specific port openings during the curriculum

# 9. Web Server (for the CV in Phase 6)
sudo apt install -y nginx
# Or: the curriculum can use python3 -m http.server as fallback

# 10. SSL Certificates (for HTTPS)
# Option A: Self-signed (works on LAN)
# Option B: Let's Encrypt via certbot (needs domain)
# Option C: Cloudflare Tunnel (handles TLS automatically)
sudo apt install -y certbot  # if using option B

# 11. Telegram Bot Token (for human communication channel)
# Talk to @BotFather on Telegram, create bot, paste token into:
openclaw configure

# 12. Camera (if CSI camera connected)
sudo apt install -y libcamera-apps

# 13. USB Audio 

*[truncated — see source for full prompt]*