# CLAUDE

> This document contains critical guidelines and requirements for Claude when working on Go projects

## IMPORTANT!!

- Ask questions whenever you are u

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude General Development Guidelines

This document contains critical guidelines and requirements for Claude when working on Go projects

## IMPORTANT!!

- Ask questions whenever you are unsure about something
- Ask for clarification whenever something is ambiguous or unclear
- Ask follow up questions when an answer was not helpful or did not fully address your question
- Repeat your understanding of my response back to me to ensure clarity and accuracy

## Quick Reference:

### Using the Justfile

The Justfile contains all development automation commands. When working on this project:

1. **Always use Just commands** instead of raw go/make commands
2. **Test your changes** with `just test` before any commit
3. **Check code quality** with `just lint` and `just fmt`
4. **Build documentation** with `just docs` after API changes
5. **Run full CI locally** with `just ci` before pushing

Common commands:
- `just dev` - Start development server with hot reload
- `just test` - Run all tests with race detection
- `just lint` - Run golangci-lint and format check
- `just build` - Build optimized binary
- `just docs-serve` - Serve documentation locally

### Pre-commit:
```markdown
Pre-commit checks:

1. Go formatting (gofmt, gofumpt, goimports)
2. Linting (golangci-lint, go vet)
3. Security scanning (gosec, gitleaks)
4. Test execution
5. Build verification
6. Module tidiness
```

---

## STRICT REQUIREMENTS

### 1. Test Driven Development (TDD)

**REQUIREMENT**: Follow strict TDD practices with RED-GREEN-REFACTOR pattern:

1. **RED**: Write a failing test FIRST
2. **GREEN**: Write minimal code to make the test pass
3. **REFACTOR**: Improve the code while keeping tests green

**NEVER** write implementation code before writing tests.

### 2. 100% Test Passing Rate
**REQUIREMENT**: ALL tests must pass 100% before any commit:
<language-specific-test-commands-here>
</language-specific-test-commands-here>
**NO EXCEPTIONS** - If a test fails, fix it before proceeding.

### 3. Docu

*[truncated — see source for full prompt]*