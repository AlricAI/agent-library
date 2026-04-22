# Troubleshooting

> This guide helps you resolve common issues when using ModPorter AI to convert Java mods to Bedrock add-ons.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting Guide

This guide helps you resolve common issues when using ModPorter AI to convert Java mods to Bedrock add-ons.

## Table of Contents

- [Upload Issues](#upload-issues)
- [Conversion Failures](#conversion-failures)
- [Missing Features](#missing-features)
- [Installation Problems](#installation-problems)
- [Runtime Errors](#runtime-errors)
- [Performance Issues](#performance-issues)

---

## Upload Issues

### "File not supported" Error

**Problem**: Your mod file won't upload

**Possible Causes**:
1. File format not supported (must be .jar or .zip)
2. File corrupted during download
3. File size exceeds limit (100MB for free tier)
4. Mod uses non-standard loader (not Forge/Fabric)

**Solutions**:

```bash
# Verify file type
file your_mod.jar

# Check file size
ls -lh your_mod.jar

# Validate JAR structure
unzip -l your_mod.jar | grep ".class"
```

**Workaround**:
- Re-download the mod from original source
- Extract and re-package as ZIP
- For non-Forge/Fabric mods, contact support

### "Mod analysis timeout"

**Problem**: Analysis takes longer than 2 minutes

**Causes**:
- Very large mod (>10,000 Java files)
- Complex dependencies
- Server overload

**Solutions**:
1. Wait and retry (server may be busy)
2. Split mod into smaller parts
3. Upgrade to Pro for priority processing
4. Use API for batch processing

---

## Conversion Failures

### "Conversion failed: Java parsing error"

**Problem**: AI cannot parse Java code

**Common Causes**:
1. Obfuscated code (common in decompiled mods)
2. Non-standard Java syntax
3. Corrupted class files

**Solutions**:

```java
// BAD - Obfuscated code
class a {
    public void a(b c) { ... }
}

// GOOD - Deobfuscated code
class SwordItem {
    public void attack(Entity target) { ... }
}
```

**Fix**:
- Use deobfuscator (ForgeFlower, CFR)
- Re-compile from source if available
- Contact mod author for deobfuscated version

### "Conversion failed: Missing dependencies"

**Problem**: Mod requires libraries not found


*[truncated — see source for full prompt]*