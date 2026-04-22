# About

> VEIL: The Execution Control Plane for AI

Version 2.1: Detailed Technical Architecture

1. Executive Summary

The Reality:
AI agents are transitioning

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
VEIL: The Execution Control Plane for AI

Version 2.1: Detailed Technical Architecture

1. Executive Summary

The Reality:
AI agents are transitioning from "advisors" to "actors." They now possess the autonomy to move capital, modify infrastructure, and manipulate sensitive data. Granting a probabilistic Large Language Model (LLM) root access to production environments without an independent enforcement layer is a catastrophic operational risk.

The Philosophy: Brain vs. Reflexes
VEIL is built on a biological design pattern:

The Reflexes (Local Enforcement): Security must be local, deterministic, and sub-millisecond. It cannot depend on cloud latency or non-deterministic third-party APIs for every action.

The Brain (Intelligence Plane): High-level strategy, policy synthesis, and forensic reasoning are powered by Google Gemini. The Brain manages the reflexes but does not sit in the network path of a live transaction.

The Solution:
VEIL is a Decision Firewall infrastructure layer. It intercepts every outgoing signal from an AI agent, evaluates the intent against local deterministic policy, and uses cloud-scale intelligence (Gemini) to evolve those policies and train the local enforcers.

2. High-Level Architecture

VEIL separates Enforcement from Intelligence. This ensures that even if the cloud is unreachable or the model hallucinations, the local firewall remains absolute.

🔷 System Context Diagram

       [ INTELLIGENCE PLANE (Cloud) ] <--------------+
       |   Powered by Google Gemini   |               |
       +--------------+---------------+               |
                      |                               |
          (A) Policy  |          (B) Local Judge      | (C) Telemetry &
              Code    |              Weights          |     Logs
                      v                               |
    [ ENFORCEMENT PLANE (Local / Edge) ] -------------+
+------------------------------------------+       +-------------------------+
|                     

*[truncated — see source for full prompt]*