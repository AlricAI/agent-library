# Neo4j Tools

> #!/usr/bin/env python3
"""
Neo4j Tools for KG Query Agent

Provides safe Neo4j query functions with automatic data quality filtering.
"""

import os
i

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Neo4j Tools for KG Query Agent

Provides safe Neo4j query functions with automatic data quality filtering.
"""

import os
import sys
import json
import re
from typing import List, Dict, Any, Optional
from neo4j import GraphDatabase

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")


class Neo4jTools:
    """Neo4j query tools with data quality awareness."""

    def __init__(self):
        if not all([NEO4J_URI, NEO4J_USERNAME, NEO4J_PASSWORD]):
            raise ValueError("Missing Neo4j environment variables")

        self.driver = GraphDatabase.driver(
            NEO4J_URI, auth=(NEO4J_USERNAME, NEO4J_PASSWORD)
        )
        self.database = NEO4J_DATABASE
        self._clean_data_status = None

    def close(self):
        """Close Neo4j driver."""
        self.driver.close()

    def execute_cypher(self, query: str, params: Optional[Dict] = None) -> List[Dict[str, Any]]:
        """
        Execute a Cypher query and return results.

        Args:
            query: Cypher query string
            params: Optional query parameters

        Returns:
            List of result records as dictionaries
        """
        with self.driver.session(database=self.database) as session:
            result = session.run(query, parameters=params or {})
            records = []
            for record in result:
                # Convert record to dict
                records.append(dict(record))
            return records

    def get_clean_data_status(self) -> Dict[str, Any]:
        """
        Get current clean data boundaries.

        Returns dict with:
            - clean_start_date: Earliest date with clean author data
            - clean_end_date: Latest date with clean author data
            - clean_papers: Number of papers with clean authors
            - total_papers: Total papers 

*[truncated — see source for full prompt]*