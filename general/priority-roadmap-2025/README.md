# Priority Roadmap 2025

> **Strategic Implementation Plan**  
**Start Date**: 2025-10-12  
**Timeline**: 18 weeks to full feature completion

---

## Quick Reference

| Phase |

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# NORAD VECTOR - Priority Roadmap 2025
**Strategic Implementation Plan**  
**Start Date**: 2025-10-12  
**Timeline**: 18 weeks to full feature completion

---

## Quick Reference

| Phase | Timeline | Focus | Status |
|-------|----------|-------|--------|
| **Phase 0** | Week 0 | Critical Hotfixes | 🔴 IN PROGRESS |
| **Phase 1** | Week 1-2 | Polish & UX | 📋 PLANNED |
| **Phase 2** | Week 3-5 | Accessibility & Performance | 📋 PLANNED |
| **Phase 3** | Week 6-9 | Strategic Depth | 📋 PLANNED |
| **Phase 4** | Week 10-14 | Content Expansion | 📋 PLANNED |
| **Phase 5** | Week 15-18 | Advanced Systems | 📋 PLANNED |

---

## Phase 0: Critical Hotfixes (Week 0)
**Duration**: 2-3 days  
**Goal**: Fix game-breaking issues and blockers

### Tasks
- [ ] **Fix Options Button** (2 hours)
  - Investigate z-index conflicts in Sheet component
  - Test pointer-events on all HUD layers
  - Verify click handlers work correctly
  - **Blocker**: Players cannot access settings

- [ ] **Fix City Lights Visibility** (4-6 hours)
  - **Option A**: Implement bloom post-processing (recommended)
  - **Option B**: Switch to instanced rendering with larger size
  - **Option C**: Add UI toggle for "Enhanced City Lights" mode
  - Test on multiple devices (desktop, mobile, tablet)
  - **User Complaint**: "Nei er fremdeles ikke lys" (repeated)

- [ ] **Quick Win: Action Confirmations** (3 hours)
  - Add toast notifications for all player actions
  - Color code: Green (success), Red (failure), Yellow (warning)
  - Include icons for action types
  - Test with all action types (launch, build, research, etc.)

### Exit Criteria
✅ All UI buttons functional  
✅ City lights clearly visible on globe  
✅ Every player action shows visual confirmation  
✅ No console errors on page load

---

## Phase 1: Polish & UX (Week 1-2)
**Duration**: 10-12 days  
**Goal**: Make game intuitive and visually polished

### Week 1: Information Architecture

#### Day 1-2: Progressive Disclosure System
- [ ] Implement "Begi

*[truncated — see source for full prompt]*