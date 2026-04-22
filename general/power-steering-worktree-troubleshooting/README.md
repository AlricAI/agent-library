# Power Steering Worktree Troubleshooting

> Practical guide for fixing common Power Steering issues in git worktree environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Troubleshoot Power Steering in Worktrees

Practical guide for fixing common Power Steering issues in git worktree environments.

## Quick Diagnosis

Run this diagnostic command to check your Power Steering configuration:

```bash
python3 << 'EOF'
import os
import subprocess
from pathlib import Path

print("=== Power Steering Worktree Diagnostic ===\n")

# Check if in git repo
try:
    subprocess.check_output(["git", "rev-parse", "--git-dir"], stderr=subprocess.DEVNULL)
    print("✓ Git repository detected")
except:
    print("✗ Not a git repository")
    exit(1)

# Check worktree status
common_dir = subprocess.check_output(
    ["git", "rev-parse", "--git-common-dir"], text=True
).strip()
git_dir = subprocess.check_output(
    ["git", "rev-parse", "--git-dir"], text=True
).strip()

is_worktree = os.path.abspath(common_dir) != os.path.abspath(git_dir)
print(f"Worktree: {'Yes' if is_worktree else 'No'}")
print(f"Common dir: {common_dir}")
print(f"Git dir: {git_dir}")

# Check state directory
state_dir = Path(common_dir) / ".claude" / "runtime" / "power-steering"
print(f"\nState directory: {state_dir}")
print(f"Exists: {state_dir.exists()}")

if state_dir.exists():
    counter_file = state_dir / "workflow_classification_block_counter.json"
    print(f"Counter file: {counter_file}")
    print(f"Exists: {counter_file.exists()}")
    if counter_file.exists():
        import json
        with open(counter_file) as f:
            print(f"Counter data: {json.load(f)}")

# Check .disabled file
disabled_locations = [
    Path(".disabled"),
    Path(common_dir) / ".claude" / "runtime" / "power-steering" / ".disabled",
    Path(subprocess.check_output(
        ["git", "rev-parse", "--show-toplevel"], text=True
    ).strip()) / ".disabled"
]

print("\n.disabled file locations:")
for loc in disabled_locations:
    exists = loc.exists()
    print(f"  {'✓' if exists else '✗'} {loc}")
    if exists:
        print(f"    → Power Steering disabled via this file")

print("\n=== 

*[truncated — see source for full prompt]*