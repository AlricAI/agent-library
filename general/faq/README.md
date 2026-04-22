# Faq

> Everything you need to know about ModPorter AI, from basic usage to advanced features.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frequently Asked Questions

Everything you need to know about ModPorter AI, from basic usage to advanced features.

## General Questions

### 1. What is ModPorter AI?

ModPorter AI is the first AI-powered tool that converts Minecraft Java Edition mods to Bedrock Edition add-ons automatically. It uses advanced multi-agent AI systems to analyze Java code, translate it to JavaScript (Bedrock Script API), convert assets, and package everything into a ready-to-use .mcaddon file.

**Key benefits**:
- Saves 3-6 months of manual rewriting
- 60-80% automation for most mods
- Supports complex features (entities, dimensions, GUI)
- Continuous learning from community conversions

### 2. How accurate is the conversion?

Accuracy depends on mod complexity:

| Mod Type | Accuracy | Manual Work |
|----------|----------|-------------|
| Simple items/blocks | 95%+ | 0-1 hours |
| Moderate (entities, recipes) | 80-90% | 2-5 hours |
| Complex (custom logic, GUI) | 60-80% | 5-20 hours |
| Very complex (dimensions, networking) | 40-60% | 20+ hours |

The AI improves with each conversion, learning from manual corrections.

### 3. What Java editions are supported?

**Supported**:
- Minecraft Forge (1.12.2 - 1.20.x)
- Fabric (1.14+)
- Quilt (experimental)
- Vanilla mods (no loader)

**Not supported**:
- Rift, LiteLoader (older loaders)
- Highly obfuscated mods
- Mods with native libraries (JNI)

### 4. What Bedrock features are supported?

**Fully supported**:
- Items, blocks, entities
- Recipes, loot tables
- Textures, models, sounds
- Script API (JavaScript)
- Components system

**Partially supported**:
- Custom GUI (needs manual work)
- Network packets (Script API workaround)
- Custom rendering (manual Bedrock implementation)
- Dimensions (experimental features)

**Not supported**:
- Native code mods
- Server-side only mods
- Some client-side rendering

### 5. Is this against Minecraft EULA?

No. ModPorter AI:
- Does not modify Minecraft's code
- Creates original add-on content
- Respe

*[truncated — see source for full prompt]*