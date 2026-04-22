# BOARD CAPABILITIES

> Hardware capabilities of the ESP32-P4-WIFI6-Touch-LCD-4B board used by p3a.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Board Capabilities Reference

Hardware capabilities of the ESP32-P4-WIFI6-Touch-LCD-4B board used by p3a.

- **Board**: [Waveshare ESP32-P4-WIFI6-Touch-LCD-4B](https://www.waveshare.com/product/arduino/boards-kits/esp32-p4/esp32-p4-wifi6-touch-lcd-4b.htm?sku=31416)
- **Wiki**: [ESP32-P4-WIFI6-Touch-LCD-4B Wiki](http://www.waveshare.com/wiki/ESP32-P4-WIFI6-Touch-LCD-4B)
- **SoC**: ESP32-P4NRW32 (RISC-V dual-core HP @ 360 MHz + single-core LP @ 40 MHz)
- **Memory**: 32 MB PSRAM (in-package), 32 MB NOR Flash (on-board)
- **Display**: 4" 720×720 IPS, MIPI-DSI, capacitive 5-point touch (GT911)

---

## Table of Contents

- [Audio Subsystem](#audio-subsystem)
- [Hardware Accelerators](#hardware-accelerators)
  - [JPEG Codec](#jpeg-codec)
  - [Pixel-Processing Accelerator (PPA)](#pixel-processing-accelerator-ppa)
  - [H.264 Encoder](#h264-encoder)
  - [2D-DMA Controller](#2d-dma-controller)
  - [Image Signal Processor (ISP)](#image-signal-processor-isp)
  - [Cryptographic Accelerators](#cryptographic-accelerators)
- [Display Interface (MIPI-DSI)](#display-interface-mipi-dsi)
- [Connectivity and Peripherals](#connectivity-and-peripherals)
- [p3a Usage Summary](#p3a-usage-summary)

---

## Audio Subsystem

The board has a complete audio output path wired on-board, including a speaker pre-connected to the speaker header.

### Audio Signal Chain

```
ESP32-P4  ──I2S──>  ES8311 (DAC)  ──analog──>  NS4150B (Class-D Amp)  ──>  8Ω 2W Speaker
           ──I2C──>  ES8311 (config)
```

### Audio Hardware

| Component | Role | Key Specs |
|-----------|------|-----------|
| **ES8311** | Mono audio codec (Everest Semiconductor) | 24-bit DAC, 8–96 kHz sample rate, 110 dB SNR, 1.8–3.3V |
| **NS4150B** | 3W mono Class-D power amplifier (Nsiway) | Up to 2.8W @ 5V/4Ω, 88% efficiency, filterless |
| **Speaker** | 8Ω 2W (MX1.25 2P connector) | Pre-connected on the board |
| **ES7210** | Echo cancellation ADC (microphone input) | For recording, not playback |

### Audio Pin Mapping

| Signal 

*[truncated — see source for full prompt]*