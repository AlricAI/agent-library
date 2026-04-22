# TOOLSET DESIGN GUIDE

> ## Design Principles

### 1. Usability First

**"Tools should be intuitive and easy to use, even for non-technical users"**

- **Clear, descriptive na

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Podcast Production Toolset Design Guide

## Design Principles

### 1. Usability First

**"Tools should be intuitive and easy to use, even for non-technical users"**

- **Clear, descriptive names** that indicate purpose
- **Comprehensive documentation** with practical examples
- **Sensible defaults** that work for most use cases
- **Helpful error messages** that guide users to solutions
- **Progress feedback** during long operations

### 2. Versatility

**"Tools should handle diverse scenarios and adapt to different requirements"**

- **Multiple input/output formats** support
- **Configurable behavior** through parameters
- **Adaptive processing** based on content characteristics
- **Platform-agnostic** design where possible
- **Extensible architecture** for future enhancements

### 3. Robustness

**"Tools should work reliably under various conditions and handle errors gracefully"**

- **Comprehensive input validation**
- **Effective error handling** with fallback strategies
- **Resource management** and monitoring
- **Quality assurance** for outputs
- **Graceful degradation** when issues occur

### 4. Informative Feedback

**"Tools should provide clear, actionable information about their operation"**

- **Detailed logging** of all operations
- **Progress reporting** for long-running tasks
- **Quality metrics** for outputs
- **Error diagnostics** with suggestions
- **Performance metrics** for optimization

### 5. Decisive Operation

**"Tools should make clear decisions and provide unambiguous results"**

- **Binary success/failure** outcomes
- **Clear quality thresholds**
- **Automated decision-making** where appropriate
- **Consistent behavior** across executions
- **Predictable results** for given inputs

## Tool Design Patterns

### 1. Base Tool Architecture

```python
class BaseTool:
    """
    Base class for all podcast production tools
    """

    def __init__(self, name: str, description: str, config: dict = None):
        """
        Initialize tool with 

*[truncated — see source for full prompt]*