# AGENT OPERATIONS HANDBOOK

> Zweck: Zentrale Uebersicht fuer den operativen Betrieb von Agenten, Skills und Workflows im Repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AGENT_OPERATIONS_HANDBOOK

Zweck: Zentrale Uebersicht fuer den operativen Betrieb von Agenten, Skills und Workflows im Repository.

## Betriebsinvarianten

1. Runtime Authority: Ausfuehrung nur ueber `./7w_wiki.py`.
2. Orchestrierung bleibt in `.agent/` autoritativ.
3. Discoverability fuer externe Hosts folgt dem Layer-Modell: `.agent/` plus `./7w_wiki.py` sind kanonisch; MCP ist die Live-Schnittstelle; `.agents/skills/` plus `.codex/config.toml` bilden den Codex-Adapter.
4. Governance-Dokumente bleiben in `System/` und `System/Synapse_Board/`.
5. Neue Systemdokumente muessen in `System/COORDINATION_HUB.md` registriert werden.
6. Epistemische Praezedenz ist `Homepage > Quellen > Wiki Pages`; die volle Drift-/Pages-Regel steht in [SY_DRIFT_PAGES_CONTRACT.md](Synapse_Board/SY_DRIFT_PAGES_CONTRACT.md).
7. `lore_manifest.json` ist eine generierte Kompatibilitaetsoberflaeche, nicht die Quelle der Wahrheit.

<!-- BEGIN GENERATED DRIFT CONTRACT REFERENCE -->
> Generated reference block. The surrounding narrative text remains manually maintained.
> Canonical contract: [SY_DRIFT_PAGES_CONTRACT.md](Synapse_Board/SY_DRIFT_PAGES_CONTRACT.md)
>
> - Epistemic precedence: `Homepage > Quellen > Wiki Pages`.
> - `docs/Siebenwind_Wiki/` is the technical edit/publish tree, not the highest truth source.
> - Technical drift is validated via `./7w_wiki.py sanitize`, `./7w_wiki.py audit`, and `./7w_wiki.py pages validate --json [--strict-links]`.
> - Deterministic contract/CI checks use `./7w_wiki.py pages validate --contract --json`.
> - `--strict` hardens the MkDocs build; `--strict-links` is the hard unresolved-link gate.
> - Generated command registries are synced by `./7w_wiki.py tech --sync-docs` / `--sync-interop`; narrative rules live in the canonical contract.
<!-- END GENERATED DRIFT CONTRACT REFERENCE -->

## Strukturkarte

| Pfad | Rolle | Autoritaet |
|---|---|---|
| `7w_wiki.py` | Einziger Runtime-Einstieg | Ja |
| `.agent/workflows/` | Methodische SOPs und Department-Loop

*[truncated — see source for full prompt]*