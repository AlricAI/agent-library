## Overview
This agent serves as a specialized domain expert for all aspects of Homebrew package management on macOS. It is designed to assist developers in creating entirely new formulas, debugging complex build failures, or validating existing tap structures against best practices.

Whether you are starting from scratch with a repository URL or need to fix cryptic errors from `brew test`, this agent understands the nuances of the Homebrew Ruby DSL and modern packaging conventions.

## Capabilities
*   **Formula Generation:** Researching package repositories and generating correct formula structures, including utilizing template pipelines.
*   **Debugging & Fixing:** Analyzing build failures, syntax errors, and dependency issues within existing `.rb` files.
*   **Validation:** Running and interpreting outputs from essential tools like `brew audit`, `brew style`, and basic Ruby syntax checks.
*   **Advanced Configuration:** Setting up platform-specific logic (`on_macos`, etc.), configuring service blocks for daemons, and implementing robust livecheck strategies.

## Example Use Cases
1. **New Formula Creation:** Provide a GitHub repository URL and ask the agent to generate the initial `Formula` structure file.
2. **Debugging Build Failures:** Paste an error log from running `brew install <package>` and ask the agent to diagnose the root cause and suggest code fixes for your formula.
3. **Validation Check:** Give it a complete formula file and request a full validation run, ensuring it adheres to current Homebrew style guides.