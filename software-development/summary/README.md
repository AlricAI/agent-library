# Summary

> ## Overview
The `lib/` directory contains the core qtests framework functionality, including test generation, utilities, and TypeScript definitions.



## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# lib/ Directory Summary

## Overview
The `lib/` directory contains the core qtests framework functionality, including test generation, utilities, and TypeScript definitions.

## Files and Their Roles

### circuitBreaker.ts
**Role**: Opossum-based circuit breaker implementation for production reliability  
**Migration**: Replaced custom implementation with industry-standard Opossum library  
**Key Features**:
- Event-driven architecture with comprehensive monitoring
- AbortController support for modern async patterns  
- Prometheus metrics integration available
- Hystrix dashboard compatibility
- Comprehensive fallback system
- Better error handling and state management
**Request/Response Flows**: 
- Input: Async functions and configuration options
- Output: Protected function execution with circuit breaking

### errorHandling/
**Role**: Comprehensive error handling utilities for robust test environments  
**Components**:
- `errorWrappers.ts` - Wraps functions with error handling and fallbacks
- `fallbackHandlers.ts` - Provides standard fallback strategies
**Key Features**:
- Structured error handling with context preservation
- Automatic fallback value generation
- Performance monitoring for error rates
- Integration with logging systems
**Request/Response Flows**: 
- Input: Functions or promises with error context
- Output: Handled results with optional fallbacks

### performanceTesting/
**Role**: Built-in performance testing and benchmarking capabilities  
**Key Features**:
- Memory usage monitoring and tracking
- Execution time measurement with statistical analysis
- Scalability testing with configurable load patterns
- Automated performance regression detection
**Request/Response Flows**: 
- Input: Test functions and performance configuration
- Output: Detailed performance metrics and reports  
**Key Features**:
- Analyzes TypeScript/JavaScript source files for exports and API routes
- Generates `.GeneratedTest.test.ts` integration tests for API endpoints and E

*[truncated — see source for full prompt]*