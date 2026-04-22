# Convergence

> ## 🎯 Overview

🔀 Convergence is a cross-series synthesis blog that reads the latest posts from every other blog series on bagrounds.org and finds hi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔀 Convergence — Product & Engineering Spec

## 🎯 Overview

🔀 Convergence is a cross-series synthesis blog that reads the latest posts from every other blog series on bagrounds.org and finds hidden connections, tensions, and emergent themes. It uses the SQL-like context query engine to pull in posts from explicitly named directories, while each other series reads only its own history.

## 🏗️ Architecture

### 🔗 Cross-Series Context via Context Queries

🔀 Convergence configures contextSources in its JSON config with two queries that drive the generation pipeline:

1. 📖 The first query reads from the convergence directory with a limit of 7, providing continuity with its own recent posts.
2. 📖 The second query reads from the five other series directories (auto-blog-zero, chickie-loo, the-noise, positivity-bias, systems-for-public-good) with limitPerSource of 1, getting the latest post from each.
3. 📦 The engine returns uniform ContextPost records. The buildBlogContext function partitions them by source directory — posts from the convergence directory become self posts, and all others become cross-series posts annotated with series name and icon from the config map.
4. 📝 A "Today Across the Blog" section is included in the user prompt.
5. 🤖 The AI then synthesizes connections across all series.

### 📊 Data Flow

- 🔍 discoverSeries parses convergence.json and its contextSources array.
- ⚙️ evaluateQueries resolves each query against the content directory, reading posts from the listed directories, applying WHERE filters, sorting by ORDER BY, and capping with LIMIT or limitPerSource. It returns uniform ContextPost records tagged with source directory.
- 📋 buildBlogContext partitions ContextPost results into self posts (from the convergence directory) and cross-series posts (from other directories, annotated with metadata from the series config map).
- 📝 buildBlogPrompt adds a "Today Across the Blog" section to the user prompt.
- 🤖 The Gemini API generates

*[truncated — see source for full prompt]*