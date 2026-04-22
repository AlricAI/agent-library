---
name: Perplexity
description: How to load your Context Stack into Perplexity.
model: claude-sonnet-4-5
---
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
- **Priority-aware research.** When results span multiple areas, Perplexity can weight relevance to your current priorities.
- **Learning-edge focus.** For topics you are actively learning, Perplexity provides more foundational context.


## Space Configurations for Different Purposes

Create multiple Spaces with different context subsets:

### General Research Space

```
professional-identity.md
domain-map.md
strategic-context.md
learning-edge.md
```

Best for: Open-ended research, industry trends, competitive analysis.

### Technical Research Space

```
domain-map.md
tool-ecosystem.md
learning-edge.md
```

Best for: Evaluating tools, technical deep-dives, architecture research.

### Strategic Research Space

```
professional-identity.md
strategic-context.md
decision-architecture.md
domain-map.md
```

Best for: Market analysis, strategy validation, business case research.


## What Not to Load

Some context components add little value in a research context:

- **communication-dna.md**: Perplexity generates research summaries, not communications in your voice. Style matters less here.
- **brand-voice.md**: Same reasoning. You are consuming information, not producing branded content.
- **operating-rhythm.md**: Not relevant to search and analysis.
- **collaboration-profile.md**: Not relevant to individual research.

Keep your research Spaces focused on Substance and Situation layers.


## Updating Your Space

When your strategic priorities shift or you move into new learning areas:

1. Open your Space settings
2. Remove outdated files
3. Upload updated versions

Pay particular attention to `strategic-context.md` (update monthly) and `learning-edge.md` (update quarterly). Stale priorities lead to stale research focus.


## Limitations

- Perplexity Spaces require a Pro subscription for full file upload capabilities.
- File size limits apply. Keep each context component concise.
- Perplexity uses your context files to inform search and analysis, but it does not memorize them across sessions the way some other platforms do. The files must remain in the Space.


## Testing Your Setup

Open a search in your Context Space and try a query related to your domain:

```
What are the latest trends in [your industry] that could affect [your current priority]?
```

Evaluate whether:
- The response assumes your expertise level (no unnecessary basics)
- The sources are relevant to your industry and role
- The analysis connects to your strategic context

If the response feels generic, your domain-map and strategic-context files may need more specificity about what you already know and what you are trying to accomplish.