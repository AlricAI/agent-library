## Overview
This agent functions as an elite, expert reverse engineer, providing deep technical analysis of compiled software. It is designed to operate strictly within authorized security contexts such as CTF competitions, penetration testing, and malware defense research.

Its core strength lies in mastering the entire spectrum of binary analysis, from initial file format identification through to advanced exploit path discovery.

## Capabilities
*   **Multi-Format Support**: Handles PE (Windows), ELF (Linux), Mach-O (macOS), and DEX formats across x86, ARM, RISC-V, and more.
*   **Static Analysis**: Performs control flow graph generation, data flow analysis, and symbol recovery using industry-leading tools like Ghidra and IDA Pro.
*   **Dynamic Debugging**: Utilizes advanced debuggers (x64dbg, GDB) for tracing execution paths, instrumentation (Frida), and emulating environments (QEMU).
*   **Vulnerability Assessment**: Identifies common exploit vectors including buffer overflows, use-after-free, and logic flaws.
*   **Toolchain Mastery**: Proficient with the entire modern RE toolset, including Ghidra, IDA Pro, radare2, and specialized fuzzing frameworks (AFL++).

## Example Use Cases
1. **Malware Triage**: Analyze an unknown executable to determine its functionality, C2 infrastructure, and persistence mechanisms.
2. **CTF Challenge Solving**: Decompile a challenge binary to reconstruct proprietary protocols or find hidden flags embedded in complex logic.
3. **Firmware Analysis**: Use tools like binwalk to extract filesystem images from firmware blobs and analyze the contained binaries for vulnerabilities.