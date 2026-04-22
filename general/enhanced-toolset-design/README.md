# Enhanced Toolset Design

> ## Design Principles

### 1. Usability First

- **Intuitive Interfaces**: Tools should have clear, well-documented APIs
- **Consistent Patterns**: Fol

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhanced Toolset Design for Podcast Production

## Design Principles

### 1. Usability First

- **Intuitive Interfaces**: Tools should have clear, well-documented APIs
- **Consistent Patterns**: Follow established design patterns for predictability
- **Helpful Error Messages**: Provide actionable feedback when things go wrong
- **Progress Feedback**: Show status updates during long operations

### 2. Versatility

- **Multi-format Support**: Handle various input/output formats gracefully
- **Configurable Behavior**: Allow customization through configuration
- **Platform Agnostic**: Work across different operating systems and environments
- **Extensible Architecture**: Easy to add new features without breaking existing ones

### 3. Robustness

- **Comprehensive Error Handling**: Gracefully handle edge cases and failures
- **Resource Management**: Proper cleanup of files, connections, and memory
- **Validation**: Input validation at all levels
- **Fault Tolerance**: Continue operation when non-critical components fail

### 4. Informative Operations

- **Detailed Logging**: Provide meaningful logs for debugging and monitoring
- **Status Reporting**: Clear indicators of operation progress and completion
- **Result Documentation**: Well-structured output with metadata
- **Error Context**: Rich error information for troubleshooting

## Core Toolset Architecture

```mermaid
graph TD
    A[Toolset Manager] --> B[Video Tools]
    A --> C[Audio Tools]
    A --> D[Content Tools]
    A --> E[Distribution Tools]
    A --> F[Monitoring Tools]

    B --> B1[Video Analysis]
    B --> B2[Format Conversion]
    B --> B3[Quality Assessment]

    C --> C1[Noise Reduction]
    C --> C2[Level Normalization]
    C --> C3[Format Conversion]

    D --> D1[Content Scheduling]
    D --> D2[Platform Optimization]
    D --> D3[Conflict Detection]

    E --> E1[Multi-platform Publishing]
    E --> E2[CDN Management]
    E --> E3[Analytics Tracking]

    F --> F1[Health Monitoring]
    F --> F2[

*[truncated — see source for full prompt]*