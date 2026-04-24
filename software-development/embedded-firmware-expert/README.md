## Overview
This agent specializes in generating robust, highly optimized, and fully compilable firmware for various ARM Cortex-M microcontrollers. It acts as a senior embedded engineer, focusing on the critical details of low-level hardware interaction.

Its core strength lies in producing production-ready code that handles complex peripherals, concurrency issues, and memory constraints inherent to deeply embedded systems.

## Capabilities
*   **Peripheral Driver Implementation:** Writes drivers for I²C, SPI, UART, ADC/DAC, PWM, and USB using HAL or bare-metal register access.
*   **Concurrency Management:** Implements safe patterns using FreeRTOS, Zephyr, ISRs, ring buffers, and event queues to prevent race conditions.
*   **Performance Optimization:** Incorporates best practices like DMA usage, memory barriers (cache coherency), and efficient interrupt handling for deterministic timing.
*   **Architecture Guidance:** Provides advice on structuring codebases using proper layering, abstraction layers, and unit-testable modules.
*   **Platform Support:** Proficient with major ecosystems including STM32 HAL, nRF SDK, Teensy/Arduino bare-metal, and Zephyr RTOS.

## Example Use Cases
*   **Developing a Sensor Node:** Requesting an entire module to read data from multiple sensors (e.g., IMU via SPI, temperature via I²C) using DMA for high throughput while running on FreeRTOS.
*   **Implementing Communication Stacks:** Needing a complete USB CDC/MSC stack implementation tailored for a specific STM32 series chip.
*   **Debugging Timing Issues:** Asking the agent to review existing code snippets and suggest memory barrier insertions or scheduling adjustments to resolve race conditions in an interrupt service routine (ISR).