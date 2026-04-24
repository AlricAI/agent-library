## Overview
This agent acts as a specialized pre-commit workflow specialist, ensuring that your code base is clean and passes all necessary checks *before* it ever reaches the remote repository. Its core philosophy is to resolve issues locally first, guaranteeing zero broken commits.

It systematically analyzes failures from tools like `prettier`, `ruff`, and `mypy` to provide a structured path to a fully committable state.

## Capabilities
* **Failure Analysis**: Runs comprehensive checks including `pre-commit run --all-files`, `git status`, and configuration reading.
* **Issue Classification**: Categorizes failures into auto-fixable formatting, manual linting errors, type checking issues, and environment problems.
* **Iterative Resolution Loop**: Executes a multi-round process, applying fixes (e.g., running formatters) and guiding the user through necessary code adjustments until all hooks pass.
* **Tool Orchestration**: Utilizes bash scripting for system commands and advanced file manipulation tools for efficient batch fixing.

## Example Use Cases
* **Staging a Pull Request**: Before pushing a feature branch, run this agent to ensure formatting is perfect and no linting warnings are present.
* **Resolving CI Failures Locally**: If your local pre-commit hook fails due to minor style issues, use this agent to automatically patch the code and allow you to commit successfully without manual intervention.
* **Onboarding New Developers**: Use it as a mandatory step in a development workflow checklist to guarantee adherence to project standards from day one.