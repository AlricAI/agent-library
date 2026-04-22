# Start

> Start a new PR by creating a feature branch following repo conventions

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping create a new pull request. Your task is to create a properly named feature branch, optionally fetch ticket details, and store context for subsequent commands.

## Step 1: Load Configuration

Check for `.claude/config.yaml` to load project-specific settings:

```bash
# Check if config exists
if [ -f ".claude/config.yaml" ]; then
  echo "CONFIG_EXISTS=true"
else
  echo "CONFIG_EXISTS=false"
fi
```

**Configuration Priority:**

1. `.claude/config.yaml` (if exists)
2. Auto-detection (package.json, pyproject.toml, etc.)
3. Sensible defaults

**Default Values (when no config):**

```yaml
workflow:
  type: staging
  developmentBranch: staging
  productionBranch: main
branches:
  feature: "{type}/{ticket}-{description}"
commits:
  types: [Feature, Fix, Hotfix, Refactor, Docs, Test, Chore]
  requireTicket: false
  ticketPattern: "^[A-Z]+-\\d+$"
issueTracker:
  type: auto
```

## Step 2: Gather Information

Ask the user for the following information (use AskUserQuestion tool):

### Question 1: Ticket ID

**Question**: "What is the ticket ID or URL?"

- Examples:
  - `PROJ-1234` (Jira format)
  - `ENG-456` (Linear format)
  - `#789` (GitHub issue)
  - `https://linear.app/team/issue/ENG-456/...`
  - `https://your-org.atlassian.net/browse/PROJ-1234`

**Parsing Logic:**

- Extract ticket ID from URL if provided
- Linear: Pattern `/issue/([A-Z]+-\d+)/`
- Jira: Pattern `/browse/([A-Z]+-\d+)`
- GitHub: Pattern `issues/(\d+)` or `#(\d+)`

**Validation:**

- If `commits.requireTicket: true` in config, ticket is required
- Validate against `commits.ticketPattern` if provided
- If no ticket provided and not required, proceed without it

### Question 2: Change Type

**Question**: "What type of change is this?"

**Options** (from config or defaults):

- `feature` - New feature or enhancement
- `fix` - Bug fix
- `hotfix` - Urgent production fix
- `chore` - Maintenance, dependencies, etc.
- `refactor` - Code refactoring
- `docs` - Documentation changes

### Question 3: Short

*[truncated — see source for full prompt]*