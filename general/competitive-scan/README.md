# Competitive Scan

> ## Purpose
Crawl a competitor's website/app, compare against our product, identify gaps and opportunities, and update vault intelligence files.

## Wh

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Competitive Scan

## Purpose
Crawl a competitor's website/app, compare against our product, identify gaps and opportunities, and update vault intelligence files.

## When to Use
- Scheduled cron (weekly recommended for active competitors)
- Before planning a new feature sprint (input for prioritization)
- When entering a new market or launching a new brand
- When a competitor ships a notable update or feature
- When Steve asks "where do we stand vs [competitor]?"

## Pre-Task Context Loading
1. Load our company profile from vault (e.g., [[companies/dirtsync.md]])
2. Load the competitor profile from vault (e.g., [[competitors/onx.md]])
3. Load previous scan results from [[intelligence/]] files
4. Load market gaps file: [[intelligence/market-gaps.md]]
5. Load SEO findings: [[intelligence/seo-findings.md]]

## Required Capabilities
- **Web access** -- must be able to crawl/scrape competitor websites
- **Analysis** -- must be able to compare features, pricing, UX systematically
- **Writing** -- must produce structured, actionable output

## Execution Steps

### Step 1: Crawl Competitor
- Visit key pages: homepage, pricing, features, blog, about, app store listing
- Document: features list, pricing tiers, UX quality, content strategy
- Note any new features or changes since last scan
- Capture key messaging and positioning language
- Check their app store reviews for common complaints (opportunities for us)

### Step 2: Diff Against Ours
- Feature-by-feature comparison table
- Pricing comparison
- UX/design quality comparison
- Content/SEO comparison
- Mobile app comparison (if applicable)

### Step 3: Identify Gaps (They Have, We Don't)
- List every feature/capability they offer that we lack
- Categorize by impact: Critical, High, Medium, Low
- Estimate implementation difficulty for each gap
- Note which gaps are table-stakes (must have) vs nice-to-have

### Step 4: Identify Advantages (We Have, They Don't)
- List every feature/capability we offer that they lac

*[truncated — see source for full prompt]*