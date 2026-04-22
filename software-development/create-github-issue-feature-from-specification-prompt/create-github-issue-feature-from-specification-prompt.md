---
name: Create Github Issue Feature From Specification.Prompt
description: Create GitHub Issue for feature request from specification file using feature_request.yml template.
model: claude-sonnet-4-5
tools:
  - search/codebase
  - Azure MCP/search
  - github
  - create_issue
  - search_issues
  - update_issue
---
# Create GitHub Issue from Specification

Create GitHub Issue for the specification at `${file}`.

## Process

1. Analyze specification file to extract requirements
2. Check existing issues using `search_issues`
3. Create new issue using `create_issue` or update existing with `update_issue`
4. Use `feature_request.yml` template (fallback to default)

## Requirements

- Single issue for the complete specification
- Clear title identifying the specification
- Include only changes required by the specification
- Verify against existing issues before creation

## Issue Content

- Title: Feature name from specification
- Description: Problem statement, proposed solution, and context
- Labels: feature, enhancement (as appropriate)