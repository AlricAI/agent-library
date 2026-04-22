# Curate With Agent

> #!/usr/bin/env python3
"""
Stage 2: AI-Powered Curation with Graph Insights

Uses Claude Agent SDK to generate intelligent reports leveraging Neo4j gr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Stage 2: AI-Powered Curation with Graph Insights

Uses Claude Agent SDK to generate intelligent reports leveraging Neo4j graph data.

This is the "crown jewel" - combining graph database insights about authors,
collaborations, and trends with AI-powered paper curation.
"""

import argparse
import asyncio
import json
import os
import sys
import time
from datetime import date, datetime, timedelta
from pathlib import Path
from typing import List, Dict, Any

from neo4j import GraphDatabase
from claude_agent_sdk import ClaudeAgentOptions, query

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")


def build_graph_context(driver, target_date: date) -> Dict[str, Any]:
    """
    Query Neo4j to build rich context for the AI agent.

    Returns graph insights to be injected into the AI prompt.
    """
    with driver.session(database=NEO4J_DATABASE) as session:
        # Trending topics (1.3x+ growth week-over-week)
        trending_query = """
        MATCH (p:Paper)-[:IN_CATEGORY]->(c:Category)
        WHERE p.published_date >= date($start_date)
          AND p.published_date <= date($end_date)
        WITH c.name as category,
             count(CASE
               WHEN p.published_date >= date($recent_start)
               THEN 1 END) as recent_count,
             count(CASE
               WHEN p.published_date < date($recent_start)
               THEN 1 END) as earlier_count
        WHERE recent_count >= 10
        WITH category, recent_count, earlier_count,
             (recent_count * 1.0 / CASE WHEN earlier_count > 0 THEN earlier_count ELSE 1 END) as growth
        WHERE growth >= 1.3
        RETURN category, recent_count, earlier_count, round(growth, 2) as growth
        ORDER BY growth DESC, recent_count DESC
        LIMIT 5
        """

        start_date = (target_date - timedelta(days=14)

*[truncated — see source for full prompt]*