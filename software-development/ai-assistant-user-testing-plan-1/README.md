# AI ASSISTANT USER TESTING PLAN

> **Status**: Ready for validation  
**Date**: 2026-04-16  
**Objective**: Validate usefulness, clarity, and accuracy of AI assistant workflow guidance


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Assistant User Testing Plan

**Status**: Ready for validation  
**Date**: 2026-04-16  
**Objective**: Validate usefulness, clarity, and accuracy of AI assistant workflow guidance

---

## Testing Goals

1. **Usefulness**: Does the AI guidance help users complete workflows faster/correctly?
2. **Clarity**: Are blockers and next steps clearly explained?
3. **Accuracy**: Do blockers match actual workflow constraints?
4. **Coverage**: Does the assistant handle all common scenarios?
5. **Edge Cases**: Are error states and unusual workflows handled gracefully?

---

## Test Scenarios

### Blog Testing (12 scenarios)

#### Scenario 1: Draft in Progress (Expected: All blockers)
- **Setup**: Fresh blog, writer assigned, no content
- **Blog state**: `writer_status: in_progress`
- **User role**: writer
- **Expected blockers**:
  - Missing: title
  - Missing: google_doc_url
  - Missing: writer should be completed before publishing
- **Validation**: All 3 blockers detected correctly
- **User feedback**: Is guidance clear enough to unblock?

#### Scenario 2: Ready for Publishing (Expected: No blockers, proceed)
- **Setup**: Blog fully filled, writer_status: completed, publisher assigned
- **Blog state**: `writer_status: completed, publisher_status: pending_review`
- **User role**: publisher
- **Expected blockers**: None (workflow ready)
- **Expected next step**: "Mark publishing complete and set live URL"
- **Validation**: Blockers empty, next steps clear
- **User feedback**: Is the next action obvious?

#### Scenario 3: Missing Publisher Assignment (Expected: Critical blocker)
- **Setup**: Writer completed, but no publisher assigned
- **Blog state**: `writer_status: completed, publisher_id: null`
- **User role**: writer
- **Expected blockers**:
  - Critical: "Publisher must be assigned before publishing"
- **Validation**: Blocker severity correct, actionable
- **User feedback**: Does user know what to do next?

#### Scenario 4: Terminal State - Already Published (Expected: 

*[truncated — see source for full prompt]*