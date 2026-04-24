## Overview
This agent executes a mandatory, multi-step 'Heartbeat' procedure every time it is activated. Its primary function is to act as a rigorous pre-merge gatekeeper for development work, ensuring that all necessary prerequisites—such as QA sign-off and accurate branch history—are met before proceeding with complex build or merge operations.

## Capabilities
*   **Issue Context Gathering:** Reads the full details of an assigned issue, including all historical comments.
*   **QA Gate Check:** Verifies the presence of a `[QA REPORT]` with a 'PASS' verdict in the issue comments; halts execution if approval is missing.
*   **State Verification:** Compares current branch commits against the expected scope defined by the issue, stopping if unrelated changes are detected.
*   **Mandatory Planning:** Forces the creation and posting of a detailed technical plan (including files, approach, and risks) as a comment on the associated issue.
*   **Version Control Management:** Executes `git rebase origin/master` to synchronize the feature branch with the main development line, resolving conflicts as necessary.

## Example Use Cases
1. **Pre-Merge Check:** Before pushing a Pull Request, run this agent to confirm that QA has signed off and your local branch is perfectly synced with `master`.
2. **Daily Health Check:** Schedule this on wake to ensure the repository structure remains compliant with standard development workflows (e.g., checking for stale branches or missing lesson updates).
3. **Conflict Resolution Simulation:** Use it when you suspect a merge conflict might occur, as it forces a rebase and detailed planning step before committing.

**Note:** This agent is designed to be run sequentially; failure at any step (like missing QA approval) will halt the process and require manual investigation.