# Connection Stability

> This document explains how to diagnose and improve AmneziaWG/WireGuard tunnel stability in "hard" networks (aggressive NAT, high jitter, UDP filtering).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## VPN connection stability and restrictive profile

This document explains how to diagnose and improve AmneziaWG/WireGuard tunnel stability in "hard" networks (aggressive NAT, high jitter, UDP filtering).

### 1. Baseline expectations

- Client configs issued by `admin-api` use:
  - `MTU=1200` (restrictive default).
  - `PersistentKeepalive=10` on the client side.
  - IPv4+IPv6 full tunnel by default: `AllowedIPs = 0.0.0.0/0, ::/0`.
  - DNS: `1.1.1.1, 1.0.0.1, 8.8.8.8, 8.8.4.4`.
- Server peers created on the node use:
  - client /32 or /128 as `AllowedIPs` on the node.
  - server keepalive ~15s by default.

### 2. Quick stability checklist

When a user reports "VPN is on but nothing works" or "works 2–3 minutes then freezes":

1. On the node container (`amnezia-awg`):
   - `docker exec amnezia-awg wg show awg0`
   - Confirm for the device:
     - `latest handshake` is recent (≤ 20–30 seconds) when the client is active.
     - `transfer: rx/tx` increases while the user is sending traffic.
2. On the host:
   - `sysctl net.ipv4.ip_forward` must be `1`.
   - NAT and routes:
     - `iptables -t nat -L POSTROUTING -n -v | grep 10.8.1` (or `nft list ruleset`).
     - `ip route | grep 10.8.1.0/24` and ensure it points to `awg0`.

Interpretation:

- Handshake missing or very old → NAT/power-saving/connectivity problem.
- Handshake OK but `rx/tx` almost not growing → routing/NAT/MTU/DNS problem.

### 3. Restrictive profile (IPv4-only, lower MTU, aggressive keepalive)

For unstable regions, use a restrictive connection profile:

- IPv4-only full tunnel:
  - Server profile: set `disable_ipv6_on_unstable_route=true`.
  - Resulting client config: `AllowedIPs = 0.0.0.0/0` (no `::/0`).
- Lower MTU:
  - Use the `mtu_probe` helper (`backend/scripts/mtu_probe.py`) to find a safe MTU and store it in the server profile.
- Keepalive:
  - Client keepalive fixed to 10 seconds; server peer keepalive ~15 seconds.

Devices created from such a profile are tagged with `connection_profile="rest

*[truncated — see source for full prompt]*