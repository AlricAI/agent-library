# Test Flat Adapter

> """Tests for FlatRetrieverAdapter backward compatibility.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for FlatRetrieverAdapter backward compatibility.

Philosophy:
- Verify same interface as MemoryRetriever
- Test store_fact, search, get_all_facts, get_statistics
- Use temporary directories for isolation
"""

import shutil
import tempfile
from pathlib import Path

import pytest

from amplihack.agents.goal_seeking.flat_retriever_adapter import FlatRetrieverAdapter


class TestFlatRetrieverAdapter:
    """Tests for FlatRetrieverAdapter."""

    @pytest.fixture
    def temp_db(self):
        """Create temporary directory for Kuzu database."""
        temp_dir = Path(tempfile.mkdtemp())
        yield temp_dir
        if temp_dir.exists():
            shutil.rmtree(temp_dir)

    @pytest.fixture
    def adapter(self, temp_db):
        """Create FlatRetrieverAdapter with temp storage."""
        adp = FlatRetrieverAdapter(agent_name="test_adapter", db_path=temp_db / "adapter_db")
        yield adp
        adp.close()

    def test_store_fact_returns_id(self, adapter):
        """store_fact should return a valid ID string."""
        fact_id = adapter.store_fact(
            context="Photosynthesis",
            fact="Plants convert light to energy",
            confidence=0.9,
            tags=["biology"],
        )
        assert fact_id is not None
        assert isinstance(fact_id, str)
        assert len(fact_id) > 0

    def test_store_fact_validation(self, adapter):
        """store_fact should validate inputs like MemoryRetriever."""
        with pytest.raises(ValueError, match="context cannot be empty"):
            adapter.store_fact(context="", fact="Some fact")

        with pytest.raises(ValueError, match="fact cannot be empty"):
            adapter.store_fact(context="Some context", fact="")

        with pytest.raises(ValueError, match="confidence must be between"):
            adapter.store_fact(context="Context", fact="Fact", confidence=1.5)

    def test_search_returns_dict_format(self, adapter):
        """search should return dicts with MemoryR

*[truncated — see source for full prompt]*