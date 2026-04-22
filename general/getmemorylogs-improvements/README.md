# Getmemorylogs Improvements

> **Purpose:** Fix self-referential search problem and improve usability

---

## 🎯 **Changes Made:**

### **1. Default `removeAllLines="GetMemoryLogs"

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GetMemoryLogs Improvements - 2025-01-09

**Purpose:** Fix self-referential search problem and improve usability

---

## 🎯 **Changes Made:**

### **1. Default `removeAllLines="GetMemoryLogs"` ($40)**

**Problem:** When searching for log content, matches would include my own GetMemoryLogs function calls, creating noise.

**Solution:** Change default value from `""` to `"GetMemoryLogs"` to automatically filter out self-referential logs.

**Impact:**
- ✅ Automatically excludes lines containing "GetMemoryLogs"
- ✅ Solves the most frustrating problem
- ✅ Can still override by setting `removeAllLines=""`

---

### **2. Add `useRegex` Parameter ($30)**

**Problem:** Unclear whether `lineContains` and `removeAllLines` use regex or literal text matching.

**Solution:** Add explicit `bool useRegex = true` parameter (following `ReplaceAllInFiles` pattern).

**Impact:**
- ✅ Makes behavior explicit
- ✅ `useRegex=true` (default): Pattern is regex
- ✅ `useRegex=false`: Pattern is literal text (special chars auto-escaped)
- ✅ Error messages now say "regex" or "text" based on mode

**Usage:**
```csharp
// Regex mode (default)
GetMemoryLogs(lineContains: "Test.*timeout")  // Matches "Test 1 timeout", "Testing timeout", etc.

// Literal mode
GetMemoryLogs(lineContains: "Test.*timeout", useRegex: false)  // Matches only "Test.*timeout" exactly
```

---

### **3. Better Feedback on Match Counts ($10)**

**Problem:** When getting too many matches, hard to know if I should refine the search.

**Solution:** Enhanced metadata to show match counts and truncation info.

**Before:**
```
[Showing lines 100-250 of 5000 total] [4750 lines remaining]
```

**After:**
```
[Matched 2000 lines, showing 150 lines with context, lines 100-250 (truncated: 1850 more matched lines not shown) of 5000 total] [4750 lines remaining]
```

**Impact:**
- ✅ Shows how many lines matched the pattern
- ✅ Shows if context lines were included
- ✅ Shows how many more matches were truncated
- ✅ Helps understand if sear

*[truncated — see source for full prompt]*