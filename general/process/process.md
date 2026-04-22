---
name: Process
description: 本文档展示系统从用户首次交互到会话压缩的完整生命周期，包含代码示例、数据状态和系统行为。

---

## 📚 场景设定

**用户场景**：开发者正在调试一个 Node.js 项目的登录接口问题

**知识库已有内容**：
- `src/auth/login.ts` - 登录逻辑代码
- `sr
model: claude-sonnet-4-5
---
# 🔄 Nexus-Context v2.0 实际运行流程演示

本文档展示系统从用户首次交互到会话压缩的完整生命周期，包含代码示例、数据状态和系统行为。

---

## 📚 场景设定

**用户场景**：开发者正在调试一个 Node.js 项目的登录接口问题

**知识库已有内容**：
- `src/auth/login.ts` - 登录逻辑代码
- `src/middleware/auth.ts` - JWT 中间件
- `docs/api.md` - API 文档

---

## 🎬 阶段一：冷启动 - 首次交互

### Step 1: 用户发起请求

```bash
curl -X POST http://localhost:3000/api/v1/agent/chat \
  -H "Content-Type: application/json" \
  -d '{
    "sessionId": "550e8400-e29b-41d4-a716-446655440000",
    "message": "你好"
  }'
```

---

### Step 2: 服务端并行处理

```typescript
// AgentController.chat()
async chat(@Body() dto: ChatDto) {
  // ✅ 创建新会话（首次交互）
  let session = await this.prisma.session.findUnique({
    where: { id: dto.sessionId }
  });

  if (!session) {
    session = await this.prisma.session.create({
      data: {
        id: dto.sessionId,
        userId: 'user_123',
        summary: null, // 冷启动无摘要
      }
    });
  }

  // 🔄 并行获取上下文
  const [history, embedding] = await Promise.all([
    // 1. 查询最近 20 条消息（首次为空）
    this.prisma.message.findMany({
      where: { sessionId: dto.sessionId },
      orderBy: { createdAt: 'desc' },
      take: 20,
    }),
    // 2. 向量化用户输入
    this.llmClient.embed(dto.message, 'EMBEDDING')
  ]);
}
```

**当前状态**：
```typescript
history = []; // 空数组
embedding = [0.123, -0.456, 0.789, ...]; // 1536 维向量
```

---

### Step 3: 向量召回（首次无相关内容）

```sql
-- VectorStoreService.similaritySearch()
SELECT id, content, metadata,
       1 - (embedding <=> '[0.123, -0.456, ...]'::vector) as similarity
FROM knowledge_docs
WHERE user_id = 'user_123'  -- 多租户隔离
ORDER BY similarity DESC
LIMIT 20;
```

**返回结果**：
```json
{
  "results": [
    {
      "id": "doc_001",
      "content": "export const login = async (req, res) => { ... }",
      "metadata": { "source": "src/auth/login.ts", "line": 10 },
      "similarity": 0.23  // 相似度很低
    }
    // ... 其他 19 条（但都很不相关）
  ]
}
```

---

### Step 4: Rerank 精排（首次无意义）

```typescript
// RerankService.rerank()
if (!config.rerankEnabled) {
  return vectorResults.slice(0, 5);
}

// 如果启用，调用 Fast Model
const rerankPrompt = `
你是一个文档相关性评估专家。
用户查询: "你好"

以下是候选文档列表：
[doc_001]: export const login = async (req, res) => { ... }
[doc_002]: export const verifyToken = (token) => { ... }
...

请选出最相关的 5 条，返回 JSON:
{ "top_ids": ["id_1", "id_5", ...] }
`;
```

**LLM 响应**：
```json
{
  "top_ids": []  // "你好" 不相关，返回空数组
}
```

---

### Step 5: 组装 Context

```xml
<!-- ContextService.buildContext() -->
<root>
  <system_instructions>
    你是一个技术助手，帮助开发者解决编程问题。
  </system_instructions>

  <long_term_memory>
    <!-- 暂无摘要 -->
  </long_term_memory>

  <relevant_knowledge>
    <!-- Rerank 返回空，无知识文档 -->
  </relevant_knowledge>

  <conversation_history>
    <!-- 首次交互，无历史 -->
  </conversation_history>

  <user_query>
    你好
  </user_query>
</root>
```

---

### Step 6: 推理生成（Thinking Model）

```typescript
// LlmClientService.chatCompletion('THINKING', messages, { stream: true })
const response = await axios.post(
  `${config.thinkingModelBase}/chat/completions`,
  {
    model: config.thinkingModelName,
    messages: [{ role: 'user', content: xmlContext }],
    stream: true,
  },
  { responseType: 'stream' }
);
```

**流式响应**：
```
data: {"type":"token","content":"你"}
data: {"type":"token","content":"好"}
data: {"type":"token","content":"！"}
data: {"type":"token","content":"我"}
data: {"type":"token","content":"是"}
data: {"type":"token","content":"你"}
data: {"type":"token","content":"的"}
data: {"type":"token","content":"技"}
data: {"type":"token","content":"术"}
data: {"type":"token","content":"助"}
data: {"type":"token","content":"手"}
data: {"type":"done"}
```

---

### Step 7: 后台处理（Fire-and-Forget）

```typescript
// 保存用户消息
await this.prisma.message.create({
  data: {
    sessionId: dto.sessionId,
    role: 'user',
    content: '你好',
    metadata: { tokenCount: 2 },
  }
});

// 保存助手响应
await this.prisma.message.create({
  data: {
    sessionId: dto.sessionId,
    role: 'assistant',
    content: '你好！我是你的技术助手。',
    metadata: { tokenCount: 12 },
  }
});

// 加入 BullMQ 队列
await this.memoryQueue.add('GENERATE_EMBEDDING', {
  messageId: userMessage.id,
  content: '你好',
});
```

**当前数据库状态**：
```sql
-- sessions
| id                                  | user_id  | summary | created_at          |
|-------------------------------------|----------|---------|---------------------|
| 550e8400-e29b-41d4-a716-446655440000 | user_123 | NULL    | 2025-01-29 10:00:00 |

-- messages
| id        | session_id                           | role      | content                       | metadata                      | embedding |
|-----------|--------------------------------------|-----------|-------------------------------|-------------------------------|-----------|
| msg_001   | 550e8400-...                         | user      | 你好                          | {"tokenCount": 2}             | NULL      |
| msg_002   | 550e8400-...                         | assistant | 你好！我是你的技术助手。        | {"tokenCount": 12}            | NULL      |
```

---

## 🔥 阶段二：复杂查询 - 知识检索

### Step 8: 用户提出复杂问题

```bash
curl -X POST http://localhost:3000/api/v1/agent/chat \
  -H "Content-Type: application/json" \
  -d '{
    "sessionId": "550e8400-e29b-41d4-a716-446655440000",
    "message": "帮我看看 login 接口报 401 错误，可能是什么原因？"
  }'
```

---

### Step 9: 向量召回（高相似度）

```sql
SELECT id, content, metadata,
       1 - (embedding <=> '[0.234, -0.567, ...]'::vector) as similarity
FROM knowledge_docs
WHERE user_id = 'user_123'
ORDER BY similarity DESC
LIMIT 20;
```

**返回结果**（高相关性）：
```json
{
  "results": [
    {
      "id": "doc_001",
      "content": "export const login = async (req, res) => {\n  const { username, password } = req.body;\n  const user = await authenticateUser(username, password);\n  if (!user) {\n    return res.status(401).json({ error: 'Invalid credentials' });\n  }\n  const token = generateJWT(user);\n  res.json({ token });\n}",
      "metadata": { "source": "src/auth/login.ts", "line": 1 },
      "similarity": 0.89  // 高度相关！
    },
    {
      "id": "doc_002",
      "content": "export const verifyToken = (token) => {\n  try {\n    return jwt.verify(token, process.env.JWT_SECRET);\n  } catch (err) {\n    return null;\n  }\n}",
      "metadata": { "source": "src/middleware/auth.ts", "line": 10 },
      "similarity": 0.76
    },
    {
      "id": "doc_003",
      "content": "# Authentication API\n\n## POST /auth/login\n\nRequest body:\n```json\n{\n  \"username\": \"user@example.com\",\n  \"password\": \"password123\"\n}\n```\n\nReturns:\n- 200: { token: \"jwt_token\" }\n- 401: { error: \"Invalid credentials\" }",
      "metadata": { "source": "docs/api.md", "line": 15 },
      "similarity": 0.72
    }
    // ... 其他 17 条
  ]
}
```

---

### Step 10: Rerank 精排（Listwise 排序）

```typescript
// RerankService
const rerankPrompt = `
你是一个文档相关性评估专家。
用户查询: "帮我看看 login 接口报 401 错误，可能是什么原因？"

以下是候选文档列表：
[doc_001]: export const login = async (req, res) => { ... }
[doc_002]: export const verifyToken = (token) => { ... }
[doc_003]: # Authentication API ...
...

请选出最相关的 5 条，返回 JSON:
{ "top_ids": ["id_1", "id_5", ...] }
`;

const result = await this.llmClient.chatCompletion('RERANK', [
  { role: 'system', content: '你是一个文档相关性评估专家。' },
  { role: 'user', content: rerankPrompt }
], { responseFormat: 'json_object' });
```

**Fast Model 响应**：
```json
{
  "top_ids": ["doc_001", "doc_003", "doc_002", "doc_015", "doc_008"]
}
```

**排序逻辑**：
- `doc_001`: login 函数本身（最相关）
- `doc_003`: API 文档说明 401 错误（次相关）
- `doc_002`: JWT 验证逻辑（可能相关）

---

### Step 11: 组装 Context（带知识库）

```xml
<root>
  <system_instructions>
    你是一个技术助手，帮助开发者解决编程问题。
  </system_instructions>

  <long_term_memory>
    <!-- 暂无摘要（会话较短） -->
  </long_term_memory>

  <relevant_knowledge>
    <doc id="doc_001" source="src/auth/login.ts" line="1">
      export const login = async (req, res) => {
        const { username, password } = req.body;
        const user = await authenticateUser(username, password);
        if (!user) {
          return res.status(401).json({ error: 'Invalid credentials' });
        }
        const token = generateJWT(user);
        res.json({ token });
      }
    </doc>
    <doc id="doc_003" source="docs/api.md" line="15">
      # Authentication API
      ## POST /auth/login
      Returns:
      - 200: { token: "jwt_token" }
      - 401: { error: "Invalid credentials" }
    </doc>
    <doc id="doc_002" source="src/middleware/auth.ts" line="10">
      export const verifyToken = (token) => {
        try {
          return jwt.verify(token, process.env.JWT_SECRET);
        } catch (err) {
          return null;
        }
      }
    </doc>
  </relevant_knowledge>

  <conversation_history>
    <message role="user">你好</message>
    <message role="assistant">你好！我是你的技术助手。</message>
  </conversation_history>

  <user_query>
    帮我看看 login 接口报 401 错误，可能是什么原因？
  </user_query>
</root>
```

---

### Step 12: 推理生成（带引用）

```typescript
// Thinking Model 分析代码后生成响应
const response = `根据代码分析，login 接口返回 401 错误的可能原因有：

1. **用户名或密码错误**（最常见）
   - 代码位置：[\`src/auth/login.ts:7\`](doc_001)
   - \`authenticateUser\` 返回 null 时触发

2. **JWT_SECRET 未配置**
   - 代码位置：[\`src/middleware/auth.ts:12\`](doc_002)
   - 环境变量缺失会导致验证失败

建议检查：
- 确认数据库中用户凭证是否正确
- 检查 \`.env\` 文件中 \`JWT_SECRET\` 是否设置
- 查看服务器日志确认 \`authenticateUser\` 函数执行情况`;
```

**流式响应**（带引用标记）：
```
data: {"type":"token","content":"根据"}
data: {"type":"token","content":"代码"}
data: {"type":"token","content":"分析"}
...
data: {"type":"citation","docId":"doc_001","source":"src/auth/login.ts","line":7}
...
data: {"type":"done"}
```

---

### Step 13: 工具调用场景（长输出摘要）

假设用户要求查看完整的错误堆栈：

```bash
curl -X POST http://localhost:3000/api/v1/agent/chat \
  -d '{
    "sessionId": "550e8400-e29b-41d4-a716-446655440000",
    "message": "查看最近的错误日志"
  }'
```

**工具返回**（超长内容）：
```json
{
  "toolCall": "executeTerminalCommand",
  "output": "[2025-01-29 10:15:23] ERROR: Authentication failed
[2025-01-29 10:15:24] ERROR: Database connection timeout
...（2500+ 字符的完整日志）"
}
```

**触发 FOLD_TOOL_OUTPUT**：
```typescript
// MemoryProcessor.processFoldToolOutput()
if (message.content.length > 2000) {
  const summary = await this.llmClient.chatCompletion('THINKING', [
    {
      role: 'system',
      content: '你是一个日志摘要专家。请总结以下错误日志的关键信息。'
    },
    {
      role: 'user',
      content: message.content
    }
  ]);

  // 假设生成的摘要
  const summarized = `
最近 1 小时内的主要错误：
1. 认证失败（23 次）- 主要原因：密码错误
2. 数据库连接超时（5 次）- 时间段：10:15-10:20
3. JWT 验证失败（12 次）- 原因：token 过期
建议：检查数据库连接池配置和用户密码策略。
  `.trim();

  // 更新 DB：保存摘要 + 原始内容存 Blob
  await this.prisma.message.update({
    where: { id: message.id },
    data: {
      content: summarized,
      metadata: {
        isFolded: true,
        originalArtifactId: 's3://logs/original_20250129.log',
        tokenCount: 150, // 摘要后只有 150 tokens
      }
    }
  });
}
```

---

## 📊 阶段三：会话增长 - Token 累积

### Step 14: 多轮交互后

假设用户进行了 **45 轮对话**（约 90,000 tokens）：

```sql
-- messages 表状态
SELECT COUNT(*) as message_count,
       SUM(metadata->>'tokenCount') as total_tokens
FROM messages
WHERE session_id = '550e8400-e29b-41d4-a716-446655440000';
```

**结果**：
```
message_count: 90
total_tokens: 92345
```

**数据库状态**：
```sql
-- sessions
| id                    | summary                     |
|-----------------------|-----------------------------|
| 550e8400-...          | NULL                        | (尚未压缩)

-- messages (部分展示)
| id    | role      | content                    | metadata->>'tokenCount' |
|-------|-----------|----------------------------|-------------------------|
| msg_089 | user    | 帮我优化这个数据库查询      | 45                      |
| msg_090 | assistant | SELECT * FROM users ...   | 1234                    |
```

---

### Step 15: 触发压缩阈值

用户发送第 **46 条消息**（假设 1,500 tokens）：

```bash
curl -X POST http://localhost:3000/api/v1/agent/chat \
  -d '{
    "message": "如何在生产环境监控这个接口的性能？"
  }'
```

**后台计算总 Token**：
```typescript
// MemoryService.checkCompactThreshold()
const totalTokens = await this.prisma.message.aggregate({
  where: { sessionId: dto.sessionId },
  _sum: {
    // 计算 metadata.tokenCount 的总和
  }
});

if (totalTokens > 100000) {
  // 🔥 触发压缩！
  await this.memoryQueue.add('COMPACT_SESSION', {
    sessionId: dto.sessionId,
    totalTokens: 101234,
  });
}
```

---

## 🗜️ 阶段四：会话压缩

### Step 16: 读取全部历史

```typescript
// MemoryProcessor.processCompactSession()
const session = await this.prisma.session.findUnique({
  where: { id: job.data.sessionId },
  include: {
    messages: {
      orderBy: { createdAt: 'asc' },
    },
  },
});

const fullHistory = session.messages.map(msg => ({
  role: msg.role,
  content: msg.content,
})).join('\n');
```

**原始内容**（约 100K tokens）：
```
user: 你好
assistant: 你好！我是你的技术助手。
user: 帮我看看 login 接口报 401 错误
assistant: 根据代码分析...
user: 查看最近的错误日志
assistant: 主要错误：1. 认证失败（23 次）...
...
（共 90 条消息）
```

---

### Step 17: 生成压缩摘要（Thinking Model）

```typescript
// 调用最强的推理模型
const summaryPrompt = `
你是一个技术会话摘要专家。请将以下对话历史压缩成高质量的摘要。

**要求**：
1. 保留关键的技术决策和结论
2. 记录用户的主要问题和解决方案
3. 忽略寒暄和无关对话
4. 使用清晰的结构化格式

**对话历史**：
${fullHistory}

**请生成摘要**（控制在 2000 tokens 以内）：
`;

const newSummary = await this.llmClient.chatCompletion('THINKING', [
  {
    role: 'system',
    content: '你是一个技术文档专家，擅长提取关键信息。'
  },
  {
    role: 'user',
    content: summaryPrompt
  }
], { maxTokens: 2000 });
```

**Thinking Model 生成的摘要**（约 1,800 tokens）：
```markdown
# 技术支持会话摘要

## 1. 认证问题（第 2-15 轮）
**问题**：login 接口返回 401 错误
**原因分析**：
- 用户凭证错误（主要）
- JWT_SECRET 环境变量未配置（次要）
**解决方案**：
- 验证数据库用户密码哈希
- 在 `.env` 中添加 `JWT_SECRET=your_secret_key`

## 2. 错误日志分析（第 16-25 轮）
**发现的问题**：
1. 认证失败 23 次（密码策略过严）
2. 数据库连接超时 5 次（连接池耗尽）
3. JWT token 频繁过期（过期时间太短：15 分钟）
**优化措施**：
- 调整连接池配置：`max: 20, idleTimeoutMillis: 30000`
- 延长 token 有效期至 24 小时

## 3. 数据库查询优化（第 26-40 轮）
**慢查询**：
```sql
SELECT * FROM users WHERE email = '...';  -- 全表扫描
```
**优化方案**：
- 添加索引：`CREATE INDEX idx_users_email ON users(email);`
- 查询时间从 850ms 降至 12ms

## 4. API 性能监控方案（第 41-46 轮）
**建议工具**：
- Prometheus + Grafana（指标监控）
- Winston + ELK（日志聚合）
**关键指标**：
- 响应时间 P95 < 200ms
- 错误率 < 0.1%
- QPS 峰值：450/s

## 待办事项
- [ ] 实施数据库索引优化
- [ ] 配置 Prometheus 监控
- [ ] 更新 API 文档中的错误码说明
```

---

### Step 18: 执行压缩（保留最近 50 轮）

```typescript
// 计算要保留的消息
const messages = session.messages;
const totalMessages = messages.length;

// 保留规则：
// 1. 最近 50 轮 = 100 条消息（user + assistant）
// 2. 或最多 50,000 tokens
let toKeep = [];
let currentTokens = 0;

for (let i = totalMessages - 1; i >= 0; i--) {
  const msgTokens = messages[i].metadata.tokenCount;

  if (toKeep.length >= 100 || currentTokens + msgTokens > 50000) {
    break;
  }

  toKeep.unshift(messages[i].id);
  currentTokens += msgTokens;
}

const toDelete = messages
  .filter(m => !toKeep.includes(m.id))
  .map(m => m.id);

// 执行事务
await this.prisma.$transaction([
  // 更新摘要
  this.prisma.session.update({
    where: { id: session.id },
    data: { summary: newSummary }
  }),
  // 删除旧消息
  this.prisma.message.deleteMany({
    where: {
      id: { in: toDelete }
    }
  })
]);
```

**压缩结果**：
```
原始消息数：90 条
原始 Token：101,234
压缩后消息数：50 条（最近 25 轮）
压缩后 Token：48,567
压缩比：52%
```

---

### Step 19: 压缩后的数据库状态

```sql
-- sessions
| id                    | summary                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 550e8400-...          | # 技术支持会话摘要\n\n## 1. 认证问题（第 2-15 轮）\n**问题**：login 接口返回 401 错误\n**原因分析**：\n- 用户凭证错误（主要）\n- JWT_SECRET 环境变量未配置（次要）\n**解决方案**：\n- 验证数据库用户密码哈希\n- 在 `.env` 中添加 `JWT_SECRET=your_secret_key`\n\n## 2. 错误日志分析（第 16-25 轮）\n**发现的问题**：\n1. 认证失败 23 次（密码策略过严）\n2. 数据库连接超时 5 次（连接池耗尽）\n3. JWT token 频繁过期（过期时间太短：15 分钟）\n**优化措施**：\n- 调整连接池配置：`max: 20, idleTimeoutMillis: 30000`\n- 延长 token 有效期至 24 小时\n\n...（完整摘要）                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

-- messages（只保留最近 50 条）
| id    | role      | content                    | created_at        |
|-------|-----------|----------------------------|-------------------|
| msg_041 | user    | 如何优化数据库查询？        | 2025-01-29 11:20:00 |
| msg_042 | assistant | 建议添加索引...             | 2025-01-29 11:20:15 |
| ...   | ...       | ...                        | ...               |
| msg_090 | user    | 如何监控性能？              | 2025-01-29 12:05:00 |
```

---

## 🔄 阶段五：压缩后的交互

### Step 20: 用户继续提问（依赖历史摘要）

```bash
curl -X POST http://localhost:3000/api/v1/agent/chat \
  -d '{
    "sessionId": "550e8400-e29b-41d4-a716-446655440000",
    "message": "刚才提到的连接池配置具体怎么写？"
  }'
```

---

### Step 21: 组装 Context（带摘要）

```xml
<root>
  <system_instructions>
    你是一个技术助手。
  </system_instructions>

  <long_term_memory>
    <!-- 🎯 关键：这里填充了压缩摘要 -->
    # 技术支持会话摘要

    ## 1. 认证问题（第 2-15 轮）
    **问题**：login 接口返回 401 错误
    **原因分析**：
    - 用户凭证错误（主要）
    - JWT_SECRET 环境变量未配置（次要）
    **解决方案**：
    - 验证数据库用户密码哈希
    - 在 `.env` 中添加 `JWT_SECRET=your_secret_key`

    ## 2. 错误日志分析（第 16-25 轮）
    **优化措施**：
    - 调整连接池配置：`max: 20, idleTimeoutMillis: 30000`
    - 延长 token 有效期至 24 小时

    ...
  </long_term_memory>

  <relevant_knowledge>
    <!-- 向量搜索结果 -->
  </relevant_knowledge>

  <conversation_history>
    <!-- 🎯 只有最近 50 条消息 -->
    <message role="user">如何在生产环境监控这个接口的性能？</message>
    <message role="assistant">建议使用 Prometheus + Grafana...</message>
  </conversation_history>

  <user_query>
    刚才提到的连接池配置具体怎么写？
  </user_query>
</root>
```

---

### Step 22: 推理生成（跨压缩边界）

**Thinking Model 响应**：

```
根据之前的讨论，连接池配置如下：

**PostgreSQL (pg)**:
\`\`\`javascript
const { Pool } = require('pg');

const pool = new Pool({
  user: 'postgres',
  host: 'localhost',
  database: 'mydb',
  password: 'secret',
  port: 5432,
  max: 20,                          // 最大连接数
  idleTimeoutMillis: 30000,         // 空闲连接超时
  connectionTimeoutMillis: 2000,    // 连接超时
});
\`\`\`

**MongoDB (Mongoose)**:
\`\`\`javascript
mongoose.connect(uri, {
  maxPoolSize: 20,
  minPoolSize: 5,
  socketTimeoutMS: 30000,
  serverSelectionTimeoutMS: 2000,
});
\`\`\`

**关键参数说明**：
- `max` / `maxPoolSize`: 根据数据库核心数设置（通常 `CPU核心数 × 2`）
- `idleTimeoutMillis`: 防止长时间占用连接
- `connectionTimeoutMillis`: 快速失败，避免请求堆积

可以根据你的 QPS（假设 450/s）和平均响应时间（50ms）计算最优连接数。
```

**🎯 关键点**：AI **成功引用了压缩前的内容**，这证明了：
1. 摘要质量足够高
2. Thinking Model 能理解上下文连续性
3. 用户感知不到压缩发生

---

## 📈 性能与成本分析

### 请求延迟分解（单次复杂查询）

```
┌─────────────────────────────────────────────┐
│ 总延迟：~1.8 秒                              │
├─────────────────────────────────────────────┤
│ 1. DB 查询历史：        30ms                │
│ 2. Embedding API：      500ms               │
│ 3. 向量搜索：           50ms                │
│ 4. Rerank (可选)：      1000ms              │
│ 5. 组装 Context：       10ms                │
│ 6. Thinking Model（首个 token）：200ms      │
└─────────────────────────────────────────────┘
```

### 成本分析（按天）

**假设**：
- 每天活跃会话：1,000 个
- 平均每会话 20 轮对话
- 10% 的会话触发工具调用（需要摘要）
- 5% 的会话触发压缩

| 项目 | 次数/天 | 单次成本 | 日成本 | 月成本 |
|------|---------|---------|--------|--------|
| Thinking Model（推理） | 20,000 | $0.002 | $40 | $1,200 |
| Thinking Model（工具摘要） | 200 | $0.003 | $0.60 | $18 |
| Thinking Model（压缩） | 50 | $0.10 | $5 | $150 |
| Fast Model（Rerank） | 18,000 | $0.0003 | $5.40 | $162 |
| Embedding API | 20,000 | $0.0001 | $2 | $60 |
| **总计** | - | - | **$53** | **$1,590** |

### 优化后（关闭 Rerank）

| 项目 | 日成本 | 月成本 | 节省 |
|------|--------|--------|------|
| **总计** | $47.60 | $1,428 | **10%** |

---

## 🎯 关键设计决策总结

### 1. 为什么摘要用 Thinking Model？
```
✅ 摘要质量直接影响后续查询准确性
✅ 摘要会被反复使用（摊薄成本）
✅ 压缩是不可逆的，必须一次做对
```

### 2. 为什么 Rerank 可配置？
```
✅ 开发环境可以关闭以降低成本
✅ 简单查询向量搜索已足够
✅ 为未来的自动策略预留空间
```

### 3. 为什么是 100K 触发压缩？
```
✅ 留出足够的增长空间（50K 保留 + 50K 新增）
✅ 避免频繁压缩（影响用户体验）
✅ 大多数单次查询在 5K tokens 以内
```

### 4. 为什么保留 50 轮而非固定 Token？
```
✅ 轮数 = 短期记忆容量（心理学：7±2，放宽到 50）
✅ Token 上限防止边缘情况（如长代码输出）
✅ 双重保护确保压缩后的可控性
```

---

## 🚀 扩展性考虑

### 未来可能的优化

1. **智能压缩触发**：
```typescript
// 根据查询模式决定是否压缩
const shouldCompact =
  totalTokens > 100000 ||
  (recentQueries.length > 10 && isTopicDrift()); // 话题漂移检测
```

2. **分级摘要策略**：
```typescript
// 第一级：每 50 轮生成小摘要
// 第二级：每 5 个小摘要合并为大摘要
// 树状结构而非线性覆盖
```

3. **混合 Rerank 策略**：
```typescript
// 简单查询：向量搜索 Top-5
// 中等查询：Fast Model Rerank
// 复杂查询：Thinking Model Rerank
```

---

**文档版本**：v1.0
**最后更新**：2025-01-29
**作者**：Nexus-Context Team