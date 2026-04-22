# Phase A Manual Tests

> ## Prerequisites
- `gh` CLI installed and authenticated (`gh auth status`)
- Network connectivity to GitHub

## Test 1: Basic --repo-file-contains

``

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase A: Core Repo Pre-Filtering - Manual Test Script

## Prerequisites
- `gh` CLI installed and authenticated (`gh auth status`)
- Network connectivity to GitHub

## Test 1: Basic --repo-file-contains

```bash
# Find repos containing "Microsoft.Extensions.AI" in any file
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo-file-contains "Microsoft.Extensions.AI" \
  --file-contains "anthropic" \
  --max-results 5
```

**Expected:**
- Shows "Pre-filtering repositories containing files with 'Microsoft.Extensions.AI'"
- Shows "Found N repositories matching pre-filter"
- Then searches for "anthropic" within only those repos
- Displays code matches

## Test 2: Save repos to file

```bash
# Find and save repos
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo-file-contains "Microsoft.Extensions.AI" \
  --save-repos test-repos.txt \
  --max-results 3
```

**Expected:**
- Creates `test-repos.txt` with format:
  ```
  owner1/repo1
  owner2/repo2
  owner3/repo3
  ```

**Verify:**
```bash
cat test-repos.txt
```

## Test 3: Load repos from file

```bash
# Create a test repos file
echo "microsoft/semantic-kernel" > my-repos.txt
echo "dotnet/aspnetcore" >> my-repos.txt

# Search within those repos only
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repos @my-repos.txt \
  --file-contains "async" \
  --max-results 5
```

**Expected:**
- Searches only within microsoft/semantic-kernel and dotnet/aspnetcore
- Shows code matches for "async"

## Test 4: Combined workflow (discover → refine)

```bash
# Step 1: Find AI-related repos and save
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repo-file-contains "OpenAI" \
  --save-repos ai-repos.txt \
  --max-results 10

# Step 2: Search within those repos for specific patterns
dotnet run --project src/cycodgr/cycodgr.csproj -- \
  --repos @ai-repos.txt \
  --file-contains "ChatCompletion" \
  --lines 10
```

**Expected:**
- First command creates ai-repos.txt with 10 repos
- Second command searches 

*[truncated — see source for full prompt]*