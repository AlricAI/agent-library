# DEVELOPMENT PLAN V1.9

> > 审查日期: 2026-04-16 | 当前版本: v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Pulse v1.9 开发计划书

> 审查日期: 2026-04-16 | 当前版本: v1.8 (Build 27, 已提交 App Store 审核)
> Codex Review: 已通过审查并修正（2026-04-16）

---

## 一、项目健康诊断

### 当前状态: 稳定，可发版

| 维度 | 状态 | 详情 |
|------|------|------|
| macOS 编译 | ✅ | BUILD SUCCEEDED (全 scheme) |
| Swift 测试 | ✅ | 186/186 通过 |
| Python 测试 | ✅ | 27/27 通过 |
| Android 编译 | ⚠️ | 开发机无 Java，CI 正常 |
| App Store | ⏳ | v1.8 Build 27 审核中 |
| Provider 覆盖 | ✅ | 26 个 Provider（含新增 GLM）|

### 发现的问题（按优先级排列，经 Codex 验证）

#### P1 — 质量问题

1. **Android 数据层缺少单元测试**
   - 66 个 Kotlin 文件仅 8 个测试文件 + 1 个 Rule（全在 `ui/` 包下）
   - `data/collector/`、`data/remote/`、`data/local/` 零覆盖
   - Room 目前版本 1 无迁移，但 CollectorManager 逻辑需验证
   - **修复**: 增加数据层测试（CollectorManager + 5 个核心 Collector）

2. **UI 硬编码字符串绕过 i18n**
   - iOS: TeamView.swift (8处), iOSLoginView.swift (2处)
   - Android: SettingsScreen.kt (15+处), TeamScreen.kt, SubscriptionScreen.kt
   - 平台间本地化覆盖不一致：Android 缺少 Spanish (`values-es/`)，Swift 有 `es.lproj`
   - **修复**: 迁移到各平台 L10n 系统 + 对齐语言矩阵

3. **Android 平台功能缺失（与 iOS 不对齐）**
   - 缺少: 团队角色变更 UI、待处理邀请列表、导出功能入口
   - `ExportUtil.kt` 存在但未被任何 UI/ViewModel 调用（Codex 验证: 无 caller）
   - 注意: Android 已有团队列表/成员列表/创建/邀请/移除功能，差距比预期小
   - **修复**: 补齐 3 项缺失 UI

#### P2 — 改进项

4. **错误提示不统一** — Android 无全局 Snackbar 系统（各页面内联处理），macOS 在 MenuBarView 处理
5. **Accessibility 标签缺失** — Android 多处 `contentDescription = null`，Swift 缺少 `accessibilityLabel`
6. **macOS Settings 缺少 Webhook 配置 UI** — iOS/Android 已有，macOS SettingsTab.swift 遗漏

> **Codex 修正**: 原计划中 "android/local.properties 未 gitignore" 为误报（已在 `android/.gitignore` 中）；
> "README 仅覆盖 Swift 和 Python" 为误报（已包含 Android 指令）。

---

## 二、v1.9 新功能规划

### 功能 A: 成本预测与智能预算

**目标**: 根据历史用量趋势，预测本月剩余花费。

**前置条件** (Codex 发现):
- Android 缺少 `DailyUsage` 客户端模型/Repository/ViewModel — 需先补齐
- `AlertGenerator.swift` 仅限 macOS — 预测告警需走跨平台路径（后端 RPC 或 helper）

**实现范围**:
- Phase 1 (Apple only): 基于 `daily_usage_metrics` 客户端线性回归，复用现有 `APIClient.fetchDailyUsage`
- Phase 2 (Android): 补齐 DailyUsage 数据管道后接入
- 在 Overview Dashboard 显示 "月末预计花费" 卡片（标注"预估"+ 置信

*[truncated — see source for full prompt]*