# Meta Clarification Example

> This demonstrates the meta-clarification feature where you can use a separate AI instance to help formulate better responses to clarification questions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Meta-Clarification Feature Example

This demonstrates the meta-clarification feature where you can use a separate AI instance to help formulate better responses to clarification questions.

## How It Works

1. **Start Clarification Workflow**: Input your request (e.g., "optimize the code")
2. **Choose AI-Assisted Mode**: When questions appear, select option 2
3. **Copy Generated Prompt**: The system generates a structured prompt for another AI
4. **Paste to External AI**: Use ChatGPT, Claude, or any other AI to get optimal answers
5. **Input AI Response**: Return to OOS and paste the AI's response

## Example Workflow

### Step 1: User Input
```
What would you like me to help you with?
> optimize the authentication system
```

### Step 2: System Analysis
```
📊 Input Analysis
   Original: optimize the authentication system
   Intent: optimization
   Confidence: 60%
   ⚠️ Ambiguities found: 2
```

### Step 3: Clarification Options
```
❓ I need clarification (3 questions):

💡 Options:
  1. Answer questions manually
  2. Generate AI-assisted response prompt (copy/paste to another AI)
  3. Input AI-assisted response

Choose option (1-3): 2
```

### Step 4: Generated Prompt for External AI
```
📋 Copy this prompt to another AI instance:
============================================================
I'm working with a clarification system and need help formulating optimal responses to these questions.

**Context**: optimize the authentication system

**Questions to Answer**:

1. What's your primary goal?
   Options:
   1. Analyze and understand existing code
   2. Implement new functionality
   3. Fix or optimize existing code
   4. Create documentation
   5. Test or validate something

2. What type of project or technology stack are you working with?

3. What level of solution are you looking for?
   Options:
   1. Quick and simple approach
   2. Comprehensive and robust solution
   3. Balanced approach with good practices

**Please provide**:
1. Your recommended answer

*[truncated — see source for full prompt]*