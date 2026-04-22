# Claude Projects

> How to build and load your Context Stack using Claude.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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


*[truncated — see source for full prompt]*