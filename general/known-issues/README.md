# KNOWN ISSUES

> ## OpenAI Integration

**Status**: ✅ Compiles against async-openai 0.31.1; needs live API verification

**Issue**: The provider was updated to the 0.3

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Known Issues

## OpenAI Integration

**Status**: ✅ Compiles against async-openai 0.31.1; needs live API verification

**Issue**: The provider was updated to the 0.31.1 API (tool enums, tool list conversion, and tool-call parsing). Compile errors are resolved; runtime/tool-calling correctness still needs validation with a real OpenAI endpoint.

**Impact**: 
- Builds now succeed with the `openai` feature
- Tool calling should work, but has not been exercised against the real API
- Further adjustments may be needed after end-to-end testing

**Workaround**:
- Prefer Ollama or LlamaCpp for local-first workflows
- If using OpenAI, run targeted E2E tests with a real API key

**Next Steps**:
1. Run live tests with a real OpenAI key to validate tool calling and streaming
2. Add mocked/OpenAI-contract tests if feasible
3. Update docs with any model-specific nuances

## GPU Backend Compilation

**Status**: ⚠️ Requires platform-specific SDKs

**Issue**: Building with GPU features requires installed SDKs:
- `llamacpp-cuda`: Requires CUDA Toolkit
- `llamacpp-metal`: macOS only, requires Xcode
- `llamacpp-vulkan`: Requires Vulkan SDK

**Impact**:
- `--all-features` builds will fail without SDKs installed
- Per-platform builds work fine

**Workaround**:
```bash
# Use specific features instead of --all-features
cargo build --features "ollama,llamacpp,local-db"

# Or enable GPU only if SDK is installed
cargo build --features "llamacpp-cuda"  # if CUDA is available
```

**Documentation**: See `docs/GGUF_USAGE.md` for GPU setup instructions

## Test Coverage

**Status**: ✅ Core features fully tested

**Details**:
- 277+ tests total (152 lib + 125 integration)
- Ollama: Full coverage with wiremock
- LlamaCpp: Needs integration tests with real GGUF models
- OpenAI: Tests disabled pending API fixes

**Recommendations**:
1. Add E2E tests with real Ollama instance in CI
2. Add LlamaCpp tests with tiny test model
3. Fix OpenAI and re-enable tests

## Windows-Specific

**Status**: ✅ Works w

*[truncated — see source for full prompt]*