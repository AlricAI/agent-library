# HOW TO USE

> This guide covers everything you need to know to use your p3a pixel art player, from initial setup to advanced features.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Use p3a

This guide covers everything you need to know to use your p3a pixel art player, from initial setup to advanced features.

## Table of Contents

1. [Initial Setup](#initial-setup)
2. [Preparing Artwork](#preparing-artwork)
3. [Touch Controls](#touch-controls)
4. [Wi-Fi Setup](#wi-fi-setup)
5. [Web Interface](#web-interface)
6. [REST API](#rest-api)
7. [USB SD Card Access](#usb-sd-card-access)
8. [Firmware Updates](#firmware-updates)
9. [Giphy Integration](#giphy-integration)
10. [Device Registration](#device-registration)
11. [Makapix Club Features](#makapix-club-features)
12. [PICO-8 Monitor](#pico-8-monitor-optional)

---

## Initial Setup

### What you need

- Waveshare ESP32-P4-WIFI6-Touch-LCD-4B board
- USB-C data cable (not a charging-only cable)
- microSD card
- a small screwdriver

### First-time setup

1. **Insert the microSD card** into the slot on the board. This requires unscrewing the back plate.
2. **Flash the firmware**. See [flash-p3a.md](flash-p3a.md) for instructions.
3. **Configure Wi-Fi** by following the [Wi-Fi Setup](#wi-fi-setup) instructions.

---

## Preparing Artwork

### Supported formats

p3a supports these image formats:
- **WebP** (animated and static) — recommended for best quality and compression; supports transparency
- **GIF** (animated and static) — supports transparency
- **PNG** (static) — supports transparency with full alpha channel
- **JPEG** (static)

**Transparency support**: Images with transparent backgrounds or alpha channels are fully supported. The background color behind transparent areas can be configured via the web interface or REST API.

### File organization

The firmware looks for artwork in this order:
1. `/animations` folder on the microSD card (preferred)
2. If that folder is empty or missing, it searches the entire card for a folder containing image files

**Recommended setup:**
1. Create a folder called `animations` on your microSD card
2. Copy your artwork files into that folder
3. Files ar

*[truncated — see source for full prompt]*