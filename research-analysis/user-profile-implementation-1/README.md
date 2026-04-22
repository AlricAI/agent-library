# USER PROFILE IMPLEMENTATION

> ## Overview

Implemented a global user profile system that extracts and persists user information across all sessions using LLM-based analysis with a 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Profile Memory - Implementation Summary

## Overview

Implemented a global user profile system that extracts and persists user information across all sessions using LLM-based analysis with a configurable, extensible schema.

## Key Design Decisions

### 1. **Single Global Profile** (Not Session-Based)
- Only ONE row in the `user_profiles` table
- Profile is shared across all sessions
- Suitable for single-user systems
- No `session_id` foreign key needed

### 2. **Schema Extensibility**
- Base schema defined in `data/configs/profile_schema.json`
- LLM can add custom fields beyond base schema
- No strict validation - allows organic growth
- Supports patch-mode updates (merge new data with existing)

### 3. **No Profile Confidence Decay**
- Profile data does not lose relevance over time
- Simple versioning with incrementing version numbers
- Tracks `last_updated_message_id` for incremental updates

## Components Modified/Created

### 1. **Profile Schema** (`data/configs/profile_schema.json`)
```json
{
  "name": "User Profile",
  "parameters": {
    "properties": {
      "user_name": "User's preferred name",
      "age": "User's age",
      "interests": "Array of interests/hobbies",
      "home": "Location description",
      "occupation": "Job/profession",
      "expertise_areas": "Areas of knowledge",
      "goals": "User's objectives",
      "conversation_preferences": "Communication style preferences",
      "technical_context": {
        "programming_languages": [],
        "tools": [],
        "operating_system": ""
      },
      "learning_style": "How user prefers to learn"
    }
  }
}
```

### 2. **Database Table** (`user_profiles`)
```sql
CREATE TABLE user_profiles (
    id INT AUTO_INCREMENT PRIMARY KEY,
    profile_data JSON NOT NULL,
    version INT DEFAULT 1,
    last_updated_message_id INT,
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    INDEX idx_updated_at (updated_at)
)
```

### 3. **CRUD Operations** (`database/crud.py`)
- `get_user_pr

*[truncated — see source for full prompt]*