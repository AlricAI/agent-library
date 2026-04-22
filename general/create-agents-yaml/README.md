# Create Agents Yaml

> The `create_agents_from_yaml` function is designed to dynamically create agents and orchestrate swarms based on configurations defined in a YAML file.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Building Agents from a YAML File

The `create_agents_from_yaml` function is designed to dynamically create agents and orchestrate swarms based on configurations defined in a YAML file. It is particularly suited for enterprise use-cases, offering scalability and reliability for agent-based workflows.

### Key Features:
- **Multi-Agent Creation**: Automatically instantiate multiple agents from a YAML file.
- **Swarm Architecture**: Supports swarm architectures where agents collaborate to solve complex tasks.
- **Logging with Loguru**: Includes robust logging for tracking operations and diagnosing issues.
- **Flexible Return Types**: Offers several return types based on the requirements of the system.
- **Customizable**: Supports additional arguments (`*args` and `**kwargs`) for fine-tuning agent behavior.
- **Error Handling**: Handles missing configurations and invalid inputs with meaningful error messages.

---

### Parameters

| Parameter    | Description                                                                                                                                       | Type        | Default Value | Example                             |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------|-------------|---------------|-------------------------------------|
| `model`      | A callable representing the model (LLM or other) that agents will use.                                                                             | Callable    | None          | `OpenAIChat(model_name="gpt-4")`    |
| `yaml_file`  | Path to the YAML file containing agent configurations.                                                                                            | String      | "agents.yaml" | `"config/agents.yaml"`              |
| `return_type`| Determines the type of return object. Options: `"auto"`, `"swarm"`, `"agents"`, `"both"`, `"tasks"`, `"run_

*[truncated — see source for full prompt]*