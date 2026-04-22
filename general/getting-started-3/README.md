# Getting Started

> This guide will help you get up and running with CycoD quickly.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started with CycoD

This guide will help you get up and running with CycoD quickly.

## Prerequisites

Before you begin, ensure you have:

- **.NET 8.0 SDK** or later installed
- An **OpenAI API key** if you plan to use OpenAI's models
- An **Azure OpenAI API key** if you plan to use Azure OpenAI
- A **GitHub token** if you plan to use GitHub Copilot

## Installation

### Installing as a .NET Tool

The easiest way to install CycoD is as a .NET global tool:

```bash
dotnet tool install --global CycoD --prerelease
```

This will make the `cycod` command available in your terminal. If you prefer a local installation that's only available in the current directory:

```bash
dotnet tool install --local CycoD --prerelease
```

Note: Local tools require you to run them through the .NET CLI: `dotnet cycod`

### Building from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/robch/cycod.git
   cd cycod
   ```

2. Build the project:
   ```bash
   dotnet build
   ```

3. Run the application:
   ```bash
   dotnet run
   ```

## Setting Up Environment Variables

CycoD uses environment variables to configure API access. You can set these in your shell or add them to a `.cycod/config` file in your home or project directory.

### Configuration File

Create a `.cycod/config` file with your variables:

```
OPENAI_API_KEY=your_api_key_here
OPENAI_CHAT_MODEL_NAME=gpt-4o
```

### OpenAI API

```bash
# Windows
set OPENAI_API_KEY=your_api_key_here
set OPENAI_CHAT_MODEL_NAME=gpt-4o

# Linux/macOS
export OPENAI_API_KEY=your_api_key_here
export OPENAI_CHAT_MODEL_NAME=gpt-4o
```

### Azure OpenAI API

```bash
# Windows
set AZURE_OPENAI_API_KEY=your_api_key_here
set AZURE_OPENAI_ENDPOINT=your_endpoint_here
set AZURE_OPENAI_CHAT_DEPLOYMENT=your_deployment_name

# Linux/macOS
export AZURE_OPENAI_API_KEY=your_api_key_here
export AZURE_OPENAI_ENDPOINT=your_endpoint_here
export AZURE_OPENAI_CHAT_DEPLOYMENT=your_deployment_name
```

### GitHub Copilot API

GitHub C

*[truncated — see source for full prompt]*