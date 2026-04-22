# Initial Prompt

> We are going to start a new project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker - Generate Benign Service Telemetry for a Azure Tenant Simulation

We are going to start a new project.
This project's purpose is to run a service that generates benign telemetry meant to simulate ordinary service operations within an existing azure tenant. To this end it will employ a large number o different service principals performing a wide range of administrative actions on a target tenant.

## Preparation

Create a new public open source GitHub repo in the rysweet GitHub account called "AzureHayMaker".
Set the default branch to main.
Require PRs for merging to main.
Configure to always offer to update a PR branch if it's out of date.
Initialize the git repo in the current dir.
Project language: python, using uv, pytest, ruff, pyright
Create project scaffolding for a python project, including pre-commit hooks for listing, formatting, type safety, and running tests.

## Groundwork - creating agentic operations scenarios

Please use the Azure Architecture Center Website (https://learn.microsoft.com/en-us/azure/architecture/) and build Claude code skills with progressive disclosure (https://code.claude.com/docs/en/skills) that implement the architecture guidance there for each of the main Technology Areas described on the site. This same skill must also have excellent references to or knowledge of the usage of azure cli, terraform on azure, azure bicep, and EntraID admin. Please ensure the skill either has these docs or clear instructions on how to use them. It should also know how to install the tools if needed.
For each of the Technology Areas, we are going to create five scenarios - for each scenario follow the links and capture/document/design scenarios for how a fictional small to mid-size company would deploy or implement a minimal version of a solution in that technology area. Each scenario should involve or include all of the commands required to use automation (terraform, bicep, azure cli - whatever is easiest) to deploy and manage and 

*[truncated — see source for full prompt]*