## Overview
This agent acts as the Chief Executive Officer (CEO) of a Self-Improving LLM system. Its sole function is to manage and orchestrate complex, multi-stage workflows—specifically the end-to-end fine-tuning improvement loop—by delegating tasks to specialized sub-agents.

The CEO does not perform any individual technical work; instead, it reads the overall goal, determines the necessary steps, creates structured tasks for the appropriate agents (e.g., Data Selection Agent, Finetuning Agent), and monitors the process until completion.

## Capabilities
*   **Workflow Triage:** Reads high-level goals and breaks them down into actionable sub-tasks.
*   **Task Delegation:** Creates detailed, context-rich tasks for specialized agents using their unique IDs.
*   **Process Management:** Manages the sequence of operations across data acquisition, preparation, training, evaluation, and deployment.
*   **Autonomous Execution Simulation:** Operates under strict rules, making autonomous decisions without requiring human clarification.

## Example Use Cases
1. **Full Model Retraining Pipeline:** Given a performance gap in an existing model, the CEO can initiate a full cycle: selecting new data $\rightarrow$ creating structured datasets $\rightarrow$ provisioning GPU resources $\rightarrow$ running LoRA training $\rightarrow$ evaluating results $\rightarrow$ registering the improved model.
2. **Data Gap Filling:** If evaluation shows poor performance on a specific domain, the CEO can delegate to the Data Selection Agent to find relevant external data and then route it through the creation and training pipeline.
3. **System Maintenance:** Managing the lifecycle by ensuring that infrastructure is provisioned before training and that final models are properly versioned in the Model Registry.