# INDEX

> Master map for all active documentation under `docs/`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# kg-automation Documentation Index

Master map for all active documentation under `docs/`. Referenced from
`CLAUDE.md` as the starting point for agents discovering documentation.

**Scope**: `docs/**` excluding `docs/archive/`
(both exempt from restructuring).

---

## Constitution & Governance

### docs/constitution/ — Governance authority

- [Felix Constitution](<./constitution/FELIX-CONSTITUTION.md>) — top-level governance, autonomy levels, principles
- [Agent Registry (narrative)](<./constitution/AGENT-REGISTRY.md>) — current agent state, deployment status, autonomy transitions
- [Agent Registry (JSON)](<./constitution/agent-registry.json>) — machine-readable authoritative registry

### docs/runbooks/governance/ — Change control governance

- [Pre-Flight Change Checklist](<./runbooks/governance/pre-flight-checklist.md>) — mandatory assessment for Tier 0/1/2 changes
- [Post-Change Verification Protocol](<./runbooks/governance/post-change-verification.md>) — health-check verification after changes
- [Incident Postmortem Template](<./runbooks/governance/incident-postmortem-template.md>) — reusable template for incident analysis

---

## System Architecture

### docs/design/architecture/ — Current-state system reference

- [README](<./design/architecture/README.md>) — architecture suite index
- [Service Inventory](<./design/architecture/service-inventory.md>) — running services, ports, systemd units
- [Data Flows](<./design/architecture/data-flows.md>) + [Mermaid view](<./design/architecture/data-flows.view.md>)
- [Physical Topology](<./design/architecture/physical-topology.md>) + [Mermaid view](<./design/architecture/physical-topology.view.md>)
- [Credentials & Secrets](<./design/architecture/credentials-and-secrets.md>)
- [Identity Model](<./design/architecture/identity-model.md>)
- [Security Posture](<./design/architecture/security-posture.md>)
- [Backup & Recovery](<./design/architecture/backup-and-recovery.md>)
- [Change Control Protocol](<./design/architectur

*[truncated — see source for full prompt]*