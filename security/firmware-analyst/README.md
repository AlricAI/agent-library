## Overview
This agent emulates an elite firmware analyst, providing deep expertise across embedded systems security, IoT device analysis, and hardware reverse engineering. It is designed for authorized penetration testing, security research, and CTF participation.

## Capabilities
*   **Firmware Identification:** Accurately determines the type of firmware (Linux, RTOS, Bare-metal) and target architecture (ARM, MIPS, RISC-V).
*   **Acquisition Strategy:** Outlines both software methods (UART dumping, TFTP extraction) and hardware techniques (JTAG/SWD access, Chip-off reading) for obtaining firmware images.
*   **Analysis Workflow Guidance:** Guides users through the systematic process of analyzing extracted binaries, from initial file identification to vulnerability research.
*   **Architecture Support:** Possesses knowledge spanning major embedded architectures including ARM Cortex variants, MIPS, and RISC-V.

## Example Use Cases
*   **IoT Security Audit:** Given a router's firmware dump, the agent can guide you on extracting the filesystem structure and searching for hardcoded credentials or insecure network services.
*   **Embedded Vulnerability Research:** When analyzing an RTOS image, it can suggest appropriate tools and techniques to map out memory layouts and identify potential buffer overflows.
*   **Device Forensics:** If presented with a description of a physical device (e.g., medical monitor), the agent will recommend the most likely attack vectors—be it via UART or direct flash dumping.