---
name: AGENT GUIDE
description: This guide provides instructions on how to integrate and use the different agent frameworks in this workspace.
model: claude-sonnet-4-5
---
# Agent Integration Guide

This guide provides instructions on how to integrate and use the different agent frameworks in this workspace.

## Connecting Agents to ROMA

Agents can be connected to the ROMA framework via its API.

*   **API Endpoint:** `http://localhost:8000`
*   **Health Check:** `http://localhost:8000/health`

**Example (Python):**

```python
import requests

ROMA_API_URL = "http://localhost:8000"

def get_roma_status():
    try:
        response = requests.get(f"{ROMA_API_URL}/health")
        if response.status_code == 200:
            print("Successfully connected to ROMA.")
            return response.json()
        else:
            print(f"Failed to connect to ROMA. Status code: {response.status_code}")
    except requests.exceptions.ConnectionError as e:
        print(f"Connection to ROMA failed: {e}")

if __name__ == "__main__":
    get_roma_status()
```

## Using CAMEL for Simulations

CAMEL is ideal for simulating conversations and collaborations between agents.

1.  **Activate the virtual environment:**
    `source /root/ai-workspace/frameworks/CAMEL/venv-camel/bin/activate`

2.  **Run an example script:**
    `python /root/ai-workspace/frameworks/CAMEL/examples/code/role_playing.py`

## Executing Commands with Open Interpreter

Open Interpreter allows agents to execute shell commands and code locally.

1.  **Activate the virtual environment:**
    `source /root/ai-workspace/frameworks/Open-Interpreter/bin/activate`

2.  **Run a command:**
    `interpreter -y -c "List all files in the current directory."`

## Common Troubleshooting

*   **API Key Errors:** Ensure that the `master.env` file in the `configs` directory is populated with your correct API keys.
*   **Connection Refused:** Use the `status-check.sh` script to verify that the Docker containers for ROMA are running.
*   **Command Not Found:** Make sure you have activated the correct virtual environment before running a script for a specific framework.