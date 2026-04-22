---
name: Chatgpt
description: How to build and load your Context Stack using ChatGPT.
model: claude-sonnet-4-5
---
# ChatGPT

How to build and load your Context Stack using ChatGPT.

ChatGPT offers several ways to load persistent context, each with different tradeoffs. The most effective approach combines Custom Instructions for your core identity with Projects for deeper context.


## Step 0: Build Your Context Stack with a Custom GPT

Before you can load your Context Stack, you need to build it. You can create a Custom GPT that runs the Context Discovery Session.

1. Go to **Explore GPTs** > **Create**
2. In the **Configure** tab, paste the entire prompt block from `discovery/quick-start.md` (5 minutes, produces 3 files) or `discovery/context-discovery-session.md` (30-45 minutes, produces all 12 files) into the **Instructions** field
3. **Name:** "Context Discovery"
4. Save the GPT
5. Start a conversation with your Context Discovery GPT
6. Answer the questions. The GPT will draft your context-component files
7. Copy each drafted file and save it as a `.md` file on your computer

Alternatively, skip the GPT and paste the prompt block directly into a new ChatGPT conversation.

Once you have your context files, follow the sections below to load them into ChatGPT for daily use.

For detailed GPT configuration best practices, knowledge file strategies, and prompting tips, see `guides/discovery-agents.md`.


## Option 1: Custom Instructions

The fastest way to get started. Custom Instructions apply to every conversation across ChatGPT.

### Setup

1. Click your profile icon (bottom left)
2. Select **Settings**
3. Go to **Personalization > Custom Instructions**
4. You will see two fields:
   - **"What would you like ChatGPT to know about you?"**
   - **"How would you like ChatGPT to respond?"**

### What to Put Where

**Field 1: "What would you like ChatGPT to know about you?"**

Paste a condensed version of your professional-identity and strategic-context. You have approximately 1,500 words per field (roughly 8,000 characters), so be dense.

Example:

```
Director of Product Operations at a healthcare technology company. I sit
between product teams and executive leadership, translating strategy into
execution. I manage cross-functional alignment across six product squads and
run quarterly planning end to end. Current priorities: platform migration
(Q3 deadline), vendor consolidation, and building a self-service analytics
capability. 12 years in product and operations, previously at two enterprise
SaaS companies. Deep expertise in product ops, agile at scale, and
healthcare IT compliance.
```

**Field 2: "How would you like ChatGPT to respond?"**

Paste the core patterns from your communication-dna. Focus on anti-patterns (what you reject) since those have the highest impact.

Example:

```
Direct and concise. Lead with the recommendation, then reasoning. No filler
phrases ("Great question!", "Certainly!"). No bullet points when a sentence
works. Active voice. Plain language over jargon. When I ask for a draft,
match a professional but approachable tone. Never use em dashes. Short
paragraphs, one idea each. If you are unsure about something, say so
directly instead of hedging with qualifiers.
```

### Limitations

- Approximately 1,500 characters per field. This forces you to distill your context to essentials.
- Applies globally. You cannot vary it by conversation.
- No file uploads. Everything must be pasted as text.


## Option 2: ChatGPT Projects

If your ChatGPT plan includes Projects, this is the better approach for detailed context.

### Setup

1. Click **Projects** in the left sidebar
2. Create a new project (e.g., "My Context")
3. Add files to the project's knowledge base

### What to Upload

Upload your context-component files directly:

```
professional-identity.md
communication-dna.md
strategic-context.md
domain-map.md
```

Add more components based on the project's purpose. For a general-purpose context project, include all components you have built.

### Project Instructions

In the project's instruction field, add:

```
These files describe my professional context. Use them to inform your
responses. Match my communication style from communication-dna.md. Ground
strategic advice in my strategic-context.md. Assume the expertise levels
described in domain-map.md.
```

### Using Projects

Every conversation within the project has access to the uploaded files. Start working without re-establishing context.

For topic-specific projects, upload only the relevant subset of components.


## Option 3: ChatGPT Memory

ChatGPT has a built-in Memory feature that learns from your conversations over time.

### How It Works

- ChatGPT automatically stores facts and preferences it learns during conversations
- You can view and manage stored memories in **Settings > Personalization > Memory**
- You can explicitly tell ChatGPT to remember something: "Remember that I prefer concise bullet points for status updates."

### Strengths

- Zero setup. It learns passively.
- Accumulates nuance over many conversations.

### Weaknesses

- You cannot control exactly what it stores or how it weights different memories.
- It may store things you did not intend.
- No structured organization. It is a flat list of facts.

### Recommendation

Use Memory as a complement, not a replacement, for explicit context files. Memory picks up incidental preferences. Your Context Stack provides the structured foundation.


## Option 4: Custom GPTs

If you build custom GPTs (via the GPT Builder), you can embed context directly.

### Setup

1. Go to **Explore GPTs** > **Create**
2. In the **Configure** tab, find the **Instructions** field
3. Paste your context components into this field

### What to Include

For a personal assistant GPT:

```
# My Professional Context

## Professional Identity
[Paste professional-identity.md]

## Communication DNA
[Paste communication-dna.md]

## Strategic Context
[Paste strategic-context.md]
```

### Limitations

- Instructions have a character limit (approximately 8,000 characters).
- The GPT is a separate entity from your main ChatGPT interface. You switch to it when you need context-aware interaction.
- Custom GPTs can also accept uploaded knowledge files, which is more scalable than pasting into instructions.


## Combining Approaches

The strongest ChatGPT setup uses multiple layers:

| Layer | What Goes There | Why |
|:------|:----------------|:----|
| Custom Instructions | Condensed identity + style | Always present, every conversation |
| Projects | Full context components | Deep context for focused work |
| Memory | Corrections and preferences over time | Accumulates nuance passively |
| Custom GPT | Role-specific context bundles | Specialized interactions |

Start with Custom Instructions. Add a Project when you want deeper context. Let Memory accumulate naturally.


## Testing Your Setup

Open a new conversation and ask:

```
Based on what you know about me, describe my role and how I prefer
to communicate.
```

If the description is thin or generic, your Custom Instructions need more specificity. If it captures your identity but misses your voice, strengthen the communication-dna content in your response preferences.

Then test with a real task:

```
Draft a one-paragraph update for my leadership team about where we
stand on the platform migration.
```

Evaluate whether it sounds like you wrote it.