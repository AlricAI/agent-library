# Test Memory Export

> """Tests for memory export/import functionality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for memory export/import functionality.

Philosophy:
- Test roundtrip: export -> import -> verify identical facts
- Test JSON format human-readability
- Test merge mode (import into existing KB)
- Test CLI-level export/import commands
- Use temporary directories for DB isolation
"""

from __future__ import annotations

import json
import shutil
import tempfile
from pathlib import Path

import pytest

from amplihack.agents.goal_seeking.hierarchical_memory import (
    HierarchicalMemory,
)
from amplihack.agents.goal_seeking.memory_export import export_memory, import_memory


@pytest.fixture
def temp_dir():
    """Create a temporary directory for test databases and exports."""
    d = Path(tempfile.mkdtemp())
    yield d
    if d.exists():
        shutil.rmtree(d)


@pytest.fixture
def populated_memory(temp_dir):
    """Create a HierarchicalMemory with some test data."""
    mem = HierarchicalMemory(agent_name="export_test", db_path=temp_dir / "source_db")

    # Store an episode
    ep_id = mem.store_episode(
        content="Article about marine biology and coral reefs.",
        source_label="Wikipedia: Coral Reefs",
    )

    # Store semantic nodes derived from the episode
    mem.store_knowledge(
        content="Coral reefs are underwater ecosystems built by colonies of tiny animals.",
        concept="coral reefs",
        confidence=0.95,
        source_id=ep_id,
        tags=["biology", "marine"],
    )
    mem.store_knowledge(
        content="The Great Barrier Reef is the largest coral reef system in the world.",
        concept="great barrier reef",
        confidence=0.9,
        source_id=ep_id,
        tags=["geography", "marine"],
    )
    mem.store_knowledge(
        content="Coral bleaching occurs when water temperatures rise abnormally.",
        concept="coral bleaching",
        confidence=0.85,
        tags=["ecology", "climate"],
    )

    yield mem
    mem.close()


class TestExportToJson:
    """Tests for HierarchicalMemory.export_

*[truncated — see source for full prompt]*