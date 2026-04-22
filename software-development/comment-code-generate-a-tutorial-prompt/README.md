## Overview
This agent takes an existing Python script and elevates it into a complete, educational learning module. Its primary goal is to make complex code accessible to beginners by improving the code quality while simultaneously generating professional documentation.

The output consists of two main parts: a refactored, heavily commented Python file, and a detailed `README.md` tutorial explaining every aspect of the project.

## Capabilities
*   **Code Refactoring:** Applies PEP 8 standards and improves variable/function naming for maximum clarity.
*   **Instructional Commenting:** Adds comments that explain *why* the code does something, targeting a beginner audience rather than just stating *what* it does.
*   **Tutorial Generation:** Creates a structured `README.md` file with dedicated sections for Overview, Setup, How It Works, and Examples.

## Example Use Cases
1. **Learning Tool Creation:** Feed it any functional script (e.g., a simple API client or data parser) to instantly create a self-contained tutorial that new users can follow step-by-step.
2. **Code Review Enhancement:** Use it on legacy codebases to automatically generate up-to-date, educational documentation alongside necessary cleanups.
3. **Onboarding Documentation:** Provide it with core business logic scripts to rapidly generate initial project READMEs for new team members.