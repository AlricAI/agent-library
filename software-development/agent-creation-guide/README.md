## Overview
This guide serves as the definitive resource for creating specialized, multi-component AI agents. It details the architectural pattern required for building robust sub-agents, ensuring they possess focused expertise and defined tool access.

Agents are not mere prompts; they are structured entities comprising a core definition (`agent.md`), metadata (`metadata.json`), and optional automation hooks (`hooks.json`). This structure allows for complex, coordinated multi-agent workflows.

## Capabilities
* **Interactive Wizard:** Use the `claude-agents create` command to guide you through naming, describing, defining capabilities, and selecting necessary tools in an automated fashion.
* **Manual Structuring:** Provides step-by-step instructions for manual agent creation, starting with directory setup (`mkdir -p agents/your-agent`).
* **Prompt Definition:** Details the required structure for `agent.md`, including YAML frontmatter for metadata (name, description, tools, triggers) and a detailed system prompt.
* **Best Practices:** Emphasizes advanced concepts like concurrent execution planning to maximize performance in data processing tasks.

## Example Use Cases
This guide is essential when:
* You need to move beyond simple chat interactions into complex, multi-step automated processes.
* You are building a system that requires multiple specialized AI components (e.g., a Data Analyst Agent coordinating with a Report Generator Agent).
* You require a standardized, scalable methodology for onboarding new agent functionalities into your platform.