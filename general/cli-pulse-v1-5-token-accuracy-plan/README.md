# CLI Pulse V1.5 Token Accuracy Plan

> **版本:** 1.1
**日期:** 2026-04-07
**作者:** Claude + Gemini 3.1 Pro
**状态:** Draft — 待确认

---

## 1. 背景与问题

CLI Pulse v1.4.1 已发布全平台（macOS/iOS/watchOS/Androi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Pulse v1.5 技术方案：Token 精准计量、订阅费追踪与历史成本分析

**版本:** 1.1
**日期:** 2026-04-07
**作者:** Claude + Gemini 3.1 Pro
**状态:** Draft — 待确认

---

## 1. 背景与问题

CLI Pulse v1.4.1 已发布全平台（macOS/iOS/watchOS/Android），核心 quota/tier 追踪功能正常工作。但与上游 CodexBar 对比，存在以下差距：

### 差距 1：Token 统计不精确
- **CLI Pulse**：`LocalScanner` 通过 `ps` 检测进程，用 CPU + 运行时长估算 token 量 → 偏差很大
- **CodexBar**：直接解析 `~/.codex/sessions/YYYY/MM/DD/*.jsonl` 和 Claude 日志，获取精确的 `input_tokens + output_tokens + cached_tokens`
- 导致 `today_usage == week_usage`（没有历史数据），Cost Summary 全显示 `<$0.01`

### 差距 2：无历史成本追踪
- CodexBar 有 `CostUsageScanner` + `CostUsageCache` + `CostUsagePricing` 完整链路
- CLI Pulse 只有当前快照，无按天/按模型的成本分析

### 差距 3：Xcode 控制台错误（轻微）
- `NSSecureCoding` 警告：App Group UserDefaults IPC 序列化未指定具体类型
- `os.log` decode range 错误：Logger 字符串插值路径过长

---

## 2. 目标

1. **精准 Token 计量**：从本地 JSONL 日志获取真实 token 数据
2. **历史按日分析**：支持 daily/weekly/monthly breakdown，按模型展示
3. **跨设备同步**：历史数据上传 Supabase，手机也能看
4. **修复控制台警告**

---

## 3. 实施计划

### 阶段一：集成 CostUsageScanner（2-3 天）

**目标**：替换 LocalScanner 的估算逻辑，改为解析本地日志获取精确 token 数据。

**步骤**：

1. **新增 `CostUsageScanner.swift`**
   - 路径：`CLIPulseCore/Sources/CLIPulseCore/CostUsageScanner.swift`
   - 参考：`codexbar/Sources/CodexBarCore/Vendored/CostUsage/CostUsageScanner.swift`
   - 扫描路径：
     - Codex: `~/.codex/sessions/YYYY/MM/DD/*.jsonl`
     - Claude: `~/Library/Application Support/Claude/projects/*/sessions/*.jsonl`
   - 解析逻辑：
     ```
     每行 JSON → 提取 type == "event_msg" && payload.type == "token_count"
     → 取 total_token_usage.{input_tokens, cached_input_tokens, output_tokens}
     → 增量 delta 计算（避免重复计数）
     → 按 timestamp 归入日期桶
     ```

2. **新增 `CostUsageCache.swift`**
   - 路径：`CLIPulseCore/Sources/CLIPulseCore/CostUsageCache.swift`
   - 参考：`codexbar/Sources/CodexBarCore/Vendored/CostUsage/CostUsageCache.swift`
   - 每个文件记录：`mtime`, `size`, `parsedBytes`, `lastModel`, `lastTotals`
   - 缓存位置：`~/Library/Caches/CLIPulse/cost-usage/`
   - 增量扫描：只解析 `parsedBytes` 之后的新内容

3. **集成到 DataRefreshManager**
  

*[truncated — see source for full prompt]*