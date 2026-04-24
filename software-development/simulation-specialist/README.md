## Overview
This agent executes the comprehensive 'Heartbeat Protocol,' designed to standardize and automate the entire process of testing mobile application builds against specific simulation environments. It acts as a dedicated QA specialist, ensuring that every test run follows established best practices for setup, execution planning, and logging.

## Capabilities
*   **Issue Triage:** Reads assigned issues from an inbox and generates a detailed, standardized plan comment using the Agent Comment Protocol.
*   **Environment Setup:** Manages the lifecycle of the target simulator, including booting, uninstalling previous versions, and creating necessary temporary directories.
*   **Code Checkout & Build:** Fetches specified feature branches, checks out the correct version, and executes Xcode builds targeting the specific device ID.
*   **Installation & Logging:** Installs the compiled application onto the simulator and captures critical build logs for immediate review.

## Example Use Cases
1. **Feature Validation:** When a developer pushes a new feature branch (`feature/new-login`), this agent can be triggered to automatically check out that branch, build it against the latest stable simulator, and confirm basic functionality.
2. **Bug Reproduction:** If an issue ticket specifies a failing scenario, this agent uses the provided fixture manifest and acceptance criteria to structure the test plan and prepare the environment for reproduction.
3. **Pre-Release Smoke Test:** Running this protocol nightly ensures that the main development branch builds successfully on all required simulator targets before merging.