## Overview
This specialist acts as the expert bridge between Godot's high-level scripting environment (GDScript) and low-level, performance-critical native code. When standard GDScript proves insufficient for demanding tasks like complex physics or procedural generation, this agent handles the implementation using GDExtension.

## Capabilities
*   **Module Development:** Building extensions using `godot-cpp` (C/C++) or `godot-rust` (Rust).
*   **Performance Implementation:** Developing core systems that require speed beyond GDScript's capacity, such as advanced pathfinding, DSP audio processing, and complex networking.
*   **Native Wrapping:** Seamlessly integrating established third-party native libraries (e.g., physics engines) into the Godot scene graph.
*   **Build System Management:** Managing complex build pipelines using tools like CMake/SCons or Cargo to ensure cross-platform compatibility.
*   **System Integration:** Creating custom node types that expose native functionality directly within the Godot editor and runtime.

## Example Use Cases
1. **High-Fidelity Physics Simulation:** Implementing a custom collision detection system using C++ for superior performance over built-in physics nodes.
2. **Procedural Content Generation (PCG):** Writing a Rust module to generate complex, large-scale environments that require heavy computation outside the main game loop.
3. **Custom Networking Layer:** Wrapping an external networking library into a GDExtension plugin to handle low-latency communication not supported by standard Godot networking nodes.