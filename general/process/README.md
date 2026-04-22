# Process

> 本文档展示系统从用户首次交互到会话压缩的完整生命周期，包含代码示例、数据状态和系统行为。

---

## 📚 场景设定

**用户场景**：开发者正在调试一个 Node.js 项目的登录接口问题

**知识库已有内容**：
- `src/auth/login.ts` - 登录逻辑代码
- `sr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
  return vectorResults.slice

*[truncated — see source for full prompt]*