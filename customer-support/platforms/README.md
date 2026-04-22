# PLATFORMS

> Sourcerer uses a flexible platform configuration system that allows both built-in platform support and user extensions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Platform Configuration System

Sourcerer uses a flexible platform configuration system that allows both built-in platform support and user extensions.

## Built-in Platforms

Current platforms are defined in `symbols/platforms/`:

- **apple2** - Apple II (6502)
  - Core symbols: apple2_rom.json, apple2_zeropage.json
  - Extensions: ProDOS, DOS 3.3

## Platform Configuration Structure

Each platform is defined by a JSON file in `symbols/platforms/{platform}.platform.json`:

```json
{
  "platform": "apple2",
  "name": "Apple II",
  "cpu": "6502",
  "symbol_files": ["symbols/apple2_rom.json"],
  "hint_files": [],
  "inline_data_routines": [],
  "extensions": {
    "prodos": {
      "symbol_files": ["symbols/prodos8.json"],
      "inline_data_routines": [
        {"address": "0xBF00", "name": "MLI", "bytes_after_call": 3}
      ]
    }
  }
}
```

## User Extensions

### Method 1: User Symbol File (Recommended)

Create a file named `{platform}.user.json` in the `symbols/` directory:

**Example: `symbols/apple2.user.json`**
```json
{
  "platform": "apple2",
  "description": "My custom Apple II symbols",
  "symbols": [
    {
      "address": "0x6000",
      "name": "MY_ROUTINE",
      "description": "My game routine",
      "type": "routine"
    }
  ]
}
```

The platform loader will automatically find and load this file when `--platform apple2` is used.

### Method 2: Explicit Symbol Files

You can always specify additional symbol files explicitly:

```bash
sourcerer --platform apple2 --symbols my_game_symbols.json -i game.bin -o game.s
```

### Method 3: Custom Platform Definition

Create your own platform file in `symbols/platforms/`:

**Example: `symbols/platforms/mygame.platform.json`**
```json
{
  "platform": "mygame",
  "name": "My Game",
  "description": "Custom configuration for my Apple II game",
  "cpu": "6502",
  "base_platform": "apple2",
  "symbol_files": [
    "symbols/apple2_rom.json",
    "symbols/apple2_zeropage.json",
    "symbols/mygame_symbols.json"
 

*[truncated — see source for full prompt]*