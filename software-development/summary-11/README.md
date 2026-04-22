# Summary

> ## Overview
The `bin/` directory contains executable CLI tools for the qtests framework.

## Files and Their Roles

### qtests-generate (Primary CLI, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# bin/ Directory Summary

## Overview
The `bin/` directory contains executable CLI tools for the qtests framework.

## Files and Their Roles

### qtests-generate (Primary CLI, backward-compatible alias: qtests-ts-generate)
**Role**: Command-line interface for generating automated TypeScript tests  
**Key Features**:
- Supports multiple analysis modes: `heuristic` (default) and `ast` (TypeScript AST)
- Scope: Integration tests only  
- Safety features: `--dry-run` (preview without writing), `--force` (overwrite generated files)
- File filtering: `--include` and `--exclude` glob patterns
- Configurable source and test directories
 - React-aware options: `--react` to force React mode; `--with-router` to wrap detected React Router components with `MemoryRouter`
 - Package script update: `--update-pkg-script` opt-in to update `package.json` test script

**Recent Updates**:
- New primary command name `qtests-generate` established (maintains `qtests-ts-generate` as backward-compatible alias).
- **Recommended Usage**: Prefer `qtests-generate` for new projects; `qtests-ts-generate` supported for legacy compatibility.
- Imports compiled generator from `../dist/lib/testGenerator.js` for predictable runtime without tsx.
- ALWAYS writes/overwrites `qtests-runner.mjs` at the client root (INIT_CWD) using a validated API‑only template (runCLI + API Mode).

**Command Examples**:
```bash
qtests-generate                           # Scan current directory with defaults
qtests-generate --src lib                 # Scan 'lib' directory instead  
qtests-generate --integration --dry-run    # Preview integration tests only
qtests-generate --mode ast --force        # Use TypeScript AST analysis, overwrite existing
qtests-generate --include "**/*.ts"       # Only process TypeScript files
qtests-generate --exclude "**/demo/**"    # Skip demo directories
qtests-generate --react --with-router     # Force React mode and wrap Router components
qtests-generate --update-pkg-script       # Opt-in to u

*[truncated — see source for full prompt]*