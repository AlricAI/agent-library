# USAGE EXAMPLES

> ## Real-World Scenarios

### Scenario 1: New Developer Getting Started

**Sarah just joined a team and needs to set up a development environment:**

`

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎯 OOS Usage Examples

## Real-World Scenarios

### Scenario 1: New Developer Getting Started

**Sarah just joined a team and needs to set up a development environment:**

```bash
# Install OOS once
curl -fsSL https://example.com/scripts/install.sh | bash

# Create new project
mkdir my-api-project
cd my-api-project
oos

# OOS shows:
# 📂 Empty directory - perfect for a new project!
# What do you need?
# 1. 🔐 Just secure environment (.env from 1Password) ← RECOMMENDED
# 2. 🆕 Full project setup with AI tools

# Sarah chooses 1, enters 1Password password
# ✅ Done! .env created with 50 secure variables
# ✅ Added .env to .gitignore
```

### Scenario 2: Existing Project Enhancement

**Mike has a React app and wants to add AI development tools:**

```bash
# Navigate to existing project
cd ~/projects/my-react-dashboard
oos

# OOS detects git repository and shows:
# 🛠️ Enhancing existing project...
# Project: my-react-dashboard
#
# What would you like to add?
# 1. 🔐 Add secure environment (.env from 1Password)
# 2. 🤖 Add AI CLI runners (Claude, Gemini, etc.)
# 3. 🔧 Add development tools (diagnostics, health checks)
# 4. 📋 All of the above

# Mike chooses 4 for full enhancement
# OOS adds AI tools without disrupting existing code
```

### Scenario 3: Quick Environment Setup

**Lisa needs API keys for a hackathon project:**

```bash
# Quick 30-second setup
mkdir hackathon-project
cd hackathon-project
oos

# Choose option 1 (secure environment)
# Enter 1Password password once
# ✅ Done! Ready to code with secure API keys

# Start coding immediately
echo 'console.log("API Key:", process.env.OPENAI_API_KEY)' > test.js
node test.js  # Works with secure keys!
```

### Scenario 4: Team Onboarding

**Company wants to standardize development environments:**

```bash
# IT Department creates setup guide:

# 1. Install OOS (one-time per developer)
curl -fsSL https://company.com/oos-scripts/install.sh | bash

# 2. Each project uses standardized setup
cd any-project
oos  # Context-

*[truncated — see source for full prompt]*