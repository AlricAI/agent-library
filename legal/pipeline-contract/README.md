# Pipeline Contract

> \# Chimera Pipeline Contract (Artifacts, run\_id, and CI Gate)



\## Artifact Chain (authoritative)

A change is valid only if these files exist unde

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
\# Chimera Pipeline Contract (Artifacts, run\_id, and CI Gate)



\## Artifact Chain (authoritative)

A change is valid only if these files exist under `artifacts/<ts>/<run\_id>/` and reference the SAME `run\_id` (format: `YYYYMMDDTHHMMSSZ-<short>`):



1\) `prompt.audit.json`

2\) `code.plan.json`

3\) `codex.instructions.json`

4\) `changeset.diff` (unified diff)

5\) `gate.decision.json` (with `"decision":"approve"`)



\### Required fields (minimum)

\- Every JSON artifact MUST contain: `"run\_id": "<id>"`.

\- `code.plan.json.ops\[].selector` MUST be one of:

&nbsp; - `{ "anchor": "ANCHOR:NAME" }`  

&nbsp; - `{ "symbol": "module.Class.func" }`  

&nbsp; - `{ "line\_range": {"file":"path","start":N,"end":M} }`

\- Each op MUST include at least `"expect\_sha\_file"` and SHOULD include `"expect\_sha\_region"`.



\### Example snippets

\*\*prompt.audit.json\*\*

```json

{ "run\_id":"20250929T001500Z-abc123", "goal":"Add mm:ss HUD timer", "definition\_of\_done":\["HUD visible","pause/resume","3 tests"] }



code.plan.json

{ "run\_id":"20250929T001500Z-abc123", "ops":\[ { "selector":{"anchor":"ANCHOR:TIMER\_INJECT"}, "expect\_sha\_file":"5f2b…", "patch":"@@ ..." } ] }



codex.instructions.json

{ "run\_id":"20250929T001500Z-abc123", "ops":\[ { "apply\_patch": { "file":"ui/hud.py", "selector":{"anchor":"ANCHOR:TIMER\_INJECT"}, "patch":"@@ ..." } } ], "preconditions":\[{"file":"ui/hud.py","expect\_sha":"5f2b…"}], "glossary\_assertions":\["Timer","Tick"] }



gate.decision.json

{ "run\_id":"20250929T001500Z-abc123", "decision":"approve", "reasons":\[], "summary":{"tests\_failed":0,"lint\_errors":0} }



CI Gate (single required check)

The Chimera Gate job SHALL fail the PR unless ALL are true:

All five artifacts exist for the PR head commit’s run\_id.





All artifacts share the same run\_id and that run\_id appears in the PR title.





gate.decision.json.decision == "approve".





If test.report.json exists, summary.failed == 0.





The changeset.diff only 

*[truncated — see source for full prompt]*