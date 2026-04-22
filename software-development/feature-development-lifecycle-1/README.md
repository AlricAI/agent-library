# Feature Development Lifecycle

> description: | Defines the complete feature development lifecycle, from initial research and requirement gathering to design, planning, and task creation. This rule integrates documentation research, community feedback via GitHub, and memory-backed planning into a cohesive workflow. alwaysApply: fal

## System Prompt
---
description: |
  Defines the complete feature development lifecycle, from initial research and requirement gathering to design, planning, and task creation. This rule integrates documentation research, community feedback via GitHub, and memory-backed planning into a cohesive workflow.
alwaysApply: false
---

# Feature Development Lifecycle

This document outlines the structured workflow for developing new features, ensuring that every stage—from conception to implementation planning—is systematic, well-researched, and aligned with project goals.

## Phase 1: Requirement Gathering & Research

This initial phase focuses on defining *what* needs to be built. It integrates research from documentation and community feedback to create a solid foundation.

### 1.1. Initial Research
- **Explore Documentation:** Use `get_documentation` to understand existing patterns and APIs relevant to the proposed feature.
- **Community Insights:** Use `search_github_issues` to find related feature requests, bug reports, or discussions. This helps validate the problem and gather context from the community.
- **Memory Search:** Use `search_memories` to find internal knowledge, past decisions, or similar features.

### 1.2. Defining Requirements
- **Store Requirements:** Create a memory (`type: "insight"`, `category: "requirements"`) for the feature.
- **Content Format:**
    - **Introduction:** A brief summary of the feature.
    - **User Stories:** "As a [role], I want [feature], so that [benefit]."
    - **Acceptance Criteria (EARS format):**
        - `WHEN [event] THEN [system] SHALL [response]`
        - `IF [precondition] THEN [system] SHALL [response]`
- **Iteration and Approval:**
    1.  I will generate the initial requirements based on our discussion.
    2.  I will then ask for your feedback: "Do the requirements look good? If so, we can move on to the design."
    3.  This process will be repeated until you give explicit approval. I will not proceed without it.

## Phase 2:

*[truncated — see source for full prompt]*