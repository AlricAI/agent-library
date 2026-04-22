# PR SPLITTING RECOMMENDATIONS

> ## Current State Analysis

The current feature branch contains **78 commits** from the past week, indicating a very large PR that encompasses multiple

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PR Splitting Recommendations

## Current State Analysis

The current feature branch contains **78 commits** from the past week, indicating a very large PR that encompasses multiple unrelated features. This makes code review difficult and increases the risk of merge conflicts.

## Recommended Split Strategy

### PR 1: Performance Optimization Bundle
**Commits to include:**
- `6987b69` - fix: resolve all CI linting and import errors
- `4bcdd95` - Fix ESLint warnings and Playwright fixture issues
- Performance analysis script updates
- Frontend code splitting implementation

**Focus:** CI fixes, linting, and bundle optimization

### PR 2: Database Schema & Backend Testing
**Commits to include:**
- `a100657` - Fix database schema - remove foreign key constraint
- `1e389da` - Apply critical CI fixes for database schema and ESLint issues

**Focus:** Database improvements and backend test fixes

### PR 3: Frontend Component Updates
**Commits to include:**
- `93efc96` - Fix duplicate variable declarations in BehaviorEditor.tsx
- Component updates in BehaviorEditor, RecipeBuilder, etc.

**Focus:** Frontend component fixes and improvements

### PR 4: Documentation & Testing Infrastructure
**Commits to include:**
- `870f766` - Implement comprehensive E2E testing, performance optimization, and documentation updates
- Documentation improvements
- E2E test setup

**Focus:** Documentation and testing infrastructure

## Benefits of Splitting

1. **Easier Code Review:** Smaller, focused PRs are easier to review thoroughly
2. **Faster Merge:** Less contentious, can be merged independently
3. **Reduced Risk:** Isolated changes minimize potential for breaking unrelated features
4. **Better Tracking:** Each PR can be linked to specific issues
5. **Parallel Development:** Different PRs can be worked on simultaneously

## Implementation Strategy

1. Create feature branches from current branch:
   ```bash
   git checkout -b feature/performance-optimizations
   git checkout -b feature/dat

*[truncated — see source for full prompt]*