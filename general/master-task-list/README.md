# MASTER TASK LIST

> Dieses Dokument dient als agentenübergreifendes Gedächtnis.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Master Task List: Siebenwind-Wiki-Rekonstruktion

Dieses Dokument dient als agentenübergreifendes Gedächtnis. Es trennt den **aktiven Fokus** von der **Projekthistorie** und definiert klare Standards für die Aufgabenpriorisierung.

## 📊 Status-Übersicht
- **Wiki-Standard:** v3.0 (Inter-AI Compliant)
- **RAG-Status (Orakel):** Aktiv & Sandbox-Resilienz (v1.1)
- **Last Handover**: 2026-04-17 (Codex → Next Agent)
- **Status**: Der technische Root-/Pages-Drift bleibt geschlossen (`legacy_root_status = removed`, `bridge_inventory.invalid = 0`). In dieser Session wurde `RESEARCH-2026-018` operativ ohne Oracle/RAG-Funktionalitaet abgearbeitet: alle exakten `[[index]]`-Platzhalter in `docs/Siebenwind_Wiki/` wurden durch kontextnahe Klartextbegriffe, kanonische Links oder `[UNGEKLÄRT]` ersetzt. `audit --json` zeigt weiterhin `0 contract_violations` und nur den bekannten `score_cluster`. `pages validate --json` bestaetigt `source-link-hygiene` als PASS, scheitert aber weiter am bekannten Audit-Precheck; `pages validate --contract --json` bleibt WARN wegen des breiteren bestehenden unresolved-Linkbacklogs (`635` unresolved, `633` unallowlisted, `621 needs_historian`), nicht wegen `[[index]]`.

---

## 🔴 Priorität 1: Aktueller Fokus (Next Step)

- [x] **Layout-Contract Cleanup & Audit-Zaehllogik**: Die `layout`-Altfelder aus den audit-relevanten Seiten wurden entfernt; `audit --json` meldet keine `legacy_field: layout`-Verletzungen mehr und weist den verbleibenden Ingestion-Score-Cluster konsistent unter `details.ingestion_issues` aus.

- [x] **Zeitstrahl Structural Repair**: `docs/Siebenwind_Wiki/05_Geschichte/Zeitstrahl.md` wurde von einem strukturell korrumpierten Mischdokument auf eine kompakte Chronik-Uebersicht mit Verweisen auf `Historie & Aeren` und `Zeitleiste (15-30 n.H.)` zurueckgefuehrt.

- [ ] **Semantic Pages Backlog Triage**: `advisor --json` zeigt trotz technischem Drift-Fix weiter `Pages WARN` mit `637` unresolved Targets (`625 needs_historian`, `5 generic_

*[truncated — see source for full prompt]*