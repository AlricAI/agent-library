# Todo Command Script Bash Test Areas Needed

> This document identifies gaps in test coverage across different execution methods (command, script, bash) and various test features.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Command/Script/Bash Test Coverage Matrix

This document identifies gaps in test coverage across different execution methods (command, script, bash) and various test features.

## Additional YAML Elements Not Yet Considered

Based on examination of the YamlTestCaseParser.cs file, the following YAML elements also need test coverage:

1. `cli` - Purpose appears to be related to command-line interface settings
2. `arguments` - A mapping of argument names to values passed to commands or scripts
3. `sanitize` - Likely related to output sanitization
4. `foreach` - Used in matrix tests to iterate over values (separate from matrix-file)
5. `optional` - Marks a test as optional, meaning it might be skipped based on certain conditions

## Feature Coverage Matrix

| Feature          | command | script | bash |
|------------------|---------|--------|------|
| args/arguments   | ✓       | ✗      | ✗    |
| input (stdin)    | ✓       | ✓      | ✓    |
| timeout          | ✗       | ✓      | ✓    |
| expect-regex     | ✓       | ✓      | ✓    |
| expect (LLM)     | ✓       | ✗      | ✗    |
| env variables    | ✗       | ✗      | ✓    |
| workingDirectory | ✓       | ✗      | ✗    |
| optional         | ✓       | ✓      | ✓    |
| tag/tags         | ✓       | ✗      | ✗    |

Legend:
- ✓: Tested
- ✗: Not tested

## Coverage Gaps:

1. **Command:**
   - No tests for timeout with command execution
   - No tests for environment variable handling with command execution

2. **Script:**
   - No tests for command-line arguments with script execution
   - No tests for LLM-based expect validation
   - No tests for environment variables
   - No tests for workingDirectory
   - No tests using tag/tags specifically with script execution

3. **Bash:**
   - No tests for command-line arguments with bash execution
   - No tests for LLM-based expect validation
   - No tests for workingDirectory
   - No tests using tag/tags specifically with bash execution

4. **Common Gaps Across All Methods:**
   

*[truncated — see source for full prompt]*