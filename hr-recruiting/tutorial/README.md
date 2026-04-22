# Tutorial

> This detailed tutorial walks you through converting a Java mod to Bedrock using ModPorter AI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Step-by-Step Conversion Tutorial

This detailed tutorial walks you through converting a Java mod to Bedrock using ModPorter AI. We'll use a simple "Custom Sword" mod as an example.

## Example Mod: Ruby Sword

For this tutorial, we'll convert a simple Java mod that adds:
- A new sword item (Ruby Sword)
- Custom texture
- Attack damage and durability

## Step 1: Prepare Your Java Mod

### What You Need

Your mod should include:
- **Java source files** (.java) - the mod logic
- **Resource files** - textures, models, sounds
- **mod metadata** - mcmod.info, fabric.json, or forge.mods.toml

### Example Structure

```
rubysword.jar
├── assets/
│   └── rubysword/
│       ├── textures/
│       │   └── items/ruby_sword.png
│       └── models/
│           └── item/ruby_sword.json
├── com/example/rubysword/
│   ├── RubySword.java
│   ├── RubySwordItem.java
│   └── RubySwordMod.java
└── META-INF/
    └── mods.toml
```

## Step 2: Upload to ModPorter AI

1. **Navigate to [modporter.ai](https://modporter.ai)**
2. **Click "Upload Mod"** or drag-and-drop your .jar file
3. **Wait for analysis** (30-60 seconds)

### What the Analysis Shows

```
Mod Analysis Complete
├── Detected Features
│   ├── Items: 1 (Ruby Sword)
│   ├── Blocks: 0
│   ├── Entities: 0
│   └── Recipes: 0
├── Complexity: Simple
├── Estimated Time: 5 minutes
└── Conversion Confidence: 95%
```

## Step 3: Review Conversion Plan

Before starting, review the AI's plan:

### Detected Components

| Component | Java Class | Bedrock Equivalent | Confidence |
|-----------|-----------|-------------------|------------|
| Ruby Sword Item | RubySwordItem | items/ruby_sword | 95% |
| Texture | ruby_sword.png | textures/items/ruby_sword.png | 100% |
| Model | ruby_sword.json | models/item/ruby_sword.json | 90% |

### Potential Issues

- **High confidence**: No issues expected
- **Medium confidence**: May need manual texture adjustment
- **Low confidence**: Custom attack logic may need tweaking

## Step 4: Start Conversion

Click

*[truncated — see source for full prompt]*