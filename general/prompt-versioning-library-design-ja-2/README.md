# Prompt Versioning Library Design Ja

> ## 背景

このリポジトリでは、`variables_info.txt` の説明文や `sparql.yaml` の description がパイプライン実行中に更新される。
単純に GitHub 上の diff だけで追うと、次の情報を横断して見るのが難しい。

- どの prompt fam

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt Versioning Library Design

## 背景

このリポジトリでは、`variables_info.txt` の説明文や `sparql.yaml` の description がパイプライン実行中に更新される。
単純に GitHub 上の diff だけで追うと、次の情報を横断して見るのが難しい。

- どの prompt family/version が使われたか
- どの入力コンテキストで生成されたか
- 生成結果が検証で通ったか
- 何が reason で修正されたか
- 最終的に `variables_info.txt` のどの行が何から何に変わったか

さらに現状は、prompt の管理レイヤーと実行レイヤーが分かれている。

- `monitoring/prompt-registry.json` と `monitoring/prompts/*.md` には prompt 系の履歴がある
- 実際のパイプライン実行では `scripts/incremental_variable_docs.rb` に heredoc の prompt が埋め込まれている

つまり、現状の `prompt-registry` は「閲覧・運用メタデータ」であって、「実行時の source of truth」ではない。

## 結論

設計できる。  
ただし「prompt のバージョン管理ライブラリ」として作るより、以下をまとめて扱う **prompt lineage library** として設計した方がよい。

- prompt versioning
- prompt rendering
- run logging
- evaluation logging
- artifact revision logging

この最後の artifact revision logging がないと、知りたい「説明文の更新履歴」が取れない。

## 設計原則

1. Prompt は immutable にする
2. 実行ログは append-only にする
3. 出力ファイルの更新は artifact revision として記録する
4. 「prompt version」と「artifact revision」を別概念にする
5. Git は保管場所の一つとして使うが、履歴参照は library の API/CLI で行う

## 追いたいエンティティ

### 1. PromptFamily

同じ用途の prompt 群。

例:

- `variable-line`
- `query-description`
- `infer-variables`
- `repair-variable-description`
- `repair-query-description`

Family は immutable な version 集合に加えて、`current` `best` `prod` のような
**名前付き ref** を持つ。`latest` は永続化せず、作成日時から導出する派生 ref として扱う。

### 2. PromptVersion

1つの family に属する immutable な version。

持つべき属性:

- `id`
- `family_id`
- `label`
- `parent_id`
- `status`
- `created_at`
- `author`
- `hypothesis`
- `template_path`
- `input_schema`
- `output_schema`
- `tags`

### 3. PromptRun

ある prompt version を 1 回実行した記録。

持つべき属性:

- `run_id`
- `family_id`
- `version_id`
- `stage`
- `dataset`
- `target_kind`
- `target_id`
- `model_backend`
- `model_name`
- `started_at`
- `finished_at`
- `input_snapshot`
- `rendered_prompt`
- `raw_output`
- `normalized_output`
- `token_usage`
- `latency_ms`
- `status`

### 4. EvaluationResult

生成結果に対する検証。

例:

- round-trip 成功/失敗
- templated 率
- raw token 混入
- 

*[truncated — see source for full prompt]*