# Benchmark Reality Gap

> SWE-bench and similar curated benchmarks overestimate agent capability by 50%+ in real-world deployment.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Benchmark Reality Gap

SWE-bench and similar curated benchmarks overestimate agent capability by 50%+ in real-world deployment. The gap emerges from benchmark framing: clean task descriptions with sufficient context don't resemble actual user queries, which are ambiguous, under-specified, and embedded in noisy ticket systems. Closing the gap requires domain-specific evaluation sets grounded in real user behavior.

> _Research informed by CAIN 2026 studies on SWE-bench vs. production agents; IDE telemetry analysis of query distribution from 200+ orgs; mutation techniques applied to convert synthetic benchmarks into realistic eval sets._

## The gap: why benchmarks lie

Curated benchmarks like SWE-bench are high-signal but low-fidelity:

- **Benchmark framing**: "Add a function to `module.py` that computes the factorial of an integer." Sufficient context, known-good acceptance criteria.
- **Real-world query**: "Factorial is broken" (from a 3-line Slack message in a 5-year-old codebase). Context is scattered across docs, issues, tests, and team history.

The 50%+ overestimate occurs because:

1. **Context abundance** — benchmark tasks come with `README.md`, working test suites, and clear accept/reject signals. Real tasks bury context in sprawling repos, outdated docs, and implicit domain knowledge.
2. **Single-threaded reasoning** — benchmarks ask "do X"; real queries require the agent to infer intent from partial signals ("we should use a cache here" → debug, understand why caching was discussed, then implement).
3. **Known search space** — benchmark tasks include the right files and functions. Real tasks hide the target in 10,000+ lines across 40+ files.
4. **Acceptance ambiguity** — benchmarks have crisp pass/fail. User tasks often have vague success criteria: "improve performance", "refactor this mess", "make it faster".
5. **Noise injection** — real repos have false-positive tests, dead code, deprecated patterns, conflicting documentation. Benchmarks sanitize th

*[truncated — see source for full prompt]*