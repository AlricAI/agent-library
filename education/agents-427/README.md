# Agents

> +++
date = '2025-01-07T16:51:43Z'
draft = true
title = 'Agents: A tutorial on building agents in python'
categories = ['AI', 'agents', 'smolagents']
t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = '2025-01-07T16:51:43Z'
draft = true
title = 'Agents: A tutorial on building agents in python'
categories = ['AI', 'agents', 'smolagents']
tag = ['agents'] 
+++

## LLM Agents

Agents are used enhance and extend the functionality of LLM's.

In this tutorial, we’ll explore what LLM agents are, how they work, and how to implement them in Python. 

## What Are LLM Agents?

An agent is an autonomous process that may use the LLM and other tools multiple times to achieve a goal. 
The LLM output often controls the workflow of the agent(s).

## What is the difference between Agents and LLMs or AI?

Agents are processes that may use LLM's and other agents to achieve a task. 
Agents act as orchestrators or facilitators, combining various tools and logic, whereas LLMs are the underlying generative engines.

For example a customer support agent could be comprised of 
- an agent to retrieve customer information 
- an agent to retrieve order details and information
- a processing agent to cancel or update orders
- a chatbot to interact with the customer
- a guardrails agent to make sure that the customer has an optimal experience
- a human in the loop agent to forward the customer to a real person when no solution is achieved


### Sample applications of Agents

Agents can be used anywhere, some common applications include

- Process unstructured natural language input.
- Perform reasoning to deduce solutions or actions.
- Interact with external systems, APIs, or databases.
- Generate human-like responses or results based on context.
- Add a memory to the LLM.
- Query the web for contextual information.
- Run python code to extract further information from the data available to the LLM


### Autonomous operation

They are often designed to act autonomously, making them useful for automating workflows, building chatbots, or even creating virtual assistants.


### Agent collaboration

Ofter we have agents interacting with other agents and in some cases managing and contro

*[truncated — see source for full prompt]*