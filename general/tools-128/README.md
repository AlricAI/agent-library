# Tools

> Tools extend your agents' capabilities.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Creating Custom Tools

Tools extend your agents' capabilities. This guide shows you how to create type-safe, production-ready tools using Zod schemas.

## Tool Basics

Every tool in Mastra follows this pattern:

```typescript
import { createTool } from "@mastra/core/tools";
import { z } from "zod";

export const myTool = createTool({
  id: "my-tool",                          // Unique identifier
  description: "What this tool does",     // Helps LLM decide when to use it
  inputSchema: z.object({ /* ... */ }),   // Validates input
  outputSchema: z.object({ /* ... */ }),  // Validates output
  execute: async (input) => { /* ... */ },// Implementation
});
```

**Why Zod?**
- Runtime validation catches errors early
- TypeScript inference is automatic
- Clear error messages for debugging
- Self-documenting schemas

## Step-by-Step: Create a Calculator Tool

### 1. Create the Tool File

Create `src/agent/src/mastra/tools/calculator-tools.ts`:

```typescript
import { createTool } from "@mastra/core/tools";
import { z } from "zod";

/**
 * Basic Calculator Tool
 * Performs arithmetic operations with validation
 */
export const calculatorTool = createTool({
  id: "calculate",
  description: "Perform arithmetic calculations (+, -, *, /, ^, sqrt)",
  
  // Define and validate input
  inputSchema: z.object({
    operation: z.enum(["+", "-", "*", "/", "^", "sqrt"])
      .describe("The arithmetic operation to perform"),
    
    a: z.number()
      .describe("First number"),
    
    b: z.number()
      .optional()
      .describe("Second number (not needed for sqrt)"),
  }),
  
  // Define expected output
  outputSchema: z.object({
    result: z.number(),
    expression: z.string(),
  }),
  
  // Implementation
  execute: async ({ operation, a, b }) => {
    let result: number;
    let expression: string;
    
    switch (operation) {
      case "+":
        if (b === undefined) throw new Error("Addition requires two numbers");
        result = a + b;
        expression = `

*[truncated — see source for full prompt]*