# Plan Qa

> Generate QA test plan YAML from ticket

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping generate a QA test plan from a ticket description, issue tracker ticket, or requirements. This command creates a structured YAML test plan that can be executed with `/start-qa`.

## Step 1: Load Configuration

Check for configuration:

```bash
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
qa:
  apiBaseUrl: ${API_BASE_URL}
  testPlansDir: tests/qa
  resultsDir: tests/qa/results
  timeout: 10
  sqsQueueUrl: ${SQS_QUEUE_URL}
issueTracker:
  type: auto
```

**Default Values:**

```yaml
qa:
  apiBaseUrl: http://localhost:3000
  testPlansDir: tests/qa
  timeout: 10
```

## Step 2: Parse Arguments

Extract from `$ARGUMENTS`:

```
$ARGUMENTS
```

**Patterns to Extract:**

| Pattern                    | Example                              | Meaning                 |
| -------------------------- | ------------------------------------ | ----------------------- |
| Ticket ID                  | `PROJ-123`, `ENG-456`                | Issue tracker ticket    |
| `--url <base_url>`         | `--url https://api.example.com`      | Override API base URL   |
| `--sqs <queue_url>`        | `--sqs https://sqs.../queue`         | SQS queue for events    |
| `--sqs-env <VAR_NAME>`     | `--sqs-env SQS_EVENTS_QUEUE`         | SQS queue from env var  |
| Remaining text             | `Test the /v2/risk endpoint`         | Task description        |

**Parsing Logic:**

```javascript
// Extract ticket ID
const ticketMatch = args.match(/([A-Z]+-\d+)/);
const ticketId = ticketMatch ? ticketMatch[1] : null;

// Extract URL override
const urlMatch = args.match(/--url\s+(\S+)/);
const baseUrl = urlMatch ? urlMatch[1] : config.qa.apiBaseUrl;

// Extract SQS queue
const sqsMatch = args.match(/--sqs\s+(\S+)/);
const sqsEnvMatch = args.match(/--sqs-env\s+(\S+)/);
const sqsQueue = sqsMatch ? sqsMatch[1] : sqsEnvMatch ? `\${${sqsEnvMatch[1]}}` : null;

// Remaining is description
const description 

*[truncated — see source for full prompt]*