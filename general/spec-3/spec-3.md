---
name: Spec
description: **目标:** 构建一个基于 Node.js (NestJS) 的高性能、零依赖、支持多模型协作的企业级 Agent 上下文管理系统。
**核心约束:** 无 LangChain，无独立 Router，环境变量驱动模型配置，基于 LLM 的 Rerank 机制。

## 1. 项目基础架构 (Inf
model: claude-sonnet-4-5
---
# 📘 Nexus-Context v2.0 技术实施规范

**目标:** 构建一个基于 Node.js (NestJS) 的高性能、零依赖、支持多模型协作的企业级 Agent 上下文管理系统。
**核心约束:** 无 LangChain，无独立 Router，环境变量驱动模型配置，基于 LLM 的 Rerank 机制。

## 1. 项目基础架构 (Infrastructure)

### 1.1 目录结构 (Directory Structure)

遵循 NestJS 标准模块化结构。

```text
src/
├── app.module.ts
├── main.ts
├── common/
│   ├── config/              # 环境变量验证
│   ├── constants/           # 系统常量
│   └── utils/               # XML构建工具, Token计算器
├── modules/
│   ├── core/
│   │   ├── prisma/          # DB 连接
│   │   └── llm-client/      # 手写 HTTP LLM 客户端 (无 LangChain)
│   ├── memory/
│   │   ├── vector-store/    # pgvector 原始 SQL 操作
│   │   ├── queue/           # BullMQ 处理器 (摘要/折叠)
│   │   └── memory.service.ts
│   └── agent/
│       ├── context/         # 上下文组装, Rerank 逻辑
│       ├── agent.controller.ts
│       └── agent.orchestrator.ts

```

### 1.2 环境变量 (Environment Variables)

使用 `zod` 或 `joi` 在启动时严格验证以下变量：

```env
# Server
PORT=3000
NODE_ENV=production

# Database
DATABASE_URL="postgresql://user:password@localhost:5432/nexus_db?schema=public"
REDIS_URL="redis://localhost:6379"

# Model 1: Thinking (主推理模型: GPT-4o, Claude 3.5 Sonnet, DeepSeek V3)
THINKING_MODEL_NAME="gpt-4o"
THINKING_MODEL_KEY="sk-..."
THINKING_MODEL_BASE="https://api.openai.com/v1"

# Model 2: Fast (高吞吐模型: GPT-4o-mini, Gemini Flash)
FAST_MODEL_NAME="gpt-4o-mini"
FAST_MODEL_KEY="sk-..."
FAST_MODEL_BASE="https://api.openai.com/v1"

# Model 3: Rerank (重排模型，通常复用 Fast 或特定小模型)
RERANK_MODEL_NAME="gpt-4o-mini"
RERANK_MODEL_KEY="sk-..."
RERANK_MODEL_BASE="https://api.openai.com/v1"
RERANK_ENABLED="true"                    # 是否启用 LLM Rerank（关闭时仅使用向量搜索 Top-5）

# Embedding (向量化模型)
EMBEDDING_MODEL_NAME="text-embedding-3-small"
EMBEDDING_MODEL_KEY="sk-..."
EMBEDDING_MODEL_BASE="https://api.openai.com/v1"

```

---

## 2. 数据库设计 (Database Schema)

### 2.1 Prisma Schema

必须开启 `postgresql` 的 `vector` 扩展。

```prisma
// schema.prisma

generator client {
  provider = "prisma-client-js"
  previewFeatures = ["postgresqlExtensions"]
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
  extensions = [vector]
}

model Session {
  id        String    @id @default(uuid())
  userId    String    @map("user_id")
  summary   String?   @db.Text // 长期记忆摘要
  createdAt DateTime  @default(now())
  updatedAt DateTime  @updatedAt
  messages  Message[]

  @@index([userId])
  @@map("sessions")
}

model Message {
  id        String   @id @default(uuid())
  sessionId String   @map("session_id")
  session   Session  @relation(fields: [sessionId], references: [id], onDelete: Cascade)
  
  // 枚举: 'user', 'assistant', 'system', 'tool'
  role      String   
  
  // 实际发送给 LLM 的内容 (如果是大工具输出，此处为摘要)
  content   String   @db.Text 
  
  // 结构化元数据
  // { 
  //   "isFolded": boolean, 
  //   "originalArtifactId": "blob_key", 
  //   "tokenCount": number,
  //   "toolCallId": string
  // }
  metadata  Json?    
  
  // 向量索引 (使用 1536 维，需根据 Embedding 模型调整)
  embedding Unsupported("vector(1536)")?

  createdAt DateTime @default(now())

  @@map("messages")
}

model KnowledgeDoc {
  id        String   @id @default(uuid())
  content   String   @db.Text
  metadata  Json?    // { source: "file.ts", line: 10 }
  
  embedding Unsupported("vector(1536)")?
  
  createdAt DateTime @default(now())

  @@map("knowledge_docs")
}

```

---

## 3. 核心模块详解 (Module Implementation)

### 3.1 `LlmClientService` (Core Module)

**职责:** 统一的 HTTP Client，处理不同厂商的 API 差异，提供流式和非流式接口。

* **Interface:**
```typescript
type ModelType = 'THINKING' | 'FAST' | 'RERANK' | 'EMBEDDING';

interface LlmMessage {
  role: 'system' | 'user' | 'assistant' | 'tool';
  content: string;
  tool_call_id?: string;
}

interface CompletionOptions {
  temperature?: number;
  maxTokens?: number;
  responseFormat?: 'json_object' | 'text';
}

```


* **核心方法 `chatCompletion`:**
1. 接收 `modelType` 参数。
2. 根据 `modelType` 从 `ConfigService` 读取对应的 `BASE_URL` 和 `API_KEY`。
3. 使用 `axios` 或 `fetch` 发送请求。
4. **Crucial:** 错误重试机制 (Exponential Backoff)。



### 3.2 `VectorStoreService` (Memory Module)

**职责:** 封装 `prisma.$queryRaw` 进行向量操作。

* **核心方法 `similaritySearch`:**
```typescript
async search(embedding: number[], limit: number = 20): Promise<SearchResult[]> {
  const vectorStr = `[${embedding.join(',')}]`;
  // 使用 <=> (cosine distance) 操作符
  return this.prisma.$queryRaw`
    SELECT id, content, metadata, 
           1 - (embedding <=> ${vectorStr}::vector) as similarity
    FROM knowledge_docs
    ORDER BY similarity DESC
    LIMIT ${limit};
  `;
}

```



### 3.3 `RerankService` (Agent/Context Module)

**职责:** 使用 `FAST_MODEL` 对召回结果进行 Listwise 排序（可通过 `RERANK_ENABLED` 环境变量禁用）。

* **配置开关:**
```typescript
// 当 RERANK_ENABLED=false 时，直接返回 Vector Search 的 Top-5
if (!config.rerankEnabled) {
  return vectorResults.slice(0, 5);
}
```

* **Prompt 模板:**
```text
你是一个文档相关性评估专家。
用户查询: "{{query}}"

以下是候选文档列表，格式为 [ID]: 内容片段。
请分析每条文档与查询的相关性，选出最相关的 5 条。

候选列表:
{{candidates_formatted_string}}

请严格返回 JSON 格式，包含一个 id 数组:
{ "top_ids": ["id_1", "id_5", ...] }

```


* **逻辑:**
1. 接收 Vector Search 的 Top-20 结果。
2. 构造 Prompt。
3. 调用 `LlmClientService.chatCompletion('RERANK', ...)`，强制 JSON 模式。
4. 解析返回的 ID，返回过滤后的 Top-5 Docs。



### 3.4 `ContextService` (Agent/Context Module)

**职责:** 构建最终发给 `THINKING_MODEL` 的 XML Prompt。

* **结构定义:**
```xml
<root>
  <system_instructions>
    ... (Persona, Guidelines) ...
  </system_instructions>

  <long_term_memory>
    {{session_summary}}
  </long_term_memory>

  <relevant_knowledge>
    <doc id="1" source="auth.ts">...</doc>
    <doc id="5" source="api.md">...</doc>
  </relevant_knowledge>

  <conversation_history>
    <message role="user">...</message>
    <message role="assistant">...</message>
  </conversation_history>

  <user_query>
    {{current_query}}
  </user_query>
</root>

```



### 3.5 `AsyncWorker` (Memory Module / BullMQ)

**职责:** 响应后的后台处理。

* **Processor:** `MemoryProcessor`
* **任务类型:**
1. `FOLD_TOOL_OUTPUT`:
* 检查 `message.content` 长度。
* 若 > 2000 字符，调用 `THINKING_MODEL` 生成摘要（摘要质量直接影响后续查询准确性）。
* 更新 DB: `content` = 摘要, `metadata.original` = 存 Blob。


2. `GENERATE_EMBEDDING`:
* 调用 Embedding API。
* 执行 SQL `UPDATE messages SET embedding = ... WHERE id = ...`。


3. `COMPACT_SESSION`:
* **触发条件**: 当会话总 Token 数超过 100,000 时触发。
* **压缩策略**:
  - 读取当前 Summary + 所有历史 Messages。
  - 调用 `THINKING_MODEL` 生成新的压缩摘要（会话摘要至关重要，需使用最强推理能力）。
  - **保留规则**: 压缩后保留最近 50 轮对话，或最多 50,000 tokens（以先达到者为准）。
  - 更新 DB: `session.summary` = 新摘要, 删除旧消息记录。





---

## 4. API 接口契约 (API Contract)

### POST `/api/v1/agent/chat`

**Request:**

```json
{
  "sessionId": "uuid-v4",
  "message": "帮我看看为什么 login 接口报错",
  "files": ["src/auth/login.ts"] // 可选：客户端主动上传的上下文
}

```

**Response (Streaming):**

```text
data: {"type": "token", "content": "好的"}
data: {"type": "token", "content": "，"}
data: {"type": "token", "content": "我"}
...
data: {"type": "citation", "docId": "1"} 
...
data: {"type": "done"}

```

---

## 5. 执行流 (Execution Flow)

当请求到达 `AgentController`：

1. **并行获取上下文 (Promise.all):**
* `History`: DB 查询最近 20 条消息。
* `Embedding`: 将 user message 转为 vector。


2. **向量召回:** 使用 vector 查询 DB，获得 Top-20。
3. **Rerank:** 将 Top-20 喂给 `FAST_MODEL`，获得 Top-5。
4. **组装 Prompt:** 拼接 XML (History + Reranked Docs + Summary)。
5. **推理生成:**
* 调用 `THINKING_MODEL` (Stream 模式)。
* 将流直接 pipe 给前端 response。


6. **后续处理 (Fire-and-Forget):**
* 将 User Message 和 Assistant Response (完整文本) 加入 BullMQ 队列。



---

## 6. 开发实施清单 (Checklist)

对于 Coding Agent，请按此顺序生成代码：

1. **Setup:** 初始化 NestJS，安装 `prisma`, `@prisma/client`, `pg`, `axios`, `bullmq`, `xml-js`。
2. **Database:** 编写 `docker-compose.yml` (Postgres+pgvector, Redis)，运行 `prisma migrate dev`。
3. **Core:** 实现 `LlmClientService`，编写单元测试确保能调通 OpenAI/Claude 接口。
4. **Memory:** 实现 `VectorStoreService` 和 `MemoryProcessor` (BullMQ)。
5. **Logic:** 实现 `RerankService` 和 `ContextService`。
6. **API:** 实现 Controller 和 Orchestrator，串联全流程。