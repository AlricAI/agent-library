# AGENT SMITH REFERENCE

> _Source: Screenshots from Omar + GitHub (yashkumarthakur2004/agent-smith-2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Smith 2.0 — Complete Reference

_Source: Screenshots from Omar + GitHub (yashkumarthakur2004/agent-smith-2.0)_
_Private repo — reference for building Lord Sav_

---

## 🏗️ Architecture

### Main Files
| File | Purpose |
|------|---------|
| `jarvis.py` | Main Telegram bot — all handlers |
| `masterconnect.py` | Flask web dashboard for WhatsApp linking |
| `whatsapp_bot.py` | WhatsApp bot integration |
| `requirements.txt` | Python dependencies |

### Bot Framework
- **Library:** `pyTelegramBotAPI` (telebot)
- **Database:** MongoDB Atlas (pymongo)
- **Web:** Flask + gunicorn
- **Image Processing:** Pillow (PIL)
- **PDF Generation:** reportlab
- **File Handling:** PyPDF2, python-docx, python-pptx

---

## 📋 Features & Commands

### Core Commands
| Command | Description |
|---------|-------------|
| `/start` | Welcome message + feature menu (inline buttons) |
| `/help` | Help menu with all commands |
| `/masterconnects` | Link bot to WhatsApp via URL |
| `/admin` | Admin panel (add/remove credits) |

### Image Tools
| Command | Description |
|---------|-------------|
| `/imagine` | Generate images (DALL-E 3, Flux 1.1 Pro, Recraft V3) |
| `/removebg` | Remove background from uploaded image |
| `/upscale` | Upscale uploaded image |
| `/facerestore` | Restore/enhance faces in photos |

### Video Generation
| Command | Description |
|---------|-------------|
| `/video` | Video generation menu |
| Supports | Kling, Luma, Hunyuan, Hailuo, Pika, Pixverse, OpenAI Sora, Wan Video, Stable Diffusion Video, CogVideoX |

### Audio & Voice
| Command | Description |
|---------|-------------|
| `/voice` | Realtime voice chat (Gemini, GPT-4o, Claude 3.5 Sonnet) |
| `/tts` | Text-to-speech (OpenAI voices) |
| `/music` | Music generation (Lyria, MusicFX) |

### TTS Voices Available
`nova`, `alloy`, `echo`, `fable`, `onyx`, `shimmer`, `coral`, `sage`, `ash`, `ballad`, `verse`

### File Conversions
| Command | Description |
|---------|-------------|
| `/imagetopdf` | Convert imag

*[truncated — see source for full prompt]*