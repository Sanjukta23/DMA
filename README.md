# DMA

STM32CubeIDE example projects exploring the **DMA (Direct Memory Access)** peripheral on the STM32F446RE microcontroller (Nucleo-F446RE). Projects 001–005 are HAL-based, built with STM32CubeMX/STM32CubeIDE, progressing from basic memory-to-memory transfers to peripheral-to-memory DMA use cases. Project 006 is written from scratch at the register level (no HAL drivers) to configure DMA directly.

## Projects

| # | Project | Description |
|---|---------|-------------|
| 001 | `001LED_Toggle` | Toggles an LED using a DMA memory-to-memory transfer (polling mode). HAL-based. |
| 002 | `002LED_Toggle_IT` | Same LED toggle example, driven by DMA in interrupt mode instead of polling. HAL-based. |
| 003 | `003SRAM_SRAM` | DMA memory-to-memory transfer between two SRAM buffers. HAL-based. |
| 004 | `004UART_SRAM_IT` | UART receive data moved into an SRAM buffer via DMA (peripheral-to-memory), using interrupts. HAL-based. |
| 005 | `005ADC_SRAM` | ADC conversion results transferred into an SRAM buffer via DMA (peripheral-to-memory). HAL-based. |
| 006 | `006SRAM_UART_M2P` | Data from an SRAM buffer transmitted over UART via DMA (memory-to-peripheral). Written from scratch at the register level, without HAL drivers. |

## Hardware

- **MCU:** STM32F446RE
- **Board:** Nucleo-F446RE (or any board built around the STM32F446RETx)

## Toolchain

- STM32CubeIDE
- STM32Cube HAL drivers (projects 001–005)
- Bare-metal / register-level, CMSIS only, no HAL (project 006)

## Getting Started

1. Clone the repository.
2. Open the desired project folder (e.g. `001LED_Toggle`) in STM32CubeIDE via **File > Open Projects from File System**.
3. Build and flash to an STM32F446RE-based board.
4. Each project's `.ioc` file can be opened in STM32CubeMX to inspect or regenerate the peripheral configuration.

## Repository Structure

Projects 001–005 follow the standard STM32CubeIDE/HAL layout:

```
<project>/
├── Core/           # Application source (main.c, interrupt handlers, HAL config)
├── Drivers/         # STM32 HAL/CMSIS drivers
├── <project>.ioc    # STM32CubeMX device configuration
├── .cproject / .project
└── STM32F446RETX_FLASH.ld / STM32F446RETX_RAM.ld   # Linker scripts
```

Project 006 (`006SRAM_UART_M2P`) is a bare-metal project without HAL, laid out as:

```
006SRAM_UART_M2P/
├── Inc/            # Headers
├── Src/            # Application source, written at the register level
├── Startup/        # Startup/vector table code
├── .cproject / .project
└── STM32F446RETX_FLASH.ld / STM32F446RETX_RAM.ld   # Linker scripts
```
