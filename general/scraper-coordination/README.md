# Scraper Coordination

> ## Performance Supply Depot LLC

---

## Scraper Task Assignments

### R2-D2 - Systems/Lead Scraping
**Status:** 🟢 ACTIVE | **Priority:** HIGH

**Tas

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scraper Coordination - Lead Generation
## Performance Supply Depot LLC

---

## Scraper Task Assignments

### R2-D2 - Systems/Lead Scraping
**Status:** 🟢 ACTIVE | **Priority:** HIGH

**Tasks:**
1. Scrape business directories (Yellow Pages, Yelp, BBB)
2. Extract contact info for decision-makers
3. Filter by company size and industry
4. Validate email addresses
5. Deduplicate against existing CRM

**Output Format:**
```json
{
  "company_name": "string",
  "industry": "string",
  "employee_count": "range",
  "contact_name": "string",
  "title": "string",
  "email": "string",
  "phone": "string",
  "address": "string",
  "website": "string",
  "tier": "Starter|Professional|Corporate|Enterprise"
}
```

**Target Volume:** 5,000 leads/week
**Delivery:** Daily CSV upload to `/sales/leads/r2d2/`

---

### TX Scraper - Texas Leads
**Status:** 🟢 ACTIVE | **Priority:** HIGH

**Geographic Focus:** Texas (All major metros)
- Houston
- Dallas-Fort Worth
- San Antonio
- Austin
- El Paso

**Industry Targets:**
- Restaurants & Food Service
- Retail Stores
- Healthcare Clinics
- Auto Repair Shops
- Salons & Spas

**Tasks:**
1. Scrape Texas Secretary of State business registry
2. Target businesses 2-5 years old (growth phase)
3. Extract owner/operator contact info
4. Cross-reference with LinkedIn

**Target Volume:** 2,000 leads/week
**Delivery:** Weekly batch to `/sales/leads/tx/`

---

### AZ Scraper - Arizona Leads
**Status:** 🟢 ACTIVE | **Priority:** HIGH

**Geographic Focus:** Arizona
- Phoenix
- Tucson
- Mesa
- Scottsdale
- Tempe

**Industry Targets:**
- Tourism & Hospitality
- Real Estate Agencies
- Construction Companies
- Medical Practices
- Legal Firms

**Tasks:**
1. Scrape Arizona Corporation Commission database
2. Focus on LLCs and S-Corps
3. Extract registered agent info
4. Find direct business phone numbers

**Target Volume:** 1,500 leads/week
**Delivery:** Weekly batch to `/sales/leads/az/`

---

### CA SOS Scraper - California Business Leads
**Status:** 🟢 ACTIVE | 

*[truncated — see source for full prompt]*