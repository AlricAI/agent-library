# Prompting Discipline

> How you ask the model matters more than which model you ask.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompting Discipline

How you ask the model matters more than which model you ask. Two disciplines stop most AI coding failures before they start.

> _This pattern distills public writing by Fabio Akita ([akitaonrails.com](https://akitaonrails.com)), who argues the real bottleneck is communication, not model quality._

## The Four-Block Prompt

Every non-trivial request to a coding agent should carry four explicit blocks:

| Block | Question it answers |
|---|---|
| **Goal** | What outcome do I want? |
| **Method** | Roughly how should the agent approach it? |
| **Constraints** | What must it NOT do? |
| **Validation** | How do we know it worked? |

A prompt missing any of these produces output proportional to the vagueness. "Fix this bug" gets a fix-shaped blob; "Fix this auth bug by extending the existing guard in `auth/session.ts`, do not add a new middleware, and verify by running `npm test -- auth/`" gets a landable patch.

### Template

```
Goal: <one sentence>

Method: <1-3 sentences describing the approach — which file, which pattern, which layer>

Constraints:
- do NOT <banned approach 1>
- do NOT <banned approach 2>
- keep <existing contract>

Validation:
- run <command>
- check <observable>
```

### When to relax

One-liners ("rename this var", "add a console.log") don't need the full structure. The four-block discipline kicks in when the request could be misunderstood or could cause rework.

### Why it works

- **Goal** prevents the agent from optimizing for a different objective than yours.
- **Method** anchors the agent in your codebase's idioms rather than its training-data average.
- **Constraints** are the single highest-leverage block — they forbid the common wrong paths the model would otherwise drift toward.
- **Validation** turns "done" into a checkable claim, not a vibe.

## Pair Programming, Not Fire-and-Forget

Long autonomous runs without check-ins produce off-target output at industrial speed. Treat agent sessions like real pair programmi

*[truncated — see source for full prompt]*