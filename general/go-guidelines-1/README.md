# GO GUIDELINES

> This guide outlines the coding standards for the floop project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Go Development Guidelines

This guide outlines the coding standards for the floop project.

## 1. Project Structure

- **`cmd/floop/`** — CLI entry point
- **`internal/`** — All application packages. Run `ls internal/` for current list.
- **`docs/`** — Documentation
- **`.floop/`** — Learned behaviors (JSONL + manifest tracked; DB + audit.jsonl gitignored)
- **`.beads/`** — Issue tracking (version controlled)

## 2. Code Style

### Formatting
- Always use `gofmt` or `goimports`
- Run `go fmt ./...` before committing

### Naming
- `CamelCase` for exported identifiers
- `camelCase` for unexported identifiers
- Short but descriptive names (`ctx` for context, `b` for behavior in loops)
- Package names: short, lowercase, singular (`models`, `store`, `learning`)

### Error Handling
- Return errors as the last return value
- Check errors immediately after function calls
- Wrap errors with context using `fmt.Errorf("doing X: %w", err)`
- Never panic except for truly unrecoverable initialization errors

```go
// Good
result, err := doSomething()
if err != nil {
    return fmt.Errorf("failed to do something: %w", err)
}

// Bad
result, _ := doSomething()  // Don't ignore errors
```

## 3. Testing

### Requirements
- All packages must have `*_test.go` files
- Use table-driven tests for functions with multiple input cases
- Test both success and error paths

### Running Tests
```bash
go test ./...                    # Run all tests
go test ./internal/models/...    # Run specific package
go test -v -cover ./...          # Verbose with coverage
```

### Test File Structure
```go
func TestFunctionName(t *testing.T) {
    tests := []struct {
        name    string
        input   InputType
        want    OutputType
        wantErr bool
    }{
        {"valid input", validInput, expectedOutput, false},
        {"invalid input", invalidInput, nil, true},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            got, err := FunctionName(tt.input)

*[truncated — see source for full prompt]*