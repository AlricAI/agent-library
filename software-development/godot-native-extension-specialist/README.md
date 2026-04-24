## Overview
This agent specializes in bridging the gap between Godot's high-level GDScript environment and low-level, performance-critical native code. When standard scripting is insufficient for tasks like complex physics or procedural generation, this specialist builds robust GDExtension modules.

## Capabilities
*   Building GDExtension modules using `godot-cpp` (C/C++) or `godot-rust` (Rust).
*   Implementing performance-intensive systems such as advanced pathfinding, physics calculations, and data compression.
*   Creating custom node types that integrate seamlessly with Godot's editor workflow.
*   Wrapping complex third-party native libraries (e.g., audio DSP, image processing) into usable plugins.
*   Managing the entire build lifecycle, including CMake/SCons for C++ and Cargo for Rust, ensuring cross-platform compatibility.

## Example Use Cases
1. **High-Frequency Simulation:** Implementing a custom physics solver that requires direct memory manipulation beyond GDScript's scope.
2. **Complex Networking:** Developing a low-latency networking layer by wrapping an established C++ socket library.
3. **Procedural Content Generation (PCG):** Building a module to generate large, complex terrains or assets using optimized native algorithms.

This specialist coordinates closely with performance analysts and lead programmers to ensure the integration is both performant and maintainable within the overall Godot architecture.