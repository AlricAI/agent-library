# FIX CI README

> This directory contains the `fix-failing-ci-checks` command for automatically detecting, diagnosing, and fixing failing CI checks for pull requests.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fix Failing CI Checks

This directory contains the `fix-failing-ci-checks` command for automatically detecting, diagnosing, and fixing failing CI checks for pull requests.

## Installation

The command is automatically available as part of the ModPorter AI CLI.

## Usage

### As a standalone script:

**Linux/macOS:**
```bash
./scripts/fix-failing-ci-checks
```

**Windows:**
```cmd
scripts\fix-failing-ci-checks.bat
```

### As part of the ModPorter CLI:

```bash
python -m modporter.cli fix-ci
```

## Prerequisites

- Must be in a git repository with a GitHub remote
- Must have the GitHub CLI (`gh`) installed and authenticated
- Must have local test environment set up (pytest, etc.)

## Command Options

```bash
fix-failing-ci-checks [OPTIONS]

Options:
  --repo-path PATH    Path to the repository (default: current directory)
  -v, --verbose       Enable verbose logging
  --version           Show version and exit
  --help              Show help message
```

## How It Works

When executed, the command will:

1. **Detect Current PR**: Automatically find the pull request associated with the current branch
2. **Identify Failing Jobs**: Check GitHub Actions/CI for any failing jobs
3. **Download Logs**: Fetch detailed logs from all failing jobs
4. **Analyze Failures**: Parse logs to categorize and identify specific failure types:
   - Test failures
   - Linting errors
   - Type checking errors  
   - Build errors
   - Dependency issues
5. **Apply Automatic Fixes**: Where possible, automatically fix issues:
   - Format code with `black`
   - Sort imports with `isort`
   - Remove unused imports with `autoflake`
   - Install missing dependencies
6. **Create Backup**: Before making changes, create a backup branch
7. **Commit Changes**: Commit fixes with descriptive commit messages
8. **Verify Fixes**: Run local tests to ensure fixes work
9. **Rollback if Needed**: If verification fails, automatically rollback changes

## Supported Fix Types

### Automatic Fixes

- **Linting Er

*[truncated — see source for full prompt]*