# USER PROFILE QUICKSTART

> ## Quick Start

### 1. Initialize Database

```python
from agentlab.database.crud import initialize_database
initialize_database()  # Creates user_pro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Profile Memory System

## Quick Start

### 1. Initialize Database

```python
from agentlab.database.crud import initialize_database
initialize_database()  # Creates user_profiles table
```

### 2. Extract Profile from Conversation

```python
from agentlab.agents.memory_processor import LongTermMemoryProcessor
from agentlab.config.memory_config import MemoryConfig

# Initialize processor
config = MemoryConfig.from_env()
processor = LongTermMemoryProcessor(config=config)

# Extract and store profile from a session
profile = processor.extract_and_store_profile(
    session_id="user-session-123",
    incremental=True  # Only process new messages
)

print(profile)
# {
#   "user_name": "Maria",
#   "age": 28,
#   "occupation": "Data Scientist",
#   "interests": ["Machine Learning", "NLP"],
#   ...
# }
```

### 3. Retrieve Stored Profile

```python
from agentlab.database.crud import get_user_profile

profile_row = get_user_profile()
print(profile_row['profile_data'])
```

### 4. Use Profile in Memory Context

The profile is automatically loaded when building memory context:

```python
from agentlab.core.memory_service import IntegratedMemoryService

service = IntegratedMemoryService()
context = service.get_context(
    session_id="user-session-123",
    memory_config={"enable_profile": True}
)

print(context.user_profile)
```

## API Endpoints

### Get Current Profile
```bash
GET /api/memory/profile
```

Response:
```json
{
  "profile_data": {
    "user_name": "Maria",
    "age": 28,
    "occupation": "Data Scientist",
    "interests": ["ML", "NLP"],
    "expertise_areas": ["Python", "PyTorch"]
  },
  "version": 2,
  "last_updated": "2025-12-22T10:30:00",
  "created_at": "2025-12-22T08:00:00"
}
```

### Extract Profile from Session
```bash
POST /api/memory/profile/extract
Content-Type: application/json

{
  "session_id": "user-session-123",
  "incremental": true
}
```

Response:
```json
{
  "profile_data": {...},
  "status": "updated"
}
```

### Delete Profile
```ba

*[truncated — see source for full prompt]*