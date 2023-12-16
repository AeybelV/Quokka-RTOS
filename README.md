# Quokka

Quokka is a lightweight Real-Time Operating System (RTOS) designed for embedded devices. It provides a minimalistic foundation for building responsive applications on resource-constrained devices.

The operating system is currently a work in progress and is presently being developed and tested on the RP2040 microcontroller.

- [Quokka](#quokka)
  - [Features](#features)
  - [Roadmap](#roadmap)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [Contributing](#contributing)
  - [License](#license)

## Features

- **Lightweight:** Minimal footprint and resource-efficient design.
- **Real-Time Task Scheduling:** Prioritize critical tasks for optimal responsiveness.
- **Configurability:** Easily adaptable to different embedded platforms.

## Roadmap

Quokka RTOS is in a infantile state; currently, the OS has been developed and tested exclusively on the RP2040. The ultimate goal of Quokka RTOS is to become hardware-agnostic, and in the upcoming phases, I plan to broaden its compatibility by conducting testing on additional microcontrollers. including the STM32F446RE and TM4C123GH6PM.

At its current state, the folder structure and CMake files are configured specifically for the RP2040. However, I recognize the importance of adaptability and are actively working on reshaping the build system. Our aim is to make it versatile, allowing compilation for various MCUs, and ensuring easy portability to new boards.

- [ ] **Task Management:**
  - Implement basic task creation, scheduling, and context switching
  - Cooperative and preemptive scheduling
Periodic and switch interrupts, and spin-lock semaphores
  - Establish a minimalistic task management system.
- [ ] **Interrupt Handling:**
  - Develop interrupt handling mechanisms for the RP2040.
  - Implement interrupt service routines (ISRs) and integrate them with the task scheduler.
**Hardware Abstraction Layer (HAL):**
  - Implement a Hardware Abstraction Layer to facilitate easier portability across different microcontrollers.
  - Define a standard interface for hardware-dependent functions.
- [ ] **Board Support Package (BSP):**
  - Develop a Board Support Package specifically for the RP2040.
  - Implement basic hardware abstraction for tasks such as GPIO, timers, and interrupts. Building upon the pico-sdk. The HAL will call the BSP functions
- [ ] Refactor the project structure and build system to allow for compiling for different MCU's. For testing and validation the following microcontrollers will be tested:
  - [ ] **STM32F446RE Integration:**
    - Expand the RTOS to support the STM32F446RE microcontroller.
    - Modify or create a BSP for STM32F446RE.
  - [ ] **TM4C123GH6PM Integration:**
    - Extend compatibility to the TM4C123GH6PM microcontroller.
    - Adapt or create a BSP for TM4C123GH6PM.

When a very rudimetnary kernel is completed, then more features will be implemented.

## Getting Started

### Prerequisites

Before getting started, make sure you have the following installed:

- CMake
- gcc-arm-none-eabi
- libnewlib-arm-none-eabi
- build-essential

Native `gcc` and `g++` are needed to compile pioasm and elf2uf2 as part of the pico SDK. Ubuntu and Debian users might additionally need to also install `libstdc++-arm-none-eabi-newlib`.

### Installation

Pull the latest version of the operating system from GitHub.

```bash
git clone https://github.com/AeybelV/Quokka-RTOS.git
cd quokka-rtos
```

To compile this project firstly initialize and update the submodules. This will initialize the pico-sdk.

```bash
git submodule update --init     # Initializes and updates submodules
```

To setup build system

```bash
mkdir build                     # Makes a output directory for compiled binaries
cd build
cmake ..                        # Writes CMake files.
```

To compile

```bash
make quokka_kernel              # Compiles the Quokka Kernel
```

You will now have compiled binaries that can be flashed to the board in `build/kernel/`. Simply copy the `uf2` file to the board and it will be flashed.

## Contributing

Contributions are welcome! Please read CONTRIBUTING.md for details on how to contribute to this project.

## License

This project is licensed under the MIT License.
