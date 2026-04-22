# IMPLEMENTATION GUIDE

> This guide provides practical implementation details for building robust, reliable toolsets for podcast production agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Robust Toolset Implementation Guide

This guide provides practical implementation details for building robust, reliable toolsets for podcast production agents.

## Implementation Strategy

### 1. **Core Implementation Principles**

```python
# Focus on practical, working implementations
class PracticalToolImplementation:
    """Base class for practical tool implementations."""

    def __init__(self, config=None):
        self.config = config or {}
        self.logger = self._setup_logging()
        self.metrics = self._initialize_metrics()

    def _setup_logging(self):
        """Setup comprehensive logging."""
        logger = logging.getLogger(self.__class__.__name__)
        logger.setLevel(logging.INFO)

        # File handler
        file_handler = logging.FileHandler(f'logs/{self.__class__.__name__}.log')
        file_handler.setFormatter(logging.Formatter(
            '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
        ))
        logger.addHandler(file_handler)

        return logger

    def _initialize_metrics(self):
        """Initialize performance metrics."""
        return {
            'execution_count': 0,
            'success_count': 0,
            'failure_count': 0,
            'avg_execution_time': 0,
            'last_execution_time': 0
        }
```

### 2. **Practical Error Handling**

```python
def _handle_errors_practically(self, error: Exception, context: Dict) -> Any:
    """Handle errors with practical recovery strategies."""

    error_type = type(error).__name__

    # Log the error with context
    self.logger.error(f"Error in {context.get('tool_name', 'unknown')}: {str(error)}")
    self.logger.debug(f"Error context: {context}")

    # Practical error handling strategies
    if isinstance(error, FileNotFoundError):
        return self._handle_missing_file(error, context)

    elif isinstance(error, ValueError):
        return self._handle_invalid_input(error, context)

    elif isinstance(error, MemoryError):
        ret

*[truncated — see source for full prompt]*