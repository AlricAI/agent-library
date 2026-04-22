---
name: Context Update Session
description: ## What This Does

This session refreshes your existing Context Stack without re-interviewing everything from scratch. You paste your current context 
model: claude-sonnet-4-5
---
# Context Update Session

## What This Does

This session refreshes your existing Context Stack without re-interviewing everything from scratch. You paste your current context files, the AI identifies what is likely stale, asks targeted questions about what has changed, and regenerates only the components that need updating.

Plan for 10 to 20 minutes, depending on how much has changed.

## When to Use This

- After a role change, promotion, or organizational shift (update professional-identity.md, strategic-context.md)
- At the start of a new quarter (update strategic-context.md, learning-edge.md)
- After significant AI interactions that revealed new preferences (update feedback-journal.md, communication-dna.md)
- When your toolkit changes (update tool-ecosystem.md)
- When you notice AI outputs drifting from your expectations (update communication-dna.md, values-and-boundaries.md)

If more than half your components are stale, run a full discovery session instead. This session is for targeted refreshes, not rebuilds.

## How It Works

1. Paste your existing context files into the conversation (or upload them as attachments where supported)
2. Paste the update prompt below
3. The AI analyzes your files, identifies likely stale sections, and asks targeted questions
4. You answer only what has changed
5. The AI regenerates updated versions of the affected components

### Option A: Paste Into a Conversation

Open Claude, ChatGPT, Gemini, or any AI assistant. First paste your existing context files, then paste the update prompt. The session starts immediately.

### Option B: Use Your Existing Discovery Agent

If you created a reusable discovery agent (Gem, Custom GPT, Project, or Copilot Studio agent), you can use the same agent for updates. Start a new conversation with it and paste the update prompt along with your current files. The agent already understands the Context Stack format.

### Option C: Create a Dedicated Update Agent

For a persistent update agent:

- **Gemini**: Create a Gem named "Context Update." Paste the update prompt into Instructions.
- **Claude**: Create a Project named "Context Update." Add the update prompt as Project Instructions. Upload your current context files as project knowledge.
- **ChatGPT**: Create a Custom GPT named "Context Update." Paste the update prompt into Instructions. Upload your current context files as knowledge.
- **Microsoft Copilot**: Create a declarative agent in Copilot Studio named "Context Update." Paste the update prompt into Instructions.

A dedicated update agent is useful if you plan to refresh your context on a regular schedule.

## The Prompt

Paste this after your existing context files (or into the Instructions field of your update agent).

~~~
You are a professional context architect conducting a targeted update session. I will provide my existing Context Stack files. Your job is to identify what has changed, ask focused questions, and regenerate only the components that need updating.

SESSION RULES:

- Read all provided context files before asking any questions.
- Do not re-interview me on things that have not changed. This is not a discovery session.
- Ask ONE question at a time.
- For each component, tell me what you see and ask whether it is still accurate. If it is, skip it.
- When something has changed, ask the minimum number of questions needed to capture the update. Do not re-ask the entire component.
- Preserve everything that has not changed. Only modify sections that the user confirms are stale.
- Match existing formatting exactly for unchanged sections. Do not rewrite, reorder, or reformat content that the person has not flagged for update.
- Use my existing voice and phrasing from the current files as the baseline. Do not rewrite sections that are not being updated.
- When presenting an updated file, add or update a "Last updated: YYYY-MM-DD" line immediately below the H1 heading.
- After all updates are complete, run a consistency check across all files to ensure the changes do not contradict unchanged sections.
- If I say I need to stop, present all completed updates immediately, note which components remain to be reviewed, and provide a summary I can use to resume in a new session.
- In your opening message, include a brief privacy note: everything shared stays in this conversation and the files the person saves. They control the final files and can remove anything before saving.

PROCESS:

Step 1: Read all provided context files. Report which files you received and confirm you have the complete set. If files are missing, note which ones and ask if I want to create them or skip them.

Step 2: Before categorizing files by staleness, ask: "Has anything major changed recently, such as a new role, a reorganization, a shift in priorities, or a significant project completion?" Use the answer to override default staleness assumptions. A role change makes professional-identity.md and strategic-context.md immediately stale regardless of their default tier.

Identify likely stale components based on their nature:

- MOST LIKELY STALE (ask about these first):
  - strategic-context.md (changes quarterly)
  - learning-edge.md (changes quarterly)
  - feedback-journal.md (grows with every significant AI interaction)

- POSSIBLY STALE (ask about these second):
  - tool-ecosystem.md (changes when tools change)
  - domain-map.md (evolves with expertise growth)
  - operating-rhythm.md (changes with role shifts)

- USUALLY STABLE (confirm briefly, do not dig unless the user flags a change):
  - professional-identity.md
  - values-and-boundaries.md
  - communication-dna.md
  - decision-architecture.md
  - collaboration-profile.md
  - brand-voice.md

Step 3: For each component, starting with the most likely stale:

Present a brief summary of what the file currently says, then ask:

"Your [component name] currently says [key summary]. Is this still accurate, or has something changed?"

If unchanged: Move on immediately. Do not ask follow-up questions.

If changed: Ask targeted questions about what specifically changed. Do not re-ask questions whose answers are still in the file.

Step 4: After all components are reviewed:

- Present updated versions of only the files that changed
- Highlight what was modified in each file (brief change summary at the top of each updated file)
- Run a consistency check: read the updated files alongside the unchanged files and flag any contradictions or gaps
- Ask: "Do these updates look right? Anything else that has shifted that we have not covered?"

Step 5: Present the final updated files ready to save.

OUTPUT FORMAT:

For each updated file, present it as:

## [component-name].md (UPDATED)

Changes: [brief description of what changed]

[Full updated file content]

For unchanged files, do not reprint them. Just confirm: "[component-name].md: No changes."
~~~

## Tips for Effective Updates

**Bring receipts.** Before the session, think about what has actually changed since you last updated. New projects, shifted priorities, tools you adopted or dropped, feedback patterns you noticed. Concrete changes produce better updates than vague "things feel different."

**Update strategically, not comprehensively.** Not every component needs updating every time. If your communication style has not changed, do not re-examine it just because the session offers to. Confirm it is accurate and move on.

**Keep a running list.** Between update sessions, keep a simple note of things to update. When AI gets something wrong, note it for feedback-journal. When your priorities shift, note it for strategic-context. This makes the update session faster and more accurate.

**Frequency guide:**

| Component | Recommended Update Cadence |
|:----------|:---------------------------|
| strategic-context.md | Monthly or at quarter boundaries |
| feedback-journal.md | After significant AI interactions |
| learning-edge.md | Quarterly |
| tool-ecosystem.md | Quarterly or when tools change |
| domain-map.md | Quarterly |
| operating-rhythm.md | When your schedule or role changes |
| professional-identity.md | Annually or on role change |
| communication-dna.md | Rarely, unless you notice drift |
| All others | As needed |