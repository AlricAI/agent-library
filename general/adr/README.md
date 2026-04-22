# Adr

> > Lumineer – Intelligent Course Discovery System
> キャプストーンプロジェクトのアーキテクチャ判断記録

---

## ADR-001: システム境界 — モジュラーモノリス

### Status: Accepted

### Context
仕

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture Decision Records (ADR)

> Lumineer – Intelligent Course Discovery System
> キャプストーンプロジェクトのアーキテクチャ判断記録

---

## ADR-001: システム境界 — モジュラーモノリス

### Status: Accepted

### Context
仕様書の成果物3に「Full Executable Code (Microservice)」と記載されている。しかしプロジェクトは1人開発、デモ用途であり、マイクロサービスの恩恵（独立スケール、独立デプロイ、チーム分離）を享受する条件が揃っていない。

### Decision
**モジュラーモノリス** + Docker Compose を採用する。

- 内部をモジュール（ingestion, search, recommendation, agents）に明確に分割
- Docker Composeでパッケージング（app + vectordb + frontend の構成）
- モジュール間は関数呼び出し（プロセス内通信）

### Alternatives Considered

| 選択肢 | 棄却理由 |
|--------|---------|
| **マイクロサービス** | 1人開発でサービス分割の恩恵がない。分散トランザクション・サービス間通信の複雑さが開発速度を下げる。Anti-pattern「分散モノリス」のリスク |
| **モノリス（分割なし）** | 内部構造が曖昧になり、将来の拡張が困難。設計判断力を示せない |
| **Kubernetes** | 3-4コンテナの管理にK8sはオーバーキル。Docker Composeで十分 |

### Consequences
- ✓ 開発速度を維持しつつ、内部の責務分離を実現
- ✓ 設計ドキュメントで「なぜマイクロサービスにしなかったか」をトレードオフとして説明可能
- ✓ 将来のマイクロサービス化が容易（モジュール境界が明確）
- ✗ 仕様書の「Microservice」文言との整合性はヒアリングで確認が必要

---

## ADR-002: バックエンド構造 — クリーンアーキテクチャ

### Status: Accepted

### Context
AI/LLMシステムでは外部依存（LLMプロバイダー、VectorDB、埋め込みモデル）が多く、これらは変更される可能性が高い。ビジネスロジック（コース検索、スキルギャップ分析、学習パス生成）を外部変更から保護する設計が必要。

### Decision
**クリーンアーキテクチャ**を採用する。

```
app/
├── domain/                 # ★核心（外部に一切依存しない）
│   ├── entities/           #   Course, LearningPath, SkillGap
│   ├── ports/              #   LLMPort, VectorStorePort, EmbeddingPort
│   └── usecases/           #   search_courses, analyze_skill_gap,
│                           #   generate_learning_path
├── infrastructure/         # 外部接続の具体実装
│   ├── llm/                #   LLMアダプタ（OpenAI等）
│   ├── vectordb/           #   VectorDBアダプタ
│   ├── embeddings/         #   埋め込みモデルアダプタ
│   └── ingestion/          #   CSVLoader, DataCleaner
├── interfaces/             # 入力アダプタ
│   └── api/                #   API Router
├── agents/                 # エージェント群（usecasesを使うオーケストレーション層）
│   ├── retrieval_agent.py
│   ├── skill_gap_agent.py
│   └── learning_path_agent.py
└── config/                 # DI設定
    └── container.py

*[truncated — see source for full prompt]*