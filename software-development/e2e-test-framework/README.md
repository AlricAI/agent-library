# E2E TEST FRAMEWORK

> **Issue:** #324 - End-to-End Integration Testing Framework

## Overview

This testing framework provides comprehensive validation of the ModPorter AI 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# End-to-End Integration Testing Framework

**Issue:** #324 - End-to-End Integration Testing Framework

## Overview

This testing framework provides comprehensive validation of the ModPorter AI conversion pipeline from Java mods to Bedrock add-ons. The tests ensure that the complete workflow (JAR → Analysis → Build → Package) produces valid, working .mcaddon files.

## Test Structure

### Main Test File: `ai-engine/tests/test_mvp_conversion.py`

This comprehensive test suite includes:

#### Test Case 1: Simple Block Conversion (Happy Path)
- **Purpose**: Validate the complete MVP pipeline
- **Steps**:
  1. Load test JAR (simple_copper_block.jar)
  2. Run JavaAnalyzerAgent to extract registry name and texture
  3. Run BedrockBuilderAgent to generate behavior and resource packs
  4. Run PackagingAgent to create .mcaddon file
  5. Validate .mcaddon structure per Bedrock specification
  6. Extract and verify manifest.json files
  7. Verify block definition JSON
  8. Confirm texture present and valid
- **Expected Results**:
  - Analysis succeeds with registry name: `simple_copper:polished_copper`
  - Build creates valid behavior_pack/ and resource_pack/ directories
  - Package creates valid .mcaddon file with correct structure
  - Conversion completes in <30 seconds
- **Success Criteria**:
  - All Bedrock specifications are met
  - No false positives (tests pass but addon doesn't work)

#### Test Case 2: Missing Texture (Fallback)
- **Purpose**: Test conversion when texture is missing
- **Expected Results**:
  - Analysis succeeds but with warning about missing texture
  - Build uses default/fallback texture
  - Package still creates valid .mcaddon
  - Warning is properly documented

#### Test Case 3: Malformed JAR (Error Handling)
- **Purpose**: Test error handling for malformed JAR files
- **Test Scenarios**:
  - Non-existent file path
  - File that's not a valid JAR
  - Empty JAR file
  - Corrupted ZIP file
  - JAR with no mod metadata
- **Expected Results**:
  - Analy

*[truncated — see source for full prompt]*