# Praises

> A record of moments the user explicitly praised the work done.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Praises

A record of moments the user explicitly praised the work done.
These are worth remembering — they signal what "good" looks like in this project.

---

- 2025-03-15: "TOTALLY!" — closing exclamation wrapping up a long, productive session covering
  diff-entity implementation, website updates, SKILL.md docs, release 0.5.0, and a thorough
  self-improvement loop (lessons captured, promoted, cleared).

  *Why I think this was praised:* The session ended with everything genuinely done — code
  shipped, documented, released, deployed, and the meta-layer (AGENTS.md, lessons.md,
  praises.md) all tidy too. "Totally" feels like satisfaction at a complete loop, not just
  a single good moment.

- 2025-03-15: "I really liked you finally tried the code in REPL before writing the actual
  function into clj file. GOOD JOB!" — for proving `diff-entity` logic in the REPL step by
  step (including cleaning out residual hot-patch state before the final verification) before
  writing any `.clj` file.

  *Why I think this was praised:* It took a few corrections to get there, but once I truly
  internalised the rule, I didn't just run the happy path — I also removed the residual
  hot-patched vars from the namespace to simulate a clean load, and only then ran all three
  query paths. That extra rigour (not just "it works in my dirty REPL state") is what made
  the difference between going through the motions and genuinely proving the code.

- 2025-03-15: "AMAZING JOB. Standing ovation!" — for recognising that the `bb install` after
  SNAPSHOT bump lesson was concrete, release-process-specific, and actionable enough to skip
  lessons.md and go straight into the AGENTS.md release checklist as step 8.

  *Why I think this was praised:* lessons.md is for recent, still-accumulating observations.
  AGENTS.md is for stable, curated knowledge. The distinction matters — not every lesson
  needs to ferment in lessons.md first. A lesson that is immediately precise, non-contextual,
  and

*[truncated — see source for full prompt]*