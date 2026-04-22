# Progress

> ## 2025-11-06

- **Markdown Linting Protocol**: Implemented strict markdown validation system for AI agents
  - ✅ Installed markdownlint-cli2 v0.18.1 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Progress Log

## 2025-11-06

- **Markdown Linting Protocol**: Implemented strict markdown validation system for AI agents
  - ✅ Installed markdownlint-cli2 v0.18.1 as dev dependency via pnpm
  - ✅ Created comprehensive `.markdownlint-cli2.jsonc` configuration with 50+ rules enforcing CommonMark/GFM standards
  - ✅ Created `.markdownlintignore` for build artifacts and special files (_.prompt.md, _.chatmode.md)
  - ✅ Added `markdown:lint`, `markdown:fix`, and `markdown:validate` npm scripts
  - ✅ Created `web/scripts/validate-markdown.sh` with colored output and clear guidance for AI agents
  - ✅ Updated lint-staged to run markdownlint before Biome formatting on \*.md files
  - ✅ Fixed all 165 violations across 58 markdown files in repository
  - ✅ Created comprehensive documentation in `memory-bank/reference/markdown-protocol.md`
  - ✅ Updated `.github/copilot-instructions.md` with mandatory validation workflow
  - ✅ Updated `AGENTS.md` with quick reference for Codex CLI agents
  - ✅ All markdown files now pass strict validation (0 errors)
  - 📋 **Key Rules**: ATX headings, dash lists, 2-space indent, no trailing spaces/tabs, code blocks with language, alt text for images, no bare URLs, single trailing newline
  - 🔧 **AI Agent Workflow**: Run `pnpm markdown:validate` after changes, fix violations, report status

## 2025-11-03

- **Dashboard Hydration & Charts**: Resolved ThemeToggle hydration mismatch and silenced Recharts dimension spam
- **Complete Clean Slate Achieved**: All errors resolved, hydration patterns validated, development environment fully operational
  - ✅ Fixed TypeScript health API route types (database info structure, removed unused NextRequest parameter)
  - ✅ Organized all imports with Biome auto-fix (page.tsx import sorting)
  - ✅ Added proper biome-ignore comment for intentional forEach side effect in test utils
  - ✅ Verified hydration prevention patterns:
    - ThemeToggle: mounted state guard with useEffect ✅
    - Dashboard charts: chart

*[truncated — see source for full prompt]*