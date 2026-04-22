# README

> The `BedrockInvokeAgentTool` enables CrewAI agents to invoke Amazon Bedrock Agents and leverage their capabilities within your workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# BedrockInvokeAgentTool

The `BedrockInvokeAgentTool` enables CrewAI agents to invoke Amazon Bedrock Agents and leverage their capabilities within your workflows.

## Installation

```bash
pip install 'crewai[tools]'
```

## Requirements

- AWS credentials configured (either through environment variables or AWS CLI)
- `boto3` and `python-dotenv` packages
- Access to Amazon Bedrock Agents

## Usage

Here's how to use the tool with a CrewAI agent:

```python
from crewai import Agent, Task, Crew
from crewai_tools.aws.bedrock.agents.invoke_agent_tool import BedrockInvokeAgentTool

# Initialize the tool
agent_tool = BedrockInvokeAgentTool(
    agent_id="your-agent-id",
    agent_alias_id="your-agent-alias-id"
)

# Create a CrewAI agent that uses the tool
aws_expert = Agent(
    role='AWS Service Expert',
    goal='Help users understand AWS services and quotas',
    backstory='I am an expert in AWS services and can provide detailed information about them.',
    tools=[agent_tool],
    verbose=True
)

# Create a task for the agent
quota_task = Task(
    description="Find out the current service quotas for EC2 in us-west-2 and explain any recent changes.",
    agent=aws_expert
)

# Create a crew with the agent
crew = Crew(
    agents=[aws_expert],
    tasks=[quota_task],
    verbose=2
)

# Run the crew
result = crew.kickoff()
print(result)
```

## Tool Arguments

| Argument | Type | Required | Default | Description |
|----------|------|----------|---------|-------------|
| agent_id | str | Yes | None | The unique identifier of the Bedrock agent |
| agent_alias_id | str | Yes | None | The unique identifier of the agent alias |
| session_id | str | No | timestamp | The unique identifier of the session |
| enable_trace | bool | No | False | Whether to enable trace for debugging |
| end_session | bool | No | False | Whether to end the session after invocation |
| description | str | No | None | Custom description for the tool |

## Environment Variables

```bash
BEDROCK_AGENT_

*[truncated — see source for full prompt]*