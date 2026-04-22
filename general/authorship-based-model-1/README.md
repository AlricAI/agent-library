# AUTHORSHIP BASED MODEL

> ## Overview

We've redesigned the author system to properly handle author deduplication using fuzzy matching.

## The Problem with the Old System

**O

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Authorship-Based Author Model

## Overview

We've redesigned the author system to properly handle author deduplication using fuzzy matching.

## The Problem with the Old System

**Old approach:**
```cypher
MERGE (a:Author {name: $name})  // One node per unique name
```

**Issues:**
- "John Doe" at Stanford + "John Doe" at MIT = same Author node ❌
- Can't distinguish between multiple people with same name
- 292K Author nodes for 845K authorships (incorrect merging)

## The New System

### 1. Authorship-Based Author Nodes

**New approach:**
```cypher
CREATE (a:Author)  // One node per authorship
SET a.kochi_author_id = 'KA_' + randomUUID()
```

**Result:**
- Each paper appearance creates a NEW Author node with unique KID
- 845K Author nodes for 845K authorships (1:1 mapping)
- "John Doe" appears on 100 papers = 100 Author nodes with 100 different KIDs

### 2. Canonical KID System

**Fields added to Author nodes:**
- `canonical_kid`: Points to the "canonical" author (the real person)
- `canonical_confidence`: Match confidence (0-100)
- `is_canonical`: True if this node IS the canonical one
- `needs_review`: True if match is uncertain (60-79% confidence)

**Example:**
```
Author node 1: John Doe (Stanford)
- kochi_author_id: KA_abc123
- canonical_kid: KA_abc123  (points to self)
- is_canonical: true

Author node 2: John Doe (Stanford)
- kochi_author_id: KA_def456
- canonical_kid: KA_abc123  (points to node 1)
- canonical_confidence: 95

Author node 3: John Doe (MIT)
- kochi_author_id: KA_ghi789
- canonical_kid: KA_ghi789  (different person, points to self)
- is_canonical: true
```

### 3. Fuzzy Matching Logic

**Three signals (0-100 score):**
1. **Co-author overlap** (0-50 pts): Same person publishes with same collaborators
2. **Name + affiliation** (0-30 pts): Exact name + institution match
3. **Research area** (0-20 pts): Shared paper categories

**Decision thresholds:**
- **≥80%**: Assign canonical_kid to existing canonical author
- **60-79%**: Assign canonical_kid

*[truncated — see source for full prompt]*