# Building Claude Code Agent Teams Skills And Monitoring Dashboard

> # **はじめに**

最近、Claude CodeのAgent Teams機能に注目しており、特にプロジェクト初期開発や中〜大規模なコード改修といった、チーム体制が求められる開発において、高効率な並列作業が実現できることを実感しています。

一方で、Claude Codeのターミナル上では以下の点

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Code Agent Teams Skillsの自作と監視ダッシュボードの紹介

# **はじめに**

最近、Claude CodeのAgent Teams機能に注目しており、特にプロジェクト初期開発や中〜大規模なコード改修といった、チーム体制が求められる開発において、高効率な並列作業が実現できることを実感しています。

一方で、Claude Codeのターミナル上では以下の点が課題と感じています。

- Team Lead（チームリード）からTeammates（チームメンバー）へのタスクアサイン方法が見えづらい
- エージェント間の協調コミュニケーションの流れが追いにくい
- 各Agentがどのように思考・行動しているかのプロセスが可視化されていない

これらの課題を踏まえ、本記事では以下の2点をご紹介します。

1. **Teamworks Skill** — 要件に基づいてAgent Teamsの体制を自律的に設計・提案するスキル
2. **Agent Teams監視ダッシュボード** — Agentの動きをリアルタイムで可視化するダッシュボード

本プロジェクトは、Github上以下のリポジトリを公開しています。
https://github.com/JustinWangJP/cc-agent-teams-action-monitor

---

# **Teamworks Skillとは？**

### **作成の目的と背景**

**目的：** Agent Teamsの作業開始前に、要件・開発ボリューム・タスク詳細・ドメイン専門家定義・コミュニケーション経路などを考慮したチーム体制をAIが自動生成し、ユーザーが承認ベースでプロジェクトを立ち上げられるようにすることです。

**一般的な問題点：** 「〇〇機能を開発したいです。フロントエンド1名、バックエンド1名で開発してください。」といった漠然とした指示では、最適な体制構築が困難です。この例では、フロントエンドとバックエンドエージェントでは、実行時にどのようなロールで、どのSkillsとMCPを使って、具体のタスクを実行するのか、わからないと思います。基本的に利用しているモデルがClaude Codeプロジェクトをスキャンして、利用できるものをモデルで自動判別してしまい、タスク量に応じて定性的のチーム作成が難しいと思われます。

### **解決できること**

- **汎用エージェントの限界を超える専門特化：**

    Claude CodeでVibe Codingを行う場合、リポジトリにSubAgentの定義やSkillsがすでに存在していても、チームメイト（SubAgents）をすべて汎用エージェント（General-Purpose）として動かすだけでは、専門スキル（Skills）や特殊ツール（MCP Servers）を十分に活用できません。

    Teamworks Skillでは、具体的なロールに基づいてどのAgent Type（`frontend`・`qa`・`multi-agent-coordinator`など）として動作するか、どのSkillsとMCP Serversを利用するかを、必要な範囲で綿密に定義します。そのうえで、Agent Teamsモードでその定義済みエージェントとして作業を実行します。

- **YAGNI原則に基づく最小構成の体制設計：**

    開発要件・タスク詳細に基づき、担当Section（`Product Design` / `Product Build`）と各Sectionのメンバープールから、YAGNI（You Aren't Gonna Need It）原則を徹底してアサインします。開発領域・ドメイン単位で専門エージェント（単体または複数）をアサインします。

    > **YAGNI徹底の理由：** 複数のTeammatesが動作する場合、そのエージェント数に比例してトークン消費量が増加します。また、自律エージェントの管理コストも上昇します。費用対効果の観点から、必要最小限のエージェント定義が最も効率的です。
    >
- **コミュニケーション経路の明確化：**

    Agent Teamsでは、基本的にメインセッション（Team Lead = あなた）から各Teammate（チームメンバー）へタスクを割り当てます。大規模なエージェント開発になると、planモードですべてのエージェントへ個別に許可を与えることは非効率です。そのため、**Section間通信はSectionリード同士のみ**に限定し、メンバー間の直接横断通信は禁止しています。これにより、あなたは各Section

*[truncated — see source for full prompt]*