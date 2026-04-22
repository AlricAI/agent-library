# VIDEO 13 PINE SCRIPT COMPLETE COURSE

> **Source:** The Art of Trading Pine Script Course (transcript provided 2026-03-07 08:04 UTC)
**Status:** Full Programming Education Course
**Language:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 13: COMPLETE Pine Script Mastery Course (6+ Hours)

**Source:** The Art of Trading Pine Script Course (transcript provided 2026-03-07 08:04 UTC)
**Status:** Full Programming Education Course
**Language:** Pine Script (TradingView)
**Agent:** the-great-cryptonio
**Total Lessons:** 20 comprehensive lessons

---

## 📚 Course Overview

Complete from-scratch programming course covering Pine Script v5/v6 programming language used for creating custom indicators and strategies on TradingView.

---

## Lesson 1: Pine Script Editor

### Key Areas:
- **Pine Editor Button:** Opens script editor
- **Create New Script:** 
  - Indicator (basic scripts)
  - Strategy (backtesting)
  - Library (code reuse)

### Editor Settings:
| Setting | Purpose | Recommendation |
|---------|---------|---------------|
| Autocomplete | Code suggestions | **ON** |
| Mini Map | Code overview | Off (clutter) |
| Status Bar | Compiler output | **ON** |
| Line Length Guide | Keep code short | Optional |

### Important Functions:
- **Add to Chart** - Compiles and displays script
- **Publish Indicator** - Makes script public
- **Version Control** - Shows every save with diffs (green = added, red = removed)
- **Pine Logs** - Debug errors

---

## Lesson 2: The Pine Script Compiler

### Version Directives:
```
@version=5    // Current standard
@version=6    // Newest (same syntax as v5, backend optimized)
```
> **Important:** v6 = same syntax as v5, just "under the hood" performance improvements

### Common Errors:
- Missing closing brackets `)` `}` `]`
- Missing quotation marks `"` `'`
- Syntax errors = red underline

### Multi-line Code:
```
function(
    parameter1,
    parameter2
    )
```
Must indent with **tab + space** for continuation

---

## Lesson 3: Comments

### Syntax:
```
// This is a single-line comment

/* 
Multi-line
comment
*/
```

### Best Practice:
- Comment heavily - explain WHY not just WHAT
- More comments better than fewer
- Future-you will thank past-you
- Public scripts ne

*[truncated — see source for full prompt]*