# Perplexity

> How to load your Context Stack into Perplexity.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Perplexity

How to load your Context Stack into Perplexity.

Perplexity is primarily a research tool. Loading your context here means search results and analysis are filtered through your domain expertise, strategic priorities, and professional perspective.


## Spaces

Perplexity Spaces are the primary integration point. A Space is a persistent research environment with its own knowledge base.

### Create Your Context Space

1. Open [perplexity.ai](https://perplexity.ai)
2. Click **Spaces** in the left sidebar
3. Click **Create Space**
4. Name it "My Context" (or "Research Base", whatever is clear)

### Add Context Files

In your Space, click **Add files** and upload your context components.

**Recommended files for a research-focused Space:**

```
professional-identity.md    # So Perplexity knows your expertise level
domain-map.md               # So it calibrates depth of explanation
strategic-context.md        # So it prioritizes relevant information
learning-edge.md            # So it focuses on areas where you are growing
```

### Add Custom Instructions

Spaces also support custom instructions. Add a directive that tells Perplexity how to use your context:

```
I am a senior professional researching topics related to my work.
Use the uploaded files to understand my domain expertise and current
priorities. When I search for something:
- Assume I know the basics of my expert domains (no introductory explanations)
- Provide deeper detail on topics in my learning-edge areas
- Prioritize sources relevant to my industry and role
- Flag information that conflicts with or updates my current strategic context
```

### Using Your Context Space

Every search and conversation within the Space draws on your uploaded files. This changes the research experience in several ways:

- **Domain-calibrated answers.** Perplexity skips introductory material for your expert domains and goes deeper.
- **Priority-aware research.** When results span multiple areas, Perplexity can weig

*[truncated — see source for full prompt]*