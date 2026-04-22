---
name: Claude Projects
description: How to build and load your Context Stack using Claude.
model: claude-sonnet-4-5
---
# Claude.ai Projects

How to build and load your Context Stack using Claude.ai Projects.

Claude Projects are the most natural fit for your Context Stack. You upload context files once, and Claude reads them automatically in every conversation within that project. No copy-paste per conversation. No re-explaining yourself.


## Step 0: Build Your Context Stack with a Project

Before you can load your Context Stack, you need to build it. The fastest way in Claude is to create a Project that runs the Context Discovery Session.

1. Go to [claude.ai](https://claude.ai) and click **Projects** in the left sidebar
2. Click **Create a project**
3. **Name:** "Context Discovery"
4. In **Project instructions**, paste the entire prompt block from `discovery/quick-start.md` (5 minutes, produces 3 files) or `discovery/context-discovery-session.md` (30-45 minutes, produces all 12 files)
5. Start a conversation inside the project
6. Answer the questions. Claude will draft your context-component files
7. Copy each drafted file and save it as a `.md` file on your computer

Once you have your context files, follow the sections below to load them into Claude for daily use.

For detailed Project configuration best practices, knowledge file strategies, and prompting tips, see `guides/discovery-agents.md`.


## Create Your Context Project

### Step 1: Open Projects

1. Go to [claude.ai](https://claude.ai)
2. Click **Projects** in the left sidebar
3. Click **Create a project**

### Step 2: Name and Describe the Project

- **Name:** "My Context Stack" (or "Personal Context", whatever is clear to you)
- **Description:** "My professional context for AI interactions. Loaded automatically in every conversation."

### Step 3: Upload Context Components

Click **Add project knowledge** and upload your context-component files:

```
professional-identity.md
communication-dna.md
values-and-boundaries.md
operating-rhythm.md
decision-architecture.md
collaboration-profile.md
brand-voice.md
domain-map.md
tool-ecosystem.md
strategic-context.md
feedback-journal.md
learning-edge.md
```

Upload them as individual files. Do not combine them into one document. Claude reads each file and understands the boundaries between components.

### Step 4: Add Project Instructions (Optional)

In the **Project instructions** field, you can add a short directive:

```
These files describe my professional context. Use them to calibrate your
responses to my role, communication style, domain expertise, and current
priorities. When I ask you to write something, match my voice as described
in communication-dna.md and brand-voice.md. When I ask for strategic advice,
ground it in my strategic-context.md and decision-architecture.md.
```

This is optional. Claude reads the uploaded files regardless. But explicit instructions can sharpen how Claude applies the context.


## Using Your Context Project

### Default Conversations

Every new conversation you start within this project automatically has access to all your context components. You do not need to reference them or ask Claude to read them.

Just start working:
- "Draft an email to my VP about the Q3 roadmap shift."
- "Review this architecture proposal and give me your honest read."
- "Help me think through whether we should build or buy this capability."

Claude will draw on your professional identity, communication style, strategic priorities, and domain expertise without being prompted to do so.

### Topic-Specific Projects

You do not need to load all 12 components into every project. For focused work, create additional projects with relevant subsets:

**"Writing and Content" project:**
- professional-identity.md
- communication-dna.md
- brand-voice.md
- strategic-context.md

**"Technical Architecture" project:**
- professional-identity.md
- tool-ecosystem.md
- domain-map.md
- decision-architecture.md

**"Research" project:**
- domain-map.md
- learning-edge.md
- strategic-context.md

### Referencing Context Across Projects

If you create multiple projects, your "My Context Stack" project serves as the master reference. When working in other projects, you can ask Claude to apply specific aspects of your context by describing them, since each project's knowledge is isolated to that project.

For a streamlined approach, upload just the components relevant to each project's purpose.


## Updating Your Context

### Routine Updates

1. Open your "My Context Stack" project
2. Click the project settings (gear icon)
3. Under **Project knowledge**, find the file to update
4. Delete the old version and upload the new one

There is no in-place editing for uploaded files. Replace the file entirely.

### Update Schedule

| Component | Update Frequency |
|:----------|:-----------------|
| strategic-context.md | Monthly |
| feedback-journal.md | After significant interactions |
| learning-edge.md | Quarterly |
| domain-map.md | Quarterly |
| tool-ecosystem.md | Quarterly |
| professional-identity.md | Annually or on role change |
| communication-dna.md | Rarely |
| All others | As needed |


## Token Considerations

Claude.ai Projects have a generous knowledge capacity, but context files still consume tokens from the conversation window.

- **Full stack (all 12 files):** Works well for general-purpose projects. Claude manages context retrieval internally.
- **Select loading (4 to 6 files):** Better for focused projects where you want maximum conversation length.

If you notice conversations hitting length limits sooner than expected, trim your context to the components most relevant to that project's purpose.


## Testing Your Setup

Start a new conversation in your Context Stack project and ask:

```
Based on the context you have about me, describe my professional role,
communication style, and current priorities.
```

Evaluate the response. If it misses something important, check the relevant component file for clarity and specificity.

Then test with a real task:

```
Draft a message to my team about why we are pausing Feature X to focus
on the platform migration.
```

The draft should match your voice, reference your actual strategic context, and reflect your communication preferences. If it sounds generic, your communication-dna or brand-voice files need more anti-patterns and signature moves.