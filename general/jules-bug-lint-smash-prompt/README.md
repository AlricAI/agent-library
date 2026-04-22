# Jules Bug Lint Smash Prompt

> ## Context

You are fixing TypeScript compilation errors (`tsc --noEmit`) in the `backend/` workspace of this monorepo. All errors are grouped by cate

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Jules Bug & Lint Smash Prompt

## Context

You are fixing TypeScript compilation errors (`tsc --noEmit`) in the `backend/` workspace of this monorepo. All errors are grouped by category below. Work through each group in order. Do not change git branches. Do not modify `frontend/`. Do not run `wrangler deploy`.

After fixing each group, run `pnpm tsc --noEmit --project backend/tsconfig.json` and verify the error count drops before moving to the next group.

---

## Group 1 — Missing / Deleted Source Files (TS2307 "Cannot find module")

These imports reference files that no longer exist. For each, either create a minimal stub that satisfies the import signature, or remove the dead import and its usages.

**Files to address:**

| File                                                                  | Missing module                                                                |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `backend/src/automations/issues/SlashCommand.ts`                      | `@/automations/push/gardener/router`                                          |
| `backend/src/automations/push/auditor.ts`                             | `./types`                                                                     |
| `backend/src/automations/push/commands/extract.ts`                    | `./types`                                                                     |
| `backend/src/automations/push/commands/registry.ts`                   | `./types`, `./fix-types`, `./fix-all`, `./resolve-conflicts`, `./implement`   |
| `backend/src/automations/push/commands/standardize.ts`                | `./types`                                                                     |
| `backend/src/automations/push/commands/test.ts`                       | `./types`, `../agents/implementer`                                            |
| `backend/src/automations/push

*[truncated — see source for full prompt]*