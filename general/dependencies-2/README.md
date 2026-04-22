# Dependencies

> ## Executive Summary
Minimal dependency configuration for a semantic search agent that connects to PostgreSQL with PGVector extension and uses OpenAI 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Semantic Search Agent - Dependency Configuration

## Executive Summary
Minimal dependency configuration for a semantic search agent that connects to PostgreSQL with PGVector extension and uses OpenAI for embeddings and LLM operations. Focus on simplicity with essential environment variables and core Python packages.

## Environment Variables Configuration

### Essential Environment Variables (.env.example)
```bash
# LLM Configuration (REQUIRED)
LLM_PROVIDER=openai
OPENAI_API_KEY=your-openai-api-key-here
LLM_MODEL=gpt-4o-mini
LLM_BASE_URL=https://api.openai.com/v1

# Database Configuration (REQUIRED)
DATABASE_URL=postgresql://username:password@localhost:5432/semantic_search_db

# Application Settings
APP_ENV=development
LOG_LEVEL=INFO
DEBUG=false
MAX_RETRIES=3
TIMEOUT_SECONDS=30

# Search Configuration
DEFAULT_SEARCH_LIMIT=10
MAX_SEARCH_LIMIT=50
SIMILARITY_THRESHOLD=0.7
EMBEDDING_MODEL=text-embedding-3-small
EMBEDDING_DIMENSIONS=1536

# Connection Pooling
DB_POOL_MIN_SIZE=5
DB_POOL_MAX_SIZE=20
DB_TIMEOUT=30
```

### Environment Variable Validation
- **OPENAI_API_KEY**: Required, must not be empty
- **DATABASE_URL**: Required, must be valid PostgreSQL connection string
- **LLM_MODEL**: Default to "gpt-4o-mini" if not specified
- **EMBEDDING_MODEL**: Default to "text-embedding-3-small"
- **DEFAULT_SEARCH_LIMIT**: Integer between 1-50, default 10

## Settings Configuration (settings.py)

### BaseSettings Class Structure
```python
class Settings(BaseSettings):
    """Application settings with environment variable support."""
    
    model_config = ConfigDict(
        env_file=".env",
        env_file_encoding="utf-8", 
        case_sensitive=False,
        extra="ignore"
    )
    
    # LLM Configuration
    llm_provider: str = Field(default="openai")
    openai_api_key: str = Field(..., description="OpenAI API key")
    llm_model: str = Field(default="gpt-4o-mini")
    llm_base_url: str = Field(default="https://api.openai.com/v1")
    
    # Database Configuration  

*[truncated — see source for full prompt]*