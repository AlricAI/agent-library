# Phase A Test Results

> **Date:** 2025-12-15  
**Status:** ✅ Core functionality working, minor file-loading issue found

## Tests Performed

### ✅ Test 1: Basic repo pre-filt

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase A Testing Results

**Date:** 2025-12-15  
**Status:** ✅ Core functionality working, minor file-loading issue found

## Tests Performed

### ✅ Test 1: Basic repo pre-filtering works
```bash
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo-file-contains "Microsoft.Extensions.AI" \
  --file-contains "anthropic" \
  --max-results 3
```

**Result:** ✅ PASS
- Pre-filtering found 6 repositories
- Code search was limited to only those repos
- Returned relevant results from pre-filtered repos

### ✅ Test 2: Repo filtering actually limits search scope
```bash
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo-file-contains "semantic-kernel" \
  --file-contains "IKernel" \
  --max-results 2
```

**Result:** ✅ PASS
- Pre-filtering found 4 repositories
- "No results found" - correctly searched only within those 4 repos
- Proves the filtering is working (not searching all of GitHub)

### ✅ Test 3: Using `--repo` directly works
```bash
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo microsoft/semantic-kernel \
  --repo dotnet/aspnetcore \
  --file-contains "async Task" \
  --max-results 2
```

**Result:** ✅ PASS
- Searches within specified repos only
- No errors

### ⚠️  Test 4: File loading has formatting issue
```bash
# Create file
cat > test-repos.txt << 'EOF'
microsoft/semantic-kernel
dotnet/aspnetcore
EOF

# Load from file
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repos @test-repos.txt \
  --file-contains "async Task" \
  --max-results 2
```

**Result:** ⚠️  ISSUE
- Error: Query parsing failed with `\n` characters in repo names
- File loading is reading lines but not parsing correctly
- Could be Windows line ending issue (CRLF vs LF)

**Workaround:** Use `--repo` flag directly instead of file loading for now

### ✅ Test 5: Fixed bug - repos list now used in searches
**Before fix:**
- Pre-filtered repos were added to `command.Repos`
- But `HandleCodeSearchAsync` was using `command.RepoPatterns`
- So pre-filtering was

*[truncated — see source for full prompt]*