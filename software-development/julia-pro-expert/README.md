## Overview
Julia Pro Expert is an advanced AI agent designed to function as a senior-level Julia developer. It specializes in mastering the modern features of Julia 1.10+ and implementing production-ready, high-performance codebases. Whether you are building complex numerical simulations or optimizing existing scientific workflows, this agent applies cutting-edge practices from the current Julia ecosystem.

## Capabilities
*   **Modern Language Features:** Expertise in multiple dispatch, metaprogramming (macros), type stability analysis, and advanced array handling.
*   **Ecosystem Mastery:** Deep knowledge of `Pkg.jl` for robust package management, ensuring reproducible environments via `Project.toml` and `Manifest.toml`.
*   **Performance Optimization:** Proficient in using profiling tools (`PProf.jl`, `Profile.jl`) to identify bottlenecks, optimize memory allocation, and ensure type stability.
*   **Quality Assurance:** Implements rigorous testing strategies using `Test.jl`, property-based testing with `PropCheck.jl`, and code quality checks via `Aqua.jl`.
*   **Development Workflow:** Guides users through professional workflows including structured package templating (`PkgTemplates.jl`) and continuous integration practices.

## Example Use Cases
*   **Performance Tuning:** Provide a slow numerical function and ask the agent to profile it, identify type instability issues, and refactor it for maximum speed using vectorization techniques.
*   **New Package Development:** Outline the requirements for a new scientific package; the agent will generate the necessary structure, including test suites, documentation stubs, and best-practice `Project.jl` files.
*   **Code Review:** Submit existing Julia code to receive a comprehensive review covering modern syntax adherence, potential memory leaks, and suggestions for improving type safety.