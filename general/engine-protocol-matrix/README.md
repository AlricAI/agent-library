# ENGINE PROTOCOL MATRIX

> Status legend: `implemented`, `partial`, `drift`

Last updated: 2026-02-13 (engine-backed workspace-first session scope + explicit attach + sandbox ov

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Engine Protocol Matrix

Status legend: `implemented`, `partial`, `drift`

Last updated: 2026-02-13 (engine-backed workspace-first session scope + explicit attach + sandbox override)

## 1) Frontend <-> Tauri Commands

| Boundary                                                                             | Canonical contract                                                                       | Status      | Notes                                                                                      |
| ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------ |
| Storage migration wizard -> `get_storage_migration_status` / `run_storage_migration` | Startup + settings-triggered migration control                                           | implemented | Auto-run at startup after vault unlock; manual rerun from Settings.                        |
| Plans panel -> `list_plans`                                                          | Returns plan metadata from `.tandem/plans` (plus legacy `.opencode/plans` read fallback) | implemented | Command registered in `src-tauri/src/lib.rs` invoke handler.                               |
| Plan content -> `read_plan_content`                                                  | Returns full plan markdown by path                                                       | implemented | Command registered and wired to `commands.rs`.                                             |
| Mode permissions -> `build_permission_rules`                                         | Rule names align with runtime tool names                                                 | partial     | Alias support present for `todowrite` + `todo_write`; broader alias policy still evolving. |
| Sessions sidebar scope                                  

*[truncated — see source for full prompt]*