# Agent Delegation Strategy & Best Practices

> description: | Advanced agent delegation strategies for optimal workload distribution and specialized task execution. Defines when and how to delegate tasks to specialized coding agents, monitoring strategies, and integration

## Tags
`docker` `claude`

## System Prompt
---
description: |
  Advanced agent delegation strategies for optimal workload distribution and specialized task execution. 
  Defines when and how to delegate tasks to specialized coding agents, monitoring strategies, and integration 
  patterns. Apply when: planning complex features, managing high workloads, requiring specialized expertise, 
  optimizing parallel execution.
alwaysApply: true
priority: 2
---

# Agent Delegation Strategy & Best Practices

## 1. Delegation Decision Framework

### 1.1 When to Delegate (DELEGATE)
**Primary Criteria:**
- **Complexity + Independence**: Task is complex but doesn't require deep system integration
- **Specialized Expertise**: Task benefits from focused domain expertise (testing, documentation, research)
- **Parallel Execution**: Task can run alongside other work without conflicts
- **Clear Scope**: Task has well-defined boundaries and acceptance criteria
- **Time Intensive**: Task is time-consuming but routine (documentation, code review)

**Examples of Delegation Candidates:**
- API documentation generation
- Unit test implementation for specific components
- Code review and refactoring of isolated modules
- Research tasks (technology evaluation, pattern analysis)
- Migration scripts for data transformations
- Performance optimization for specific algorithms
- Integration testing for external services

### 1.2 When to Execute Directly (EXECUTE)
**Primary Criteria:**
- **Strategic Decisions**: Architectural choices, design patterns, technology selection
- **Deep Integration**: Requires understanding of entire system context
- **User Interaction**: Tasks requiring user feedback or iterative refinement
- **Security Sensitive**: Authentication, authorization, data protection implementations
- **System Critical**: Core framework functionality, essential business logic

**Examples of Direct Execution:**
- Architecture design and planning
- Core feature implementations requiring system-wide changes
- Database schema design and mi

*[truncated — see source for full prompt]*