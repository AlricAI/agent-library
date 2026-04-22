# TDD Workflow

> description: Test-Driven Development workflow for Project with Brain Garden integration globs: - "**/*.test.ts"

## Tags
`typescript` `sqlite`

## System Prompt
---
description: Test-Driven Development workflow for Project with Brain Garden integration
globs:
  - "**/*.test.ts"
  - "**/*.spec.ts"
  - "**/*.test.tsx"
  - "packages/core-*/**/*"
scopes:
  - testing
  - tdd
  - brain-garden
  - project
alwaysApply: true
---

# TDD Workflow

## 🎯 Core Principle

**AI-assisted development benefits most from E2E and integration tests that prove features actually work.**

Therefore, **E2E and Integration tests are MOST IMPORTANT** because they:
- ✅ Prove features actually work (AI-detectable signals)
- ✅ Prevent regressions when AI makes changes
- ✅ Validate the entire motivation system end-to-end
- ✅ Give confidence that "motivation metrics" are accurate

**Unit tests are supplementary** - they test isolated logic but don't prove the feature delivers value.

---

## 📐 Test Hierarchy (Priority Order)

### 1. **E2E Tests** (Highest Priority)
**Purpose:** Prove entire user workflows work in Electron app

**Test these flows:**
```typescript
// E2E: Motivation Dashboard displays correct metrics
describe('Motivation Dashboard E2E', () => {
  it('should display project quality score from database', async () => {
    // 1. Setup: Insert test project with quality_score = 94
    // 2. Launch Electron app
    // 3. Navigate to project
    // 4. Assert: Quality score 94/100 is visible
    // 5. Assert: Motivation message "ABSOLUTELY WORTH RESUMING" appears
  });

  it('should refresh metrics when project is rescanned', async () => {
    // Test that scanning updates UI in real-time
  });
});
```

**Tools:**
- Playwright for Electron
- Real SQLite database (test fixtures)
- Full Electron main + renderer interaction

### 2. **Integration Tests** (High Priority)
**Purpose:** Prove adapters → Core → Database flows work

**Test these integrations:**
```typescript
// Integration: Quality checker correctly calculates scores
describe('Quality Checker Integration', () => {
  it('should calculate correct quality score for project', async () => {
    

*[truncated — see source for full prompt]*