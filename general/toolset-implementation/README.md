# TOOLSET IMPLEMENTATION

> ## Overview

This guide provides comprehensive implementation details for creating robust, reliable toolsets for the podcast production system. It foc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Toolset Implementation Guide

## Overview

This guide provides comprehensive implementation details for creating robust, reliable toolsets for the podcast production system. It focuses on practical implementation patterns and best practices for building tools that work consistently and provide informative feedback.

## Core Toolset Architecture

### 1. Base Tool Class

```python
class BaseTool:
    """
    Base class for all podcast production tools
    """

    def __init__(self, name: str, description: str, config: dict = None):
        """
        Initialize the tool with name, description, and configuration

        Args:
            name: Tool name
            description: Tool description
            config: Configuration dictionary
        """
        self.name = name
        self.description = description
        self.config = config or self._load_default_config()
        self.logger = self._setup_logger()
        self.metrics = self._setup_metrics()
        self.error_handler = ComprehensiveErrorHandler(name)
        self.quality_assessor = QualityAssuranceFramework(name)
        self.fallback_manager = FallbackStrategyFramework(name)

    def _load_default_config(self) -> dict:
        """Load default configuration"""
        return {
            "timeout": 300,
            "max_retries": 3,
            "retry_delay": 5,
            "resource_limits": {
                "memory": "2GB",
                "cpu": "1 core"
            },
            "quality_thresholds": {
                "min_completeness": 0.8,
                "min_accuracy": 0.85,
                "min_quality": 0.7
            }
        }

    def _setup_logger(self) -> Logger:
        """Setup comprehensive logging"""
        logger = Logger(f"tool.{self.name}")
        logger.add_handler(FileHandler(f"logs/{self.name}.log"))
        logger.add_handler(ConsoleHandler())
        logger.set_level(LOG_LEVEL_INFO)
        return logger

    def _setup_metrics(self) -> MetricsCollector:
       

*[truncated — see source for full prompt]*