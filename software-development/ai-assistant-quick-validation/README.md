# AI ASSISTANT QUICK VALIDATION

> **Purpose**: Fast smoke test before formal user testing  
**Duration**: 15-20 minutes  
**Tester**: [Your name]  
**Date**: [Today]  

---

## Pre-Tes

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Assistant - Quick Validation Checklist

**Purpose**: Fast smoke test before formal user testing  
**Duration**: 15-20 minutes  
**Tester**: [Your name]  
**Date**: [Today]  

---

## Pre-Testing Setup

- [ ] Dev server running (`npm run dev`)
- [ ] Browser dev tools open (F12) for error checking
- [ ] Test blog ID: `6a4e2213-a5a6-4ee1-8aa6-4fd5d67e0c26`
- [ ] Test blog writer: `632da6e6-96d6-4c60-bb1b-01343b09d953`

---

## Blog Detail Page Tests

### Test 1: Ask AI Button Visible ✓
- [ ] Navigate to blog detail page
- [ ] Look for "Ask AI" button in header (next to status badges)
- [ ] Button has blue background and info icon
- **Result**: ✅ PASS / ❌ FAIL

### Test 2: Modal Opens on Click ✓
- [ ] Click "Ask AI" button
- [ ] Modal opens with smooth transition
- [ ] Modal has header, content area, footer
- [ ] Close button (X) visible in top-right
- **Result**: ✅ PASS / ❌ FAIL

### Test 3: Modal Shows Loading State ✓
- [ ] Modal opens
- [ ] Loading spinner appears with "Analyzing..." text
- [ ] Loading lasts 1-3 seconds
- **Result**: ✅ PASS / ❌ FAIL

### Test 4: Response Displays Correctly ✓
- [ ] Modal shows 4 sections: Current State, Blockers, Quality Issues, Next Steps
- [ ] Summary shows "Can Proceed" and "Confidence"
- **Result**: ✅ PASS / ❌ FAIL

### Test 5: Blocker Content Makes Sense ✓
- [ ] Blockers are relevant to blog state
- [ ] For completed blog: shows "Cannot transition from completed (terminal stage)"
- [ ] Severity colors correct (red=critical, amber=warning, blue=info)
- **Result**: ✅ PASS / ❌ FAIL

### Test 6: Refresh Button Works ✓
- [ ] Click Refresh button
- [ ] Loading state appears
- [ ] Response refreshes successfully
- **Result**: ✅ PASS / ❌ FAIL

### Test 7: Modal Closes ✓
- [ ] Click "Done" button
- [ ] Modal closes smoothly
- [ ] Can open modal again
- **Result**: ✅ PASS / ❌ FAIL

### Test 8: No Console Errors ✓
- [ ] Open F12 dev tools
- [ ] Check Console tab
- [ ] No red error messages
- **Result**: ✅ PASS / ❌ FAIL

---

## Social 

*[truncated — see source for full prompt]*