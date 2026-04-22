# ExecSummary

> You’re building a **contained builder**: a workspace-scoped agent that can read/write/execute to fulfill user intent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Vision and why this exists

You’re building a **contained builder**: a workspace-scoped agent that can read/write/execute to fulfill user intent. That’s the “power” part.

You also need a **verification gate** because agent output is not inherently trustworthy. Verification is the “safety + reliability” part. It prevents:

* shipping broken artifacts,
* silent regressions,
* “works on my machine” failures,
* and unreproducible changes.

The MVP proves a single thing: **you can turn intent → concrete changes → verified artifact**, repeatedly, with an audit trail.

This is general-purpose. “CI gate” is just one instance of verification; different projects will have different gates.

---

## Core principles (non-negotiable)

1. **Workspace containment**

* The agent is only allowed to affect the workspace it’s assigned.
* No cross-workspace writes. No hidden shared state.

2. **Hard isolation boundary**

* BUILD can write.
* VERIFY cannot write.
* VERIFY runs only on an immutable snapshot.

3. **Artifact-centric truth**

* The output isn’t “the agent said it worked.”
* The output is a **snapshot + patch + verification report** that anyone can replay.

4. **Verification is the oracle**

* The builder can run preflight checks, but only the verifier’s clean-room results determine PASS/FAIL.

5. **Driver abstraction**

* Claude Code is the first agent implementation, not the architecture.
* Swapping agents later must not change the control plane contract.

---

## What the MVP must demonstrate

You need a demo that is boringly convincing:

### Demonstration outcomes

1. Submit a work order: “Implement X in repo Y.”
2. Agent edits the workspace and runs local preflight.
3. System snapshots the result (immutable identity).
4. Clean-room verifier runs the gate.
5. If fail, builder loops using structured failure feedback.
6. Eventually PASS produces a shippable artifact with audit logs.

### Deliverables for a single run (always produced)

* Immutable snapshot identifier (c

*[truncated — see source for full prompt]*