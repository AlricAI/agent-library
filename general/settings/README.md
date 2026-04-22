# Settings

> """Settings configuration for Semantic Search Agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Settings configuration for Semantic Search Agent."""


from dotenv import load_dotenv
from pydantic import ConfigDict, Field
from pydantic_settings import BaseSettings

# Load environment variables from .env file
load_dotenv()


class Settings(BaseSettings):
    """Application settings with environment variable support."""

    model_config = ConfigDict(
        env_file=".env",
        env_file_encoding="utf-8",
        case_sensitive=False,
        extra="ignore"
    )

    # Database Configuration
    database_url: str = Field(
        ...,
        description="PostgreSQL connection URL with PGVector extension"
    )

    # LLM Configuration (OpenAI-compatible)
    llm_provider: str = Field(
        default="openai",
        description="LLM provider (openai, anthropic, gemini, ollama, etc.)"
    )

    llm_api_key: str = Field(
        ...,
        description="API key for the LLM provider"
    )

    llm_model: str = Field(
        default="gpt-4o-mini",
        description="Model to use for search and summarization"
    )

    llm_base_url: str | None = Field(
        default="https://api.openai.com/v1",
        description="Base URL for the LLM API (for OpenAI-compatible providers)"
    )

    # Search Configuration
    default_match_count: int = Field(
        default=10,
        description="Default number of search results to return"
    )

    max_match_count: int = Field(
        default=50,
        description="Maximum number of search results allowed"
    )

    default_text_weight: float = Field(
        default=0.3,
        description="Default text weight for hybrid search (0-1)"
    )

    # Connection Pool Configuration
    db_pool_min_size: int = Field(
        default=10,
        description="Minimum database connection pool size"
    )

    db_pool_max_size: int = Field(
        default=20,
        description="Maximum database connection pool size"
    )

    # Embedding Configuration
    embedding_model: str = Field(
        default="text-

*[truncated — see source for full prompt]*