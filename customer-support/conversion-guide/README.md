# Conversion Guide

> This guide covers the conversion process, supported features, and best practices for converting Minecraft Java Edition mods to Bedrock Edition add-ons.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Conversion Guide

This guide covers the conversion process, supported features, and best practices for converting Minecraft Java Edition mods to Bedrock Edition add-ons.

## Understanding the Conversion Process

ModPorter AI uses a multi-agent AI system to analyze Java mod code and translate it to Bedrock-compatible formats. The conversion process involves:

1. **Analysis**: Extracting mod structure, dependencies, and components
2. **Translation**: Converting Java code to Bedrock Script API
3. **Asset Conversion**: Processing textures, models, and sounds
4. **Validation**: Checking for errors and compatibility issues
5. **Packaging**: Creating a distributable .mcaddon file

---

## Supported Features

### Blocks

| Feature | Support Level | Notes |
|---------|---------------|-------|
| Basic blocks | Full | Properties, states, loot tables |
| Block entities | Full | Inventory, tile entities |
| Custom textures | Full | PNG support, animation frames |
| Block models (JSON) | Full | Standard Bedrock JSON format |
| Tile entities | Full | Data-driven storage |

### Items

| Feature | Support Level | Notes |
|---------|---------------|-------|
| Basic items | Full | Name, lore, texture |
| Custom textures | Full | PNG support |
| Item components | Full | Bedrock 1.20+ components |
| Enchantments | Partial | Standard enchantments only |
| Food items | Full | Hunger restoration |

### Entities

| Feature | Support Level | Notes |
|---------|---------------|-------|
| Mobs/NPCs | Full | Basic behavior, AI |
| Projectiles | Full | Arrow, fireball, etc. |
| Entity models | Full | JSON models |
| Entity textures | Full | PNG support |
| Custom AI behaviors | Partial | Requires manual adjustment |

### Recipes

| Feature | Support Level | Notes |
|---------|---------------|-------|
| Crafting recipes | Full | Shaped, shapeless |
| Smelting recipes | Full | Furnace, blast furnace |
| Stonecutter recipes | Full | Single item output |
| Brewing recipes | Full | Standard potions

*[truncated — see source for full prompt]*