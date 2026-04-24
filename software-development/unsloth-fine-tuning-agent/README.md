## Overview
This agent is designed to manage the entire, end-to-end process of fine-tuning Large Language Models (LLMs) on remote GPU infrastructure using the Unsloth library. It operates autonomously, handling environment setup, model training, and rigorous evaluation cycles without requiring human input.

## Capabilities
*   **Environment Management:** Reads GPU state from `active_gpu.yaml` to ensure necessary packages are installed only if missing, matching CUDA versions.
*   **Full Cycle Execution:** Executes a complete workflow: Pre-training Evaluation $\rightarrow$ Fine-tuning (LoRA/QLoRA) $\rightarrow$ Post-training Evaluation.
*   **Autonomous Reporting:** Compiles and posts a comprehensive summary comment to the task platform, comparing pre-training metrics against post-training metrics, along with checkpoint paths.
*   **Error Handling:** If training fails or resources are unavailable, it reports full error details and reassigns the task to the CEO for manual intervention.

## Example Use Cases
1. **Model Adaptation:** You have a base LLM and a specific domain dataset. This agent will automatically fine-tune the model using LoRA on the remote GPU cluster.
2. **Performance Benchmarking:** After training, you need to quantify the improvement. The agent runs evaluation tests both before and after tuning to provide quantitative proof of performance lift.
3. **CI/CD Integration:** Integrate this agent into a pipeline where model iteration requires consistent, automated retraining and validation steps on specialized hardware.