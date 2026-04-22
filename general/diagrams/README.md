# DIAGRAMS

> This document contains comprehensive visual diagrams explaining the ModPorter AI system architecture and conversion process flow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ModPorter AI - System Architecture Diagrams

This document contains comprehensive visual diagrams explaining the ModPorter AI system architecture and conversion process flow.

## System Architecture Overview

```mermaid
graph TB
    User[👤 User] --> Frontend[⚛️ React Frontend<br/>Vite + TypeScript]
    Frontend --> API[🔌 API Gateway<br/>FastAPI]
    
    API --> Backend[🐍 Backend Service<br/>Python + FastAPI]
    Backend --> AIEngine[🤖 AI Engine<br/>CrewAI + LangChain]
    Backend --> Database[(🗄️ PostgreSQL<br/>Conversion Data)]
    Backend --> Cache[(⚡ Redis<br/>Session Cache)]
    Backend --> FileStorage[📁 File Storage<br/>Conversion Assets]
    
    AIEngine --> JavaAnalyzer[🔍 Java Analyzer<br/>Agent]
    AIEngine --> BedrockArchitect[🏗️ Bedrock Architect<br/>Agent]
    AIEngine --> LogicTranslator[🔄 Logic Translator<br/>Agent]
    AIEngine --> AssetConverter[🎨 Asset Converter<br/>Agent]
    AIEngine --> PackagingAgent[📦 Packaging<br/>Agent]
    AIEngine --> QAValidator[✅ QA Validator<br/>Agent]
    
    LocalAgent[🎮 Local Validation Agent<br/>Node.js] --> MinecraftJava[☕ Minecraft Java]
    LocalAgent --> MinecraftBedrock[🧱 Minecraft Bedrock]
    LocalAgent --> Backend
    
    classDef userClass fill:#e1f5fe
    classDef frontendClass fill:#f3e5f5
    classDef backendClass fill:#e8f5e8
    classDef aiClass fill:#fff3e0
    classDef dataClass fill:#fce4ec
    classDef agentClass fill:#f1f8e9
    
    class User userClass
    class Frontend,API frontendClass
    class Backend backendClass
    class AIEngine,LocalAgent aiClass
    class Database,Cache,FileStorage dataClass
    class JavaAnalyzer,BedrockArchitect,LogicTranslator,AssetConverter,PackagingAgent,QAValidator agentClass
```

## PRD Feature Flow - Conversion Process

```mermaid
flowchart TD
    Start([🚀 User Starts Conversion]) --> Upload{📤 Upload Method?}
    
    Upload -->|File| FileUpload[📁 File Upload<br/>PRD Feature 1]
    Upload -->|URL| URLInput[🔗 URL Input<br/>CurseForge/Modri

*[truncated — see source for full prompt]*