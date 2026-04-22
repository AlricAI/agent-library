# VIDEO 17 PINESCRIPT BASICS

> **Source:** TradingView Education (transcript provided 2026-03-07 08:27 UTC)
**Status:** Pine Script Foundation Tutorial Complete
**Topic:** Introduct

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 17: Pine Script Basics — Building Your First Indicator

**Source:** TradingView Education (transcript provided 2026-03-07 08:27 UTC)
**Status:** Pine Script Foundation Tutorial Complete
**Topic:** Introduction to Pine Script v5, creating custom indicators
**Difficulty:** Beginner
**Prerequisite:** None

---

## 🎯 LEARNING OBJECTIVES

By the end of this video, you will:
- ✅ Understand Pine Editor location and interface
- ✅ Know the 5 versions of Pine Script (v5 is current)
- ✅ Create a basic indicator from scratch
- ✅ Plot indicators on charts
- ✅ Customize colors and styles

---

## 📍 Step 1: Open Pine Editor

**Location:** Bottom of TradingView chart

**What is Pine Editor?**
- IDE (Integrated Development Environment) built into TradingView
- Where you write, save, and manage Pine Script code

---

## 📝 Step 2: Pine Script Fundamentals

### Version Declaration
```pinescript
//@version=5
```
**What it does:**
- Tells TradingView which Pine Script version to use
- **v5 is current** — stay updated with latest versions
- Always start your script with this line

**Where to learn more:**
- TradingView User Manual (linked in video)
- Documentation for all 5 versions

---

## 💬 Step 3: Comments

```pinescript
// This is a comment
// Anything starting with // is ignored by the compiler
// Use comments to document your code
```

**Syntax:** `//` makes everything after it on that line a comment
**Purpose:** Documentation, explanations, notes to self

---

## 🚀 Step 4: Create Your First Indicator

### The `indicator()` Function

```pinescript
indicator("Rocket Moving Average", overlay=true)
```

**Components:**
| Component | Value | Meaning |
|-----------|-------|---------|
| `indicator` | Function | Declares this is an indicator |
| `"Rocket Moving Average"` | String | **Name** of your indicator |
| `overlay=true` | Boolean | Plots **ON the price chart** |

**What is `overlay=true`?**
- `true` = Draws indicator **directly on the price chart**
- `false` = Draws in

*[truncated — see source for full prompt]*