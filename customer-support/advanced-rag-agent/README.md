# Advanced Rag Agent

> """
Advanced RAG Agent that integrates multi-modal search capabilities.

This agent provides sophisticated retrieval-augmented generation with support

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Advanced RAG Agent that integrates multi-modal search capabilities.

This agent provides sophisticated retrieval-augmented generation with support
for multi-modal content, hybrid search, query expansion, and result re-ranking.
"""

import logging
import re
from typing import List, Dict, Any, Optional, Tuple
from dataclasses import dataclass
from datetime import datetime, timezone

# Import advanced RAG components
from search.hybrid_search_engine import HybridSearchEngine, SearchMode, RankingStrategy
from search.reranking_engine import EnsembleReRanker
from search.query_expansion import QueryExpansionEngine, ExpansionStrategy
from utils.multimodal_embedding_generator import MultiModalEmbeddingGenerator, EmbeddingStrategy
from utils.advanced_chunker import AdvancedChunker
from schemas.multimodal_schema import SearchQuery, SearchResult, MultiModalDocument, ContentType

# Import existing components
from utils.vector_db_client import VectorDBClient
from utils.token_optimizer import ContextTrimmer

logger = logging.getLogger(__name__)


@dataclass
class RAGResponse:
    """Response from the Advanced RAG Agent."""

    answer: str
    sources: List[SearchResult]
    confidence: float
    processing_time_ms: float
    metadata: Dict[str, Any]

    def to_dict(self) -> Dict[str, Any]:
        """Convert to dictionary for serialization."""
        return {
            "answer": self.answer,
            "sources": [
                {
                    "document_id": source.document.id,
                    "title": source.document.source_path,
                    "content_preview": source.matched_content,
                    "relevance_score": source.final_score,
                    "rank": source.rank,
                }
                for source in self.sources
            ],
            "confidence": self.confidence,
            "processing_time_ms": self.processing_time_ms,
            "metadata": self.metadata,
        }


class AdvancedRAGAgent:
    """
    Advanced

*[truncated — see source for full prompt]*