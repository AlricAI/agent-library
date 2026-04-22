# Power Steering Compaction Api

> Developer documentation for compaction handling in power-steering mode.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Power-Steering Compaction API Reference

Developer documentation for compaction handling in power-steering mode.

## Overview

The compaction handling system provides robust validation and diagnostics when conversation context is compacted (older messages removed due to token limits). This ensures critical session data is preserved and developers can integrate compaction awareness into their tools.

## Core Components

### CompactionValidator

Validates that critical session data was preserved during compaction.

**Module:** `power_steering_checker.py`

**Purpose:** Analyzes transcript to detect compaction events and validate data integrity.

**API:**

```python
class CompactionValidator:
    """Validates conversation compaction and data preservation.

    Detects when Claude's context window was compacted (old messages removed)
    and validates that critical session data was preserved. Provides actionable
    diagnostics for recovery when data is lost.

    Philosophy:
    - Fail-open: Default to "valid" when uncertain
    - Actionable: Provide specific recovery steps, not just "data lost"
    - Fast: Validation completes in < 100ms for typical transcripts

    Examples:
        Basic validation:
        >>> validator = CompactionValidator()
        >>> result = validator.validate(transcript, session_id)
        >>> if not result.passed:
        ...     print(f"Warnings: {result.warnings}")
        ...     print(f"Recovery: {result.recovery_steps}")

        Check specific data types:
        >>> result = validator.validate_todos(transcript)
        >>> result.passed
        True

        Get compaction metrics:
        >>> ctx = validator.get_compaction_context(transcript)
        >>> print(f"Turn: {ctx.turn_at_compaction}")
        >>> print(f"Messages removed: {ctx.messages_removed}")
    """

    def validate(
        self,
        transcript: list[dict],
        session_id: str
    ) -> ValidationResult:
        """Validate entire transcript for compaction 

*[truncated — see source for full prompt]*