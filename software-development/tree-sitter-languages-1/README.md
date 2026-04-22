# TREE SITTER LANGUAGES

> This document details the programming languages supported by the Code Indexing System, including which symbol types are extracted and any language-specific considerations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tree-Sitter Language Support

This document details the programming languages supported by the Code Indexing System, including which symbol types are extracted and any language-specific considerations.

## Supported Languages Overview

| Language | ID | Extensions | Symbol Extraction | Notes |
|----------|-----|------------|-------------------|-------|
| Go | `go` | `.go` | ✅ Full | Excellent support |
| TypeScript | `typescript` | `.ts`, `.mts`, `.cts` | ✅ Full | Including decorators |
| JavaScript | `javascript` | `.js`, `.mjs`, `.cjs`, `.jsx` | ✅ Full | ES6+ supported |
| TSX | `tsx` | `.tsx` | ✅ Full | React components |
| Python | `python` | `.py`, `.pyw`, `.pyi` | ✅ Full | Classes, functions, decorators |
| Java | `java` | `.java` | ✅ Full | Full OOP support |
| Kotlin | `kotlin` | `.kt`, `.kts` | ✅ Full | Including data classes |
| Rust | `rust` | `.rs` | ✅ Full | Traits, impls, macros |
| PHP | `php` | `.php`, `.phtml` | ✅ Full | Classes, traits, interfaces |
| Swift | `swift` | `.swift` | ✅ Full | Protocols, extensions |
| C | `c` | `.c` | ✅ Full | Functions, structs |
| C++ | `cpp` | `.cpp`, `.cc`, `.cxx`, `.hpp` | ✅ Full | Classes, templates |
| C# | `csharp` | `.cs` | ✅ Full | Full .NET support |
| Ruby | `ruby` | `.rb`, `.rake`, `.gemspec` | ✅ Full | Modules, classes |
| Scala | `scala` | `.scala`, `.sc` | ✅ Full | Objects, traits |
| Bash | `bash` | `.sh`, `.bash`, `.zsh` | ⚠️ Partial | Functions only |

## Language Details

### Go

**Extensions**: `.go`

**Extracted Symbols**:
- `package` - Package declarations
- `function` - Standalone functions
- `method` - Methods with receivers
- `struct` - Struct type definitions
- `interface` - Interface definitions
- `type` - Type aliases
- `constant` - Const declarations
- `variable` - Var declarations

**Example**:
```go
package main

type UserService struct {
    db *Database
}

func (s *UserService) GetUser(id string) (*User, error) {
    return s.db.Find(id)
}

func NewUserService(db *Database) *UserServ

*[truncated — see source for full prompt]*