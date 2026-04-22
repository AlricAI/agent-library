# Code Craftsmanship Principles

> This document outlines key patterns and principles for writing clean, maintainable, and efficient code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Craftsmanship Principles

This document outlines key patterns and principles for writing clean, maintainable, and efficient code. These guidelines were developed through iterative refinement of actual code and represent practical approaches to software craftsmanship.

## Key Design Patterns

### Progressive Refinement
- Start with working code, then iteratively improve it
- Each change should build on previous improvements
- Explore alternatives and weigh trade-offs at each step
- Don't expect to get it right on the first attempt
- **Push through initial complexity** - resistance often means you're learning, not that you should quit
- **Work incrementally through hard problems** - break them down rather than avoiding them

### Meaningful Naming
- Spend time finding precise, descriptive variable names
- Create a "narrative" through variable names that shows data transformation
- Prefer action-oriented names that indicate what processing has occurred
- Use consistent naming patterns for related concepts
- Concise is good, but clarity is better

### Proximity Principle
- Position variables close to where they're first used
- Group related operations together
- Arrange code to reveal dependencies and flow
- "Snuggle" related statements to show their relationship

### Early Return Pattern
- Handle special cases first with early returns
- Use descriptive condition variables to make returns self-documenting
- Structure conditional paths from specific to general
- Avoid deeply nested conditions when possible

### Variable Minimalism
- Eliminate unnecessary intermediate variables
- Combine operations where it improves clarity
- Only create variables when they add meaning or improve readability
- Consider inlining single-use variables in expressions

### Conditional Optimization
- Check conditions before doing expensive work
- Use early returns to avoid unnecessary processing
- Break complex conditionals into named variables for clarity
- Consider the common case and o

*[truncated — see source for full prompt]*