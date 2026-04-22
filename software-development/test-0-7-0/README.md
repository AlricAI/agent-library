# Test 0.7.0

> First, set up a test team with a default model.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
### 1. Create Team with Default Model

First, set up a test team with a default model.

Prompt:
"Create a team named 'v070-test' for testing thinking levels. Use 'anthropic/claude-3-5-sonnet-latest' as the default model."

---

### 2. Spawn Teammates with Different Thinking Levels

Test the new thinking parameter by spawning three teammates with different settings.

Prompt:
"Spawn three teammates with different thinking levels:
- 'DeepThinker' with 'xhigh' thinking level. Tell them they are an expert at complex architectural analysis.
- 'MediumBot' with 'medium' thinking level. Tell them they are a balanced worker.
- 'FastWorker' with 'low' thinking level. Tell them they need to work quickly."

---

### 3. Verify Thinking Levels in Team Config

Check that the thinking levels are correctly persisted in the team configuration.

Prompt:
"Read the config for the 'v070-test' team. Verify that DeepThinker has thinking level 'xhigh', MediumBot has 'medium', and FastWorker has 'low'."

---

### 4. Test Environment Variable Propagation

Verify that the PI_DEFAULT_THINKING_LEVEL environment variable is correctly set for each spawned process.

Prompt (run in terminal):
"Run 'ps aux | grep PI_DEFAULT_THINKING_LEVEL' to check that the environment variables were passed to the spawned teammate processes."

---

### 5. Assign Tasks Based on Thinking Levels

Create tasks appropriate for each teammate's thinking level.

Prompt:
"Create a task for DeepThinker: 'Analyze the pi-teams codebase architecture and suggest improvements for scalability'. Set it to in_progress.
Create a task for FastWorker: 'List all TypeScript files in the src directory'. Set it to in_progress."

---

### 6. Verify Teammate Responsiveness

Check that all teammates are responsive and checking their inboxes.

Prompt:
"Check the status of DeepThinker, MediumBot, and FastWorker using the check_teammate tool. Then send a message to FastWorker asking them to confirm they received their task."

---

### 7. Test Minim

*[truncated — see source for full prompt]*