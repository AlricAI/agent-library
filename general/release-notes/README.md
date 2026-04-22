# RELEASE NOTES

> ## What's New

### ✨ Features
- server proxy by websocket (#547)
- **[EXPERIMENTAL]** auto-renew on sandbox proxy/ingress access for [OSEP-0009](https

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# server 0.1.9

## What's New

### ✨ Features
- server proxy by websocket (#547)
- **[EXPERIMENTAL]** auto-renew on sandbox proxy/ingress access for [OSEP-0009](https://github.com/alibaba/OpenSandbox/blob/main/oseps/0009-auto-renew-sandbox-on-ingress-access.md) (#535)
- **[UNSTABLE]** add Pool CRUD API and Kubernetes CRD service (#357)

### 🐛 Bug Fixes
- **[IMPORTANT]** restore lifecycle route serialization to omit None fields in JSON responses instead of emitting explicit null (#555)
- ensure httpx streaming responses are closed in sandbox proxy (#547)
- print exception stack when create workload failure (#524)

## 👥 Contributors

Thanks to these contributors ❤️

- @wangdengshan
- @Pangjiping
- @ninan-nn

---
- PyPI: opensandbox-server==0.1.9
- Docker Hub: opensandbox/server:v0.1.9
- Aliyun Registry: sandbox-registry.cn-zhangjiakou.cr.aliyuncs.com/opensandbox/server:v0.1.9

# server 0.1.8 [DEPRECATED]

## What's New

### ✨ Features
- bump execd's image to v1.0.8 (#502)
- Add [egress].mode (dns | dns+nft, default dns); wire to sidecar as OPENSANDBOX_EGRESS_MODE on both Docker and Kubernetes (#501)
- add per-sandbox egress auth header generation and propagation through lifecycle endpoint responses (#492)
- support no-timeout (manual cleanup) in Kubernetes sandbox service (#466)
- support manual cleanup sandboxes (#446)
- implement OSSFS storage for **Docker service** in sandbox lifecycle (#340)

### 🐛 Bug Fixes
- Kubernetes egress: Run the sidecar privileged; use a startup command (sysctl for net.ipv6.conf.all.disable_ipv6, then /egress) instead of Pod securityContext.sysctls for IPv6; remove build_ipv6_disable_sysctls. (#501)
- reuse a single volume per claim_name and add multiple volumeMounts instead of one volume per Volume object. (#458)
- fix Docker server-proxy endpoint resolution for bridge sandboxes with egress sidecar by falling back to host-mapped endpoint resolution when internal IP resolution is not applicable (#492)
- increase default pids_limit to 40

*[truncated — see source for full prompt]*