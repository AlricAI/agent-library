---
name: Best Practices
description: How to build, maintain, and get the most from your Context Stack.
model: claude-sonnet-4-5
---
# Best Practices

How to build, maintain, and get the most from your Context Stack.


## Start Small

Do not try to build all 12 components at once. Start with three:

1. **professional-identity.md**: Who you are and what you do
2. **communication-dna.md**: How you write and what you reject
3. **strategic-context.md**: What you are working on right now

These three cover Self, Style, and Situation. Load them into one AI platform and use them for a week. Notice where AI output improves and where it still misses. Then add components to close the gaps.

Most people find that professional-identity plus communication-dna alone produces a noticeable improvement. Everything else is refinement.


## Be Specific, Not Comprehensive

A 200-word professional identity that captures your perspective is more useful than a 2,000-word resume. AI does not need your complete career history. It needs the details that change how it should respond to you.

**Weak (generic, could be anyone):**

```
I am a senior leader with 15 years of experience in technology.
I manage teams and drive strategic initiatives.
```

**Strong (specific, changes AI behavior):**

```
I run product operations at a healthcare technology company, sitting
between six product squads and the executive team. Most of my work
involves translating vague strategic directives into concrete execution
plans. I have strong opinions about prioritization frameworks and low
tolerance for status reports that do not surface real blockers.
```

The strong version tells the AI your role, your organizational position, what you actually do, and what you care about. The AI will now frame advice differently, skip introductory explanations about product ops, and avoid generic strategic platitudes.

Apply this principle to every component. Density beats breadth.


## Anti-Patterns Are Gold

Most people describe what they want from AI. The highest-leverage input is what you do not want. Your anti-patterns, the things that make you immediately reject AI output, are the most powerful calibration data.

In your communication-dna, include explicit rejections:

```
## Anti-Patterns (Never Do These)

- Never start a response with "Great question!" or "Absolutely!"
- No bullet points when a full sentence would be clearer
- Never use the phrase "in order to" (just say "to")
- Do not hedge with "it might be worth considering" when you mean "do this"
- No em dashes
- Never use "leverage" as a verb
- Do not summarize what I just said back to me before answering
```

These negative constraints are more effective than positive style descriptions because they eliminate the most common failure modes. Most AI systems default to the same handful of filler patterns. Explicitly blocking those patterns forces the output toward your actual voice.


## Update Strategically

Context components have different half-lives. Updating everything at once is wasteful. Match your update cadence to how fast each component actually changes.

### Update monthly

**strategic-context.md**: Your priorities, active projects, and constraints shift regularly. A stale strategic context means AI advice is grounded in last quarter's reality. This is the most time-sensitive component.

### Update quarterly

**learning-edge.md**: Your learning focus shifts as you build new skills and encounter new challenges. Update as needed, at least quarterly.

**tool-ecosystem.md**: Your tech stack evolves as you adopt new tools and drop old ones. Update when your daily toolkit changes.

**domain-map.md**: Your expertise grows. Areas that were "learning" may now be "proficient." New domains may have appeared.

**collaboration-profile.md**: How you work with people can shift with team dynamics. Review quarterly to ensure it reflects your current working relationships.

### Update as needed

**feedback-journal.md**: Add entries after significant AI interactions where you corrected the output or discovered a preference. Do not batch these; capture them while the memory is fresh. This is how your Context Stack learns.

### Update yearly or on role change

**professional-identity.md**: Your role, organization, and professional arc change slowly. Update when you change jobs, get promoted, or shift your career direction significantly.

**values-and-boundaries.md**: Your deepest principles rarely shift. Review annually to confirm they still hold.

### Rarely changes

**communication-dna.md**: Your voice is your voice. Add new anti-patterns when you discover them, but the core patterns stay stable.

**decision-architecture.md**: Your decision-making frameworks evolve slowly over years.

**brand-voice.md**: External voice shifts gradually with brand evolution.

**operating-rhythm.md**: Work patterns change with role transitions, not on a regular cadence.


## Test Your Context

After building or updating your context components, test them. Start a fresh AI conversation with your context loaded and ask:

```
Based on the context you have about me, describe:
1. My professional role and what I actually do day to day
2. How I prefer to communicate
3. What I am working on right now
4. What topics I am expert in vs. still learning
```

Evaluate the response. If any section is thin, vague, or wrong, the corresponding component needs work.

Then test with a real task. Ask the AI to draft something you would normally write: an email, a project update, a decision memo. Evaluate whether it sounds like you or like a generic AI. The gap between the two tells you where your context needs more specificity.


## Keep It Dense

Every sentence in a context component should carry information that changes AI behavior. If a sentence could apply to anyone in your role, it is not specific enough. If removing a sentence would not change AI output, remove it.

**Too sparse:**

```
I am experienced in project management and leadership.
```

**Dense enough:**

```
I run quarterly planning for a 200-person product org. I use OKRs with
a strict "3 objectives, 4 key results each" constraint. I push back
on teams that write key results as tasks instead of outcomes.
```

The dense version gives the AI concrete information: your scope, your framework, your constraints, and a specific opinion. It will now generate OKR-related content that matches your approach.


## Own Your Voice

If AI output sounds generic even with your context loaded, the problem is almost always in communication-dna or brand-voice. These components need the most attention to detail.

Common fixes:

- **Add more anti-patterns.** Most people underestimate how many AI defaults they actually dislike.
- **Include writing samples.** Paste 2 to 3 short examples of sentences you have actually written and are proud of. These act as style targets.
- **Specify sentence structure.** "Short sentences. Rarely more than 15 words." is more effective than "I prefer concise writing."
- **Name the register.** "Professional but not formal. Like a respected colleague, not a consultant." gives the AI a social calibration point.
- **Call out specific words.** "Use 'ship' not 'deliver.' Use 'build' not 'develop.' Use 'fix' not 'remediate.'" This level of word-choice specificity is what separates a generic voice from yours.


## The Feedback Loop

Your Context Stack improves through use. The mechanism is simple:

1. Use AI with your context loaded
2. Notice when the output is wrong, off-tone, or missing the point
3. Identify why: missing context, wrong assumption, style mismatch
4. Add an entry to feedback-journal.md capturing the correction
5. If the pattern is fundamental, update the relevant component

This loop is the single most important practice for long-term context quality. A Context Stack that never gets corrected never gets better.

**Example feedback-journal entry:**

```
## 2024-11-15: Status Update Tone

When I asked for a project status update, the AI wrote it as a formal
report with "Executive Summary" and "Key Findings" headers. My actual
status updates are 3 to 5 bullet points in Slack, casual tone, ending
with what I need from the reader. Updated communication-dna.md with
format preferences for status updates.
```

Notice the structure: what happened, what was wrong, what you did about it. Over time, these entries build a detailed record of your preferences that no single component could capture upfront.


## Common Mistakes

### Writing a resume instead of a context file

Your professional-identity is not your LinkedIn profile. It should capture how you think and what shapes your perspective, not a list of accomplishments.

### Being too polite about anti-patterns

"I slightly prefer shorter sentences" does not work. "Never write a sentence longer than 20 words unless it contains a list" does work. Be blunt in your anti-patterns.

### Loading everything everywhere

Full-stack loading works on platforms with generous context windows. On platforms with tight limits, select loading produces better results than cramming everything in and exceeding the token budget.

### Forgetting to update strategic-context

This is the most common decay pattern. Your context files say you are working on Project X, but you finished that two months ago. Now the AI is giving you advice framed around a project that no longer exists.

### Treating it as a one-time setup

A Context Stack is a living system. The initial build gets you 70% of the value. The ongoing feedback loop and strategic updates get you the remaining 30%, and that 30% is what makes it feel like the AI actually knows you.