# STM32 Fundamentals

A hands-on STM32 embedded systems learning project based on the [ControllersTech STM32 Beginner Course](https://controllerstech.com/stm32-beginner-course-learn-stm32-from-scratch/).

The primary target is the **NUCLEO-F446RE (STM32F446RE)**.

For simulation and hardware-independent testing, selected exercises are adapted to the **STM32F103C8T6 (Blue Pill)** and tested in **Wokwi**.

## Current Progress

### Clock Configuration

- System clock configured with STM32CubeMX.
- Primary STM32F446RE project configured for a 180 MHz system clock.
- A separate STM32F103C8T6 configuration is used for Wokwi simulation.

### GPIO

- Configured GPIO output with STM32 HAL.
- Implemented LED blinking using:
  - `HAL_GPIO_WritePin()`
  - `HAL_GPIO_TogglePin()`
- Worked with active-high and active-low LED configurations.
- Adapted the NUCLEO-F446RE PA5 LED example to the Blue Pill PC13 active-low LED for simulation.

### USART / UART

- Configured **USART2** with:
  - 115200 baud
  - 8 data bits
  - no parity
  - 1 stop bit
  - no hardware flow control
  - oversampling by 16
- Implemented polling-based UART transmission with `HAL_UART_Transmit()`.
- Transmitted text strings over UART.
- Converted integer values to text with `sprintf()` and transmitted them over UART.
- Connected USART2 to the Wokwi Serial Monitor for simulation.

## Project Targets

| Purpose | Board / MCU | Notes |
|---|---|---|
| Primary development target | NUCLEO-F446RE / STM32F446RE | Main CubeMX/CubeIDE project |
| Simulation target | Blue Pill / STM32F103C8T6 | Used to test selected exercises in Wokwi |

Because the boards are electrically different, the simulation project is adapted where necessary rather than treated as a byte-for-byte copy of the primary project.

For example, the NUCLEO-F446RE user LED is active-high on PA5, while the Blue Pill LED on PC13 is active-low.

## Tools

- STM32CubeMX
- STM32CubeIDE
- STM32 HAL
- Wokwi
- Git / GitHub
- VSCode

## Repository Structure

```text
.
├── Core/                       # Application source and headers
├── Drivers/                    # STM32 HAL and CMSIS drivers
├── Videos/                     # Project demonstrations
├── .settings/                  # STM32CubeIDE settings
├── STM32_Fundamentals.ioc      # STM32CubeMX configuration
├── STM32F446RETX_FLASH.ld      # Flash linker script
├── STM32F446RETX_RAM.ld        # RAM linker script
├── .project                    # Eclipse/STM32CubeIDE project metadata
├── .cproject                   # C/C++ build configuration used by STM32CubeIDE
├── .mxproject                  # STM32CubeMX project metadata
└── .gitignore
```

Build output directories such as `Debug/` and `Release/` are intentionally excluded from Git.

## Build

1. Open `STM32_Fundamentals.ioc` in STM32CubeMX or STM32CubeIDE.
2. Generate the project code if the CubeMX configuration has changed.
3. Build the project in STM32CubeIDE.
4. Build artifacts are generated locally and are not committed to the repository.

## Wokwi Testing

Selected exercises are reproduced in a separate STM32F103C8T6 project for Wokwi in VSCode.

For the current USART2 test:

- `PA2` — USART2 TX
- `PA3` — USART2 RX
- UART configuration — `115200 8N1`
- Wokwi Serial Monitor is used to inspect transmitted data.

The simulation project is intended for validating concepts and program behavior where possible; the NUCLEO-F446RE remains the primary project target.

## Roadmap

This repository will grow as the STM32 beginner course progresses.

- [x] Clock configuration
- [x] GPIO output and LED blinking
- [x] USART2 configuration
- [x] UART polling transmission
- [x] String and integer transmission
- [x] Wokwi UART/LED simulation
- [ ] UART receive
- [ ] UART interrupts
- [ ] UART DMA
- [ ] ADC
- [ ] I2C
- [ ] SPI
- [ ] Timers and PWM
- [ ] Sensor and external peripheral interfacing

## Status

**Work in progress.**

The goal of this repository is not only to reproduce course examples, but to understand the underlying STM32 peripherals, clocking, GPIO behavior, communication interfaces, and HAL implementation while keeping the project reproducible in Git.