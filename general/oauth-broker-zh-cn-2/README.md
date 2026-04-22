# Oauth Broker.Zh CN

> English: [oauth-broker.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GitHub OAuth Broker（可选）

English: [oauth-broker.md](oauth-broker.md)

该能力仅用于简化 GitHub OAuth 登录体验，不在记忆同步数据链路中。

## 最低步骤（推荐）

1. 先部署 broker（平台一键入口或 CLI）。
2. 拿到 broker URL（例如：`https://xxx.workers.dev`）。
3. 在 WebUI `Configuration` 中：
   - 填 `OAuth Broker URL`
   - 点击 `Sign In via GitHub`

记忆同步仍是用户机器上的本地 Git 操作。

健康检查（将 `<BROKER_URL>` 替换为你的地址）：

```bash
curl -sS -X POST "<BROKER_URL>/v1/github/device/start" \
  -H 'Content-Type: application/json' \
  -d '{}' | jq .
```

预期：返回类似 `missing client_id` 的 JSON 错误（说明 broker 端点可达）。

## 平台一键部署入口

- Cloudflare Worker：
  - `https://deploy.workers.cloudflare.com/?url=https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/cloudflare-worker`
  - 如果 Cloudflare 出现通用 monorepo 警告页面，可继续；该模板已包含 `wrangler.toml`。
- Vercel：
  - `https://vercel.com/new/clone?repository-url=https://github.com/NoPKT/omnimem&root-directory=examples%2Foauth-broker%2Fvercel&project-name=omnimem-oauth-broker`
- Railway：
  - `https://railway.app/new/template?template=https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/railway`
- Fly.io 模板参考：
  - `https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/fly`

## 部署页面需要填写什么

- 通用必填：
  - `GITHUB_OAUTH_CLIENT_ID`（GitHub OAuth App 的 client id）
- Cloudflare Worker：
  - Worker Settings -> Variables and Secrets 中设置 `GITHUB_OAUTH_CLIENT_ID`。
- Vercel：
  - Project Settings -> Environment Variables 中增加 `GITHUB_OAUTH_CLIENT_ID`（至少 Production）。
- Railway：
  - Variables 页增加 `GITHUB_OAUTH_CLIENT_ID`。
- Fly.io：
  - App 名称可自定义但需唯一。
  - 用 `fly secrets set GITHUB_OAUTH_CLIENT_ID=...` 设置 secret。

## CLI 兜底（可复现）

```bash
# 环境自检
omnimem oauth-broker doctor

# 一条命令自动流水线（doctor + init + deploy 预览）
omnimem oauth-broker auto

# 执行部署
omnimem oauth-broker auto --apply
```

手动指定 provider 示例：

```bash
omnimem oauth-broker init --provider cloudflare --dir ./oauth-broker-cloudflare --client-id Iv1.your_client_id
omnimem oauth-broker deploy --provider cloudflare --dir ./oauth-broker-cloudflare --apply
```

## 启动引导联动



*[truncated — see source for full prompt]*