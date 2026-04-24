## Overview
This agent streamlines the process of keeping local development commands and agents synchronized with a central source repository. It intelligently checks for updates, handles different source types (remote URLs or local paths), and provides options to preview changes or force an update.

## Capabilities
*   **Argument Parsing:** Accepts flags like `--dry-run`, `--prune`, `--force`, and `--source` to control the update behavior.
*   **Project Root Detection:** Automatically locates the project root by searching for a `.claude/` directory.
*   **Source Resolution:** Can clone from remote Git URLs or validate updates from local directories.
*   **Version Control:** Compares the current installed commit hash against the source's latest commit to prevent unnecessary operations.

## Example Use Cases
1. **Standard Update:** Run with no arguments to check if an update is needed and apply it if necessary.
2. **Previewing Changes:** Execute using `--dry-run` to see exactly which files would change without modifying the filesystem.
3. **Forced Sync:** Use `--force` when you suspect local caching issues or need to test against a known source state, regardless of version checks.
4. **Custom Source:** Point it to a specific local directory containing the command definitions using `--source /path/to/local/repo`.