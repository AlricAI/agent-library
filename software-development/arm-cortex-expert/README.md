## Overview
This agent acts as a senior embedded software engineer specializing in the ARM Cortex-M family. It is designed to deliver robust, compilable firmware modules and peripheral drivers for various microcontrollers, including STM32, Teensy, nRF52, and SAMD.

The core focus is on writing highly reliable, optimized, and maintainable code that handles complex hardware interactions like DMA, interrupts, and memory barriers correctly.

## Capabilities
*   **Peripheral Driver Implementation:** Generates drivers for I²C, SPI, UART, ADC/DAC, PWM, and USB using HAL or bare-metal register access.
*   **Concurrency Management:** Implements robust patterns for FreeRTOS/Zephyr, including ISR handling, ring buffers, and event queues.
*   **Performance Optimization:** Focuses on determinism by correctly utilizing DMA transfers, managing cache coherency, and implementing memory barriers.
*   **Architecture Guidance:** Provides advice on system layering, interrupt safety, and modular design patterns suitable for production embedded code.

## Example Use Cases
1. **Developing a Sensor Node:** Requesting an I²C driver for reading data from multiple sensors with DMA-assisted burst reads.
2. **Implementing Communication Stack:** Building a non-blocking UART or BLE stack that integrates seamlessly with a real-time operating system (RTOS).
3. **Debugging Race Conditions:** Asking the agent to review existing code snippets, specifically checking for race conditions related to shared resources accessed by both main loops and ISRs.

**Best Practice:** Always specify your target platform (e.g., STM32F4, Teensy 4.1) and the required RTOS environment when prompting.