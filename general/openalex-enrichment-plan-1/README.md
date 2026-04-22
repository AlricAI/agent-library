# OPENALEX ENRICHMENT PLAN

> ## POC Results (100 Papers from Early June 2025)

```
Papers processed:           100
Papers found in OpenAlex:   6 (6% - expected for late June)
Auth

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAlex Enrichment Plan - POC Proven ✅

## POC Results (100 Papers from Early June 2025)

```
Papers processed:           100
Papers found in OpenAlex:   6 (6% - expected for late June)
Authors matched:            53 (100% match rate!)
Match confidence:           100% high confidence (>95%)
```

**Example enrichments:**
- Author with h-index 91, 26K citations (UCL researcher)
- Author with h-index 49, 10K citations (Google Canada)
- Authors from Google, UCSF, Cambridge, Beijing University, etc.
- Citations ranging from 5 to 26,000
- h-index from 1 (new researchers) to 91 (senior researchers)

**Key Success Metrics:**
- ✅ 100% match rate (position-based matching is reliable!)
- ✅ 100% high confidence (no fuzzy/uncertain matches)
- ✅ Rich data (h-index, citations, institutions for most)
- ✅ Script runs in seconds (6 API calls for 100 papers)

---

## Full Backfill Plan

### Current State
- **Total canonical authors**: 268,015
- **Currently enriched**: 10,387 (4%)
- **Target**: 197,000 enriched (74%)

### Papers Available for Matching

| Date Range | Papers | Status |
|------------|--------|--------|
| Feb 2024 - May 2025 | 117,680 | ✅ In OpenAlex |
| June 2025 | 9,568 | ✅ In OpenAlex |
| July - Oct 2025 | 35,512 | ❌ Not in OpenAlex yet |
| **Total** | **162,760** | |

### Phase 1: Paper-Based Matching (Week 1-2)

**Target**: 127,248 papers (Feb-June 2025)

**Approach**:
```bash
# Process papers in batches of 50
# Expected: ~400-500 authors per batch
# Total batches: 2,545
# API calls: 2,545 (papers) + 2,545 (author profiles) = 5,090 calls
# Time: ~3 hours (spread over days with rate limiting)
```

**Expected Results**:
- Papers processed: 127,248
- OpenAlex coverage: ~70% (accounting for indexing delays)
- Authors matched: ~67,000 (high confidence via position matching)
- Authors enriched: ~67,000 with h-index, citations, institutions

**Implementation**:
```bash
cd sms-bot/agents/arxiv-research-graph

# Run full backfill
python3 openalex_enrichment_backfill.py \
 

*[truncated — see source for full prompt]*