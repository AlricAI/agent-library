# ASPIREONE TB SETUP GUIDE

> **For:** Captain's Old PC Setup  
**Date:** April 5, 2026  
**Status:** READY TO DEPLOY

---

## HARDWARE SPECIFICATIONS

**Asus AspireOne (Netbook):*

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LOCAL MODEL SETUP - ASUS ASPIREONE + SUSE LINUX + 1TB DRIVE
**For:** Captain's Old PC Setup  
**Date:** April 5, 2026  
**Status:** READY TO DEPLOY

---

## HARDWARE SPECIFICATIONS

**Asus AspireOne (Netbook):**
- **CPU:** Intel Atom (low power)
- **RAM:** 2-4GB (upgradeable to 2GB max typically)
- **Storage:** Internal SSD/HDD (small)
- **Display:** 10.1" (sufficient for headless operation)
- **Network:** WiFi + Ethernet
- **USB:** Multiple ports for external drive

**1TB External Drive:**
- **Connection:** USB 3.0 (or USB 2.0)
- **Format:** ext4 (Linux native)
- **Mount Point:** /mnt/tb-drive

---

## SUSE LINUX ISO

**From Repository:**
- Location: Similar to V3 Cosmic Engine specs
- Version: openSUSE Leap or Tumbleweed
- Architecture: x86_64 (Atom compatible)

**Installation Steps:**
1. Download SUSE Linux ISO
2. Create bootable USB: `dd if=openSUSE.iso of=/dev/sdX bs=4M`
3. Boot AspireOne from USB
4. Install to internal drive (minimal installation)
5. Configure network (WiFi/Ethernet)

---

## SYSTEM REQUIREMENTS CHECK

**AspireOne Limitations:**
- ⚠️ **Low RAM (2-4GB)** - Cannot run 70B models
- ✅ **Can run 8B models** - Perfect for specialized agents
- ✅ **Headless mode** - No GUI needed
- ✅ **USB boot** - Can boot from external drive

**Recommended Approach:**
- **Small models (7B-8B)** on AspireOne
- **Distributed setup** - AspireOne as agent node
- **Connect to main VPS** - Agent federation

---

## INSTALLATION GUIDE

### Step 1: Prepare TB Drive

```bash
# Connect 1TB drive to AspireOne
# Boot into SUSE Linux

# Format drive (if new)
sudo mkfs.ext4 /dev/sdX1  # Replace sdX with your drive

# Create mount point
sudo mkdir /mnt/tb-drive
sudo mount /dev/sdX1 /mnt/tb-drive

# Make permanent in /etc/fstab
echo "/dev/sdX1 /mnt/tb-drive ext4 defaults,noatime 0 2" | sudo tee -a /etc/fstab
```

### Step 2: Install Ollama

```bash
# Download Ollama for Linux
curl -fsSL https://ollama.com/install.sh | sh

# Configure to use TB drive
sudo mkdir -p /mnt/tb-drive/ol

*[truncated — see source for full prompt]*