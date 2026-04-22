# MCADDON STRUCTURE

> ## Overview

A `.mcaddon` file is a ZIP archive containing one or more Minecraft Bedrock Edition add-on packages. This document specifies the correct 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bedrock .mcaddon Package Structure Documentation

## Overview

A `.mcaddon` file is a ZIP archive containing one or more Minecraft Bedrock Edition add-on packages. This document specifies the correct internal structure for importing into Bedrock Edition.

## Critical Structure Requirements

### Top-Level Directories

**CORRECT (Plural):**
```
behavior_packs/
resource_packs/
```

**INCORRECT (Singular) - Will fail to import:**
```
behavior_pack/  ❌
resource_pack/  ❌
```

This is the most common error. Bedrock Edition requires the plural form.

## Complete Package Structure

```
my_addon.mcaddon
├── behavior_packs/                    # BEHAVIOR PACKS (plural)
│   └── my_mod_bp/                     # Individual behavior pack folder
│       ├── manifest.json              # REQUIRED: Pack metadata
│       ├── blocks/                    # Optional: Block definitions
│       │   ├── copper_block.json
│       │   └── tin_block.json
│       ├── items/                     # Optional: Item definitions
│       │   └── copper_item.json
│       ├── entities/                  # Optional: Entity definitions
│       │   └── custom_mob.json
│       ├── recipes/                   # Optional: Crafting recipes
│       │   └── copper_ingot.json
│       ├── loot_tables/               # Optional: Loot tables
│       ├── functions/                 # Optional: Command functions
│       ├── scripts/                   # Optional: JavaScript API scripts
│       │   └── main.js
│       ├── spawn_rules/               # Optional: Mob spawn rules
│       └── texts/                     # Optional: Language/localization
│           └── en_US.lang
│
└── resource_packs/                    # RESOURCE PACKS (plural)
    └── my_mod_rp/                     # Individual resource pack folder
        ├── manifest.json              # REQUIRED: Pack metadata
        ├── textures/                  # Optional: Texture files
        │   ├── blocks/
        │   │   ├── copper_block.png
        │   │   └── tin_blo

*[truncated — see source for full prompt]*