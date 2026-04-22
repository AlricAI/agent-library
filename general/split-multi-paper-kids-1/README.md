# Split Multi Paper Kids

> #!/usr/bin/env python3
"""
Split multi-paper KIDs into individual authorship KIDs.

Some Author nodes have KIDs that link to multiple papers. This sho

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Split multi-paper KIDs into individual authorship KIDs.

Some Author nodes have KIDs that link to multiple papers. This should not happen
in the authorship-based model - each authorship should get its own unique KID.

This script:
1. Finds all Author nodes where KID links to >1 paper
2. For each paper they authored, creates a new Author node with unique KID
3. Preserves all metadata and relationships
4. Deletes the old multi-paper KID

Usage:
    python3 split_multi_paper_kids.py --dry-run  # See what would happen
    python3 split_multi_paper_kids.py           # Run the split
"""

import argparse
import os
import sys
from datetime import datetime
from neo4j import GraphDatabase

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")


def count_multi_paper_kids(driver):
    """Count how many KIDs link to multiple papers."""
    with driver.session(database=NEO4J_DATABASE) as session:
        result = session.run("""
            MATCH (a:Author)-[r:AUTHORED]->(p:Paper)
            WITH a, count(p) as paper_count
            WHERE paper_count > 1
            RETURN count(a) as multi_paper_kids
        """)
        return result.single()['multi_paper_kids']


def get_multi_paper_author_kids(driver, limit=None):
    """Get KIDs of authors that link to multiple papers."""
    with driver.session(database=NEO4J_DATABASE) as session:
        query = """
            MATCH (a:Author)-[r:AUTHORED]->(p:Paper)
            WITH a, count(p) as paper_count
            WHERE paper_count > 1
            RETURN a.kochi_author_id as kid
            ORDER BY kid
        """
        if limit:
            query += f" LIMIT {limit}"

        result = session.run(query)
        return [record['kid'] for record in result]


def split_multi_paper_kids(driver, dry_run=False):
    """
    Split multi-paper KIDs into indivi

*[truncated — see source for full prompt]*