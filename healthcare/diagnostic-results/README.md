# DIAGNOSTIC RESULTS

> ## Summary

**Issue**: Claude's candidate selection returning 0 candidates even though Apify returns 10 LinkedIn candidates.

**Root Cause**: Likely a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Recruiting Agent Diagnostic Results

## Summary

**Issue**: Claude's candidate selection returning 0 candidates even though Apify returns 10 LinkedIn candidates.

**Root Cause**: Likely a data format mismatch between what Apify returns and what Claude expects.

**Status**: ✅ Core selection logic is WORKING. Issue is with data transformation.

---

## Key Findings

### 1. Claude Selection Logic is Working ✅

I created a mock test (`sms-bot/scripts/test-recruit-selection-mock.js`) with well-formatted candidate data. Results:

- ✅ Claude successfully selected all 10 candidates
- ✅ JSON parsing worked correctly (handles markdown code blocks)
- ✅ Match reasons were relevant and well-written
- ✅ Output format matches expectations

**Conclusion**: The AI selection logic and prompt are working correctly when given proper data.

### 2. LinkedIn Cookie Issue 🔄

When testing with real Apify calls:
- ❌ LinkedIn cookies are currently expired
- Error: "Failed to authorize with linkedin. Please retry with new cookies"

**Action Needed**: Update `LINKEDIN_COOKIE` in `.env.local` with fresh cookies from Cookie-Editor Chrome extension.

### 3. Data Format Investigation 🔍

**Enhanced Logging Added** (in `apify-client.ts:177-200` and `index.ts:315-321`):

The code now logs:
1. Raw Apify result format (first item)
2. Available field names in raw data
3. Transformed candidate data
4. Sample of what Claude receives

This will reveal if Apify returns different field names than expected.

---

## Current Code Structure

### Apify Client (`apify-client.ts`)

```typescript
// Transformation tries multiple field names:
{
  name: result.name || result.fullName || 'Unknown',
  title: result.title || result.headline,
  company: result.company || result.companyName,
  linkedinUrl: result.url || result.profileUrl || result.linkedinUrl,
  summary: result.summary || result.about,
  // ...
}
```

**Problem**: If Apify uses different field names, candidates will have:
- name: "Unknown"
- title: und

*[truncated — see source for full prompt]*