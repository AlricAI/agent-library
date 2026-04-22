# CURRENT TASKS

> **Assigned:** 2026-03-28 20:21 UTC
**Priority:** HIGH
**Status:** ACTIVE

---

## Task: Lead Enrichment - Website & Email Research

### Objective
Enri

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CURRENT_TASKS.md - Dusty
**Assigned:** 2026-03-28 20:21 UTC
**Priority:** HIGH
**Status:** ACTIVE

---

## Task: Lead Enrichment - Website & Email Research

### Objective
Enrich existing lead database with website URLs and email addresses for all businesses across 58 counties in CA, OR, WA, TX, AZ, NM.

### Background
We have lead files for 58+ counties but they're missing critical contact information:
- ❌ Website URLs
- ❌ Email addresses
- ❌ Social media profiles (bonus)

### Scope

**Files to Process:**
Located in: `/root/.openclaw/workspace/aocros/performance_supply_depot/leads/`

**Priority States (in order):**
1. **California** - 58 counties (CA_* files)
2. **Oregon** - 36 counties (OR_*, Baker_* files)
3. **Washington** - 39 counties (WA_*, *_WA_* files)
4. **Texas** - 254 counties (TX_* files)
5. **Arizona** - 15 counties (AZ_* files) - NEW
6. **New Mexico** - 33 counties (NM_* files) - NEW

**Key Files:**
- `CA_All_58_Counties_Leads.xlsx` (master file - start here)
- `ALL_STATES_Leads.xlsx` (consolidated)
- Individual county files

### Process

For each business in the lead files:

1. **Extract Business Info**
   - Business Name
   - Address
   - Phone Number (if available)
   - County/State

2. **Research Website**
   - Google search: "Business Name + City + website"
   - Check Yelp, Yellow Pages, Chamber of Commerce
   - Verify URL is active (HTTP 200 check)

3. **Find Email Address**
   - Check website "Contact" or "About" pages
   - Look for info@, contact@, sales@ patterns
   - Use Hunter.io or similar tools (if API available)
   - Check LinkedIn company pages

4. **Update Lead Sheet**
   - Add "Website" column
   - Add "Email" column
   - Add "Email_Source" column (where found)
   - Add "Last_Updated" timestamp

5. **Mark Status**
   - ✅ Complete: Website + Email found
   - ⚠️ Partial: Website OR Email found
   - ❌ No Contact: Neither found

### Output Format

Update each Excel file with new columns:
```
Business_Name | Address | Phone | Website | Em

*[truncated — see source for full prompt]*