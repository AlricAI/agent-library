# CLAUDE

> This document contains critical guidelines and requirements for Claude when working on Go projects

### tools

- [godoc](https://godoc.org/github.com/

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Development Guidelines for Go Projects

This document contains critical guidelines and requirements for Claude when working on Go projects

### tools

- [godoc](https://godoc.org/github.com/golang/gddo/gosrc)

### 8. Pre-commit Quick Reference

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

### Testing Best Practices:

Use table-driven tests for comprehensive coverage:

```go
func TestFunction(t *testing.T) {
    tests := []struct {
        name    string
        input   string
        want    string
        wantErr bool
    }{
        {"empty input", "", "", false},
        {"valid input", "test", "TEST", false},
        {"error case", "error", "", true},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            got, err := Function(tt.input)
            if tt.wantErr {
                require.Error(t, err)
                return
            }
            require.NoError(t, err)
            assert.Equal(t, tt.want, got)
        })
    }
}
```

### Testing commands

- Unit tests: `go test ./...`
- Race condition tests: `go test -race ./...`
- End-to-end tests: `just test-e2e`
- Integration tests: `go test -tags=integration ./...`

### Documentation Standards:

```go
// Package mcp provides a Model Context Protocol server implementation.
//
// This package implements the full MCP specification, providing handlers
// for tools, resources, and prompts.
//
// Example usage:
//
//	server := mcp.NewServer()
//	server.RegisterTool("example", exampleHandler)
//	if err := server.Start(); err != nil {
//	    log.Fatal(err)
//	}
package mcp

// Server represents an MCP server instance.
// It manages the lifecycle of tools, resources, and client connections.
type Server struct {
    // ...
}

// NewServer creates a new MCP server with defau

*[truncated — see source for full prompt]*