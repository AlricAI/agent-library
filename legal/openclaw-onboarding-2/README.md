# OPENCLAW ONBOARDING

> Use this exact checklist.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Use this exact checklist.

1. Start Paperclip in auth mode.
```bash
cd <paperclip-repo-root>
pnpm dev --tailscale-auth
```
Then verify:
```bash
curl -sS http://127.0.0.1:3100/api/health | jq
```

2. Start a clean/stock OpenClaw Docker.
```bash
OPENCLAW_RESET_STATE=1 OPENCLAW_BUILD=1 ./scripts/smoke/openclaw-docker-ui.sh
```
Open the printed `Dashboard URL` (includes `#token=...`) in your browser.

3. In Paperclip UI, go to `http://127.0.0.1:3100/CLA/company/settings`.

4. Use the OpenClaw invite prompt flow.
- In the Invites section, click `Generate OpenClaw Invite Prompt`.
- Copy the generated prompt from `OpenClaw Invite Prompt`.
- Paste it into OpenClaw main chat as one message.
- If it stalls, send one follow-up: `How is onboarding going? Continue setup now.`

Security/control note:
- The OpenClaw invite prompt is created from a controlled endpoint:
  - `POST /api/companies/{companyId}/openclaw/invite-prompt`
  - board users with invite permission can call it
  - agent callers are limited to the company CEO agent

5. Approve the join request in Paperclip UI, then confirm the OpenClaw agent appears in CLA agents.

6. Gateway preflight (required before task tests).
- Confirm the created agent uses `openclaw_gateway` (not `openclaw`).
- Confirm gateway URL is `ws://...` or `wss://...`.
- Confirm gateway token is non-trivial (not empty / not 1-char placeholder).
- The OpenClaw Gateway adapter UI should not expose `disableDeviceAuth` for normal onboarding.
- Confirm pairing mode is explicit:
  - required default: device auth enabled (`adapterConfig.disableDeviceAuth` false/absent) with persisted `adapterConfig.devicePrivateKeyPem`
  - do not rely on `disableDeviceAuth` for normal onboarding
- If you can run API checks with board auth:
```bash
AGENT_ID="<newly-created-agent-id>"
curl -sS -H "Cookie: $PAPERCLIP_COOKIE" "http://127.0.0.1:3100/api/agents/$AGENT_ID" | jq '{adapterType,adapterConfig:{url:.adapterConfig.url,tokenLen:(.adapterConfig.headers["x-openclaw-token

*[truncated — see source for full prompt]*