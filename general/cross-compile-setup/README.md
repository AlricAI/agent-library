# CROSS COMPILE SETUP

> ## Date: 2025-11-17

This document summarizes all changes made to enable cross-compilation for the `remembrances-mcp` project.

## Identified Issues



## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cross-Compilation Setup Summary

## Date: 2025-11-17

This document summarizes all changes made to enable cross-compilation for the `remembrances-mcp` project.

## Identified Issues

During the initial execution of `./scripts/release-cross.sh`, the following issues were encountered:

### 1. Library Compilation Script
- **Issue**: The command `bash scripts/build-libs-cross.sh` failed because goreleaser-cross did not recognize the command.
- **Solution**: Added `--entrypoint /bin/bash` to the docker run command in `build_shared_libraries()`.

### 2. Duplicate Replace Directives in go.mod
- **Issue**: Two `replace` directives pointed to the same directory, causing a Go error:
```
replace github.com/madeindigio/go-llama.cpp => ~/www/MCP/Remembrances/go-llama.cpp
replace github.com/go-skynet/go-llama.cpp => ~/www/MCP/Remembrances/go-llama.cpp
```
- **Solution**: Removed the duplicate directive for `go-skynet/go-llama.cpp`.

### 3. Docker Volumes Not Mounted
- **Issue**: GoReleaser could not access `~/www/MCP/Remembrances/` for local modules.
- **Solution**: Added volume mount in `run_goreleaser()`:
```bash
-v "~/www/MCP/Remembrances:~/www/MCP/Remembrances"
```

### 4. CURL Dependency in llama.cpp
- **Issue**: CMake required CURL, which was not available in the container.
- **Solution**: Disabled CURL in CMake flags:
```bash
-DLLAMA_CURL=OFF
```

### 5. Outdated Vendor Directory
- **Issue**: The vendor directory was not synchronized with go.mod.
- **Solution**: Added `go mod vendor` to the before hooks in `.goreleaser.yml`.

### 6. Rust/Cargo Not Available
- **Issue**: The goreleaser-cross container did not have Rust installed to compile surrealdb-embedded.
- **Solution**: Created a custom Docker image with Rust.

### 7. Missing macOS Tools
- **Issue**: `install_name_tool` not available for macOS cross-compilation.
- **Status**: Pending - the custom image should resolve this with osxcross.

## Created Files

### 1. `docker/Dockerfile.goreleaser-custom`
Custom Dockerfile

*[truncated — see source for full prompt]*