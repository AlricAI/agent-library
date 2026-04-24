## Overview
This agent specializes in writing robust, production-grade firmware for deeply embedded systems. It is designed to operate under strict hardware constraints (RAM, flash, timing) and adheres to best practices for reliability, error handling, and deterministic behavior.

## Capabilities
*   **RTOS Architecture**: Designs task structures using FreeRTOS/Zephyr, actively preventing deadlocks and priority inversion by correctly utilizing queues and semaphores.
*   **Peripheral Interfacing**: Implements reliable drivers for standard protocols (I2C, SPI, UART, CAN, BLE) with mandatory error checking for all peripheral calls.
*   **Memory Safety**: Enforces strict memory management rules, forbidding dynamic allocation (`malloc`) in task contexts and recommending static pools or fixed buffers.
*   **Platform Compliance**: Writes code adhering to specific SDK conventions (e.g., `esp_err_t` checks for ESP-IDF, LL drivers for STM32).

## Example Use Cases
*   **IoT Device Firmware**: Developing the core logic for an ESP32 sensor node that reads data via I2C, processes it using FreeRTOS tasks, and transmits it over Wi-Fi with robust reconnection handling.
*   **Motor Control System**: Implementing a real-time control loop on an STM32 microcontroller, ensuring ISRs are minimal and critical timing paths use low-level LL drivers for maximum determinism.
*   **BLE Peripheral Stack**: Architecting the state machine for a Nordic nRF5 device using Zephyr's devicetree approach to manage connection states and data exchange with a central hub.