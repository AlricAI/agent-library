# Storage Schema

> > Last updated: v3.3.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cue — Storage Schema Documentation

> Last updated: v3.3.0

---

## Storage Keys

| Key | Type | Written By | Read By |
|-----|------|------------|---------|
| `smartactions:buttons` | `ButtonDef[]` | Global Admin UI | All render modules, project settings |
| `smartactions:categories` | `Category[]` | Global Admin UI | All render modules, project settings |
| `smartactions:project:{id}` | `ProjectConfig` | Project Settings UI | All render modules |
| `smartactions:global` | `GlobalConfig` | Global Admin UI | All render modules, admin UI |
| `smartactions:lastClicked:{buttonId}:{issueKey}` | `string` (ISO timestamp) | Dispatcher (fire-and-forget) | All issue render modules |
| `smartactions:version` | `string` | App bootstrap | Migration checks |

> **Last-clicked key is scoped per issue.** Each button tracks its own timestamp separately per Jira issue key. Clicking a button on PROJ-1 does not affect the timestamp shown on PROJ-2.
>
> Project page (`jira:projectPage`) has no issue context — it uses an empty string for `issueKey`, giving it its own separate tracking slot.

---

## Constants

```typescript
export const CATEGORIES_KEY = 'smartactions:categories';
export const GLOBAL_KEY = 'smartactions:global';
export const LAST_CLICKED_PREFIX = 'smartactions:lastClicked:';

// All SET_ISSUE_PROPERTY keys are stored and written with this prefix.
// User types just the suffix; app stores "cue.smartaction.{suffix}".
// JQL: issue.property[cue.smartaction.status].value = "escalated"
// TODO (Phase 2 - nice to have): add jira:entityPropertyIndex in manifest.yml
// for indexed fast JQL search.
export const PROPERTY_KEY_PREFIX = 'cue.smartaction.';
```

---

## TypeScript Interfaces

### ActionType
```typescript
type ActionType =
  | 'OPEN_URL'
  | 'OPEN_MODAL'
  | 'JIRA_TRANSITION'
  | 'JIRA_COMMENT'
  | 'JIRA_ASSIGN'
  | 'COPY_TEXT'
  | 'SET_ISSUE_PROPERTY'
  | 'FORGE_FUNCTION'
  | 'CREATE_CHILD_ISSUE';
```

### PlacementType
```typescript
type PlacementType = 'panel' | '

*[truncated — see source for full prompt]*