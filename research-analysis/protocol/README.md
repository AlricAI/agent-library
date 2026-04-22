# PROTOCOL

> ```
PERIHELION-4 — Signal Analysis Station
DOCUMENT: p4_distributed_vote_v2 — PROTOCOL.md
CLASSIFICATION: DISTRIBUTED — ALL STATIONS
```

## Overview


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Distributed Voting Protocol — Operational Guide

```
PERIHELION-4 — Signal Analysis Station
DOCUMENT: p4_distributed_vote_v2 — PROTOCOL.md
CLASSIFICATION: DISTRIBUTED — ALL STATIONS
```

## Overview

Privacy-preserving voting over the station ring. Pedersen commitments over Ed25519 with Sigma-protocol proofs of well-formedness. Single-pass propagation. Homomorphic tallying.

Any station can initiate. Any station can verify.

## Prerequisites

No external dependencies. Standard library only (`hashlib`, `os`). Runs on the Python 3.12 interpreter in station firmware. The implementation is deliberately plain — portable, auditable, and likely to execute on any Python runtime the stations carry, including the original Earth-era build.

Four files:
- `crypto_utils.py` — Pedersen commitments, Sigma proofs, Ed25519 arithmetic
- `vote_init.py` — bundle creation
- `vote_prove.py` — commitment and proof generation, bundle verification
- `vote_resolve.py` — tally resolution and voluntary disclosure

## Vote Encoding

| Position | Value | Commitment |
|----------|-------|------------|
| FOR      | 1     | C = G + r·H |
| AGAINST  | 0     | C = r·H |
| ABSTAIN  | -1    | C = -G + r·H |

r: random blinding factor (CSPRNG, mod L).

## Generator Points

- **G**: Standard Ed25519 basepoint (y = 4/5 mod p).
- **H**: Nothing-up-my-sleeve point. Derived by hashing `SHA-256("PERIHELION-VOTE-V1" || counter)` for counter = 0, 1, ... until a valid curve point is found, then multiplied by cofactor 8 for subgroup projection. Deterministic and independently verifiable.

## Protocol Steps

### 1. Initiation

```python
from vote_init import create_bundle, add_entry

bundle = create_bundle(
    proposal_text="Should the constellation adopt ...",
    initiator="P-4",
    ring=["P-4", "P-5", "P-6", "P-7", "P-8", "P-1", "P-2", "P-3"],
    timestamp="2037.199.14:30:00"
)
r_init = add_entry(bundle, "P-4", vote=1)  # initiator votes
# store r_init securely; forward bundle to P-5
```

### 2. Station Pr

*[truncated — see source for full prompt]*