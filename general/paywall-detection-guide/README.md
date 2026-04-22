# PAYWALL DETECTION GUIDE

> ### Reference Source
This section is based on detailed insights from [RemovePaywalls.com](https://removepaywalls.com/blog/) and the magnolia1234 bypas

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Site-Specific Paywall Detection Insights from RemovePaywalls.com

### Reference Source
This section is based on detailed insights from [RemovePaywalls.com](https://removepaywalls.com/blog/) and the magnolia1234 bypass-paywalls-clean project at [GitFlic](https://gitflic.ru/project/magnolia1234/bypass-paywalls-clean-filters). All techniques and signals are derived from comprehensive analysis of these sources.

### Technical Implementation Methods Identified

#### User-Agent Manipulation Strategies
- **Googlebot Spoofing**: `Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)`
- **Archive Crawler Spoofing**: Wayback Machine, Archive.today user agents
- **Search Engine Crawlers**: Bing, Yahoo, DuckDuckBot user agents

#### Header Manipulation Techniques
- **Referrer Bypass**: Setting referrer to Google Search, Facebook, Twitter
- **Origin Header Modification**: Spoofing origin domain
- **Cookie Manipulation**: Clearing subscriber cookies, resetting article counters

#### DOM Manipulation Strategies
- **Overlay Removal**: Removing paywall modals, subscription overlays
- **Content Unhiding**: Revealing hidden article text, images
- **Script Blocking**: Preventing paywall enforcement JavaScript

#### Archive/Cache Retrieval Methods
- **Archive.org Integration**: Automatic fallback to Wayback Machine
- **12ft.io/1ft.io**: Ladder-based bypass services
- **Google Cache**: Cached page retrieval strategies

### Key Detection Signals

#### DOM Element Indicators
- **Overlay Elements**: Look for `.paywall-overlay`, `.subscription-modal`, `.premium-content-blocker`
- **Banner Messages**: Detect `.subscribe-banner`, `.paywall-message`, `.subscription-required`
- **Content Blockers**: Identify `.article-blocker`, `.content-gate`, `.metered-paywall`

#### URL Pattern Matching
- **Subscription Paths**: `/subscribe`, `/premium`, `/membership`, `/subscription`
- **Paywall Parameters**: `?paywall=true`, `?metered=1`, `?limit=exceeded`
- **Article Limits**: `/artic

*[truncated — see source for full prompt]*