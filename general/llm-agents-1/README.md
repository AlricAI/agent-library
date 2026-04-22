# Llm Agents

> ```javascript
while (true) {
    const response = await model(messages, tools);
    if (response.stop_reason !== "tool_use") {
        return response

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agents的核心

```javascript
while (true) {
    const response = await model(messages, tools);
    if (response.stop_reason !== "tool_use") {
        return response.text;
    }
    const results = await execute(response.tool_calls);
    messages.push(results);
}
```

## 模型即代理

**~200 行代码，4 个工具，所有编程 Agent 的本质。**

Claude Code 的秘密？**没有秘密。**

剥去 CLI 外观、进度条、权限系统，剩下的出奇简单：一个让模型持续调用工具直到任务完成的循环。

## 核心洞察

传统助手：

```text
用户 -> 模型 -> 文本回复
```

Agent 系统：

```text
用户 -> 模型 -> [工具 -> 结果]* -> 回复
                     ^_________|
```

星号很重要。模型**反复**调用工具，直到它决定任务完成。这将聊天机器人转变为自主代理。

**核心洞察**：模型是决策者，代码只提供工具并运行循环。

## 四个核心工具

Claude Code 有约 20 个工具，但 4 个覆盖 90% 的场景：

| 工具 | 用途 | 示例 |
|------|------|------|
| `bash` | 运行命令 | `npm install`, `git status` |
| `read_file` | 读取内容 | 查看 `src/index.ts` |
| `write_file` | 创建/覆盖 | 创建 `README.md` |
| `edit_file` | 精确修改 | 替换一个函数 |

有了这 4 个工具，模型可以：
- 探索代码库（`bash: find, grep, ls`）
- 理解代码（`read_file`）
- 做出修改（`write_file`, `edit_file`）
- 运行任何东西（`bash: python, npm, make`）

## Agent 循环

整个 Agent 在一个函数里：

```javascript
async function agentLoop(messages) {
    while (true) {
        // 1. 询问模型
        const response = await client.messages.create({
            model: MODEL,
            system: SYSTEM,
            messages: messages,
            tools: TOOLS
        });

        // 2. 打印文本输出
        for (const block of response.content) {
            if (block.text) {
                console.log(block.text);
            }
        }

        // 3. 如果没有工具调用，完成
        if (response.stop_reason !== "tool_use") {
            return messages;
        }

        // 4. 执行工具，继续循环
        const results = [];
        for (const tc of response.tool_calls) {
            const output = await executeTool(tc.name, tc.input);
            results.push({
                type: "tool_result",
                tool_use_id: tc.id,
                content: output
            });
        }

        messages.push({
            role: "assistant",
            content: response.content
     

*[truncated — see source for full prompt]*