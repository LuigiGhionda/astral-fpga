
# Astral FPGA emulation

## Overview

This project is set up to build and deploy software on the Astral platform by using FPGA emulation on the VCU118 development board. The provided Makefile is designed to automate various tasks including setting up the environment and running OpenOCD and GDB for debugging.

## Requirements

- `openocd`: OpenOCD should be installed and accessible via the command line.
- `riscv64-unknown-elf-gdb`: GDB for RISC-V.

## Variables

The Makefile uses several variables that can be customized:

| **Variable**                 | **Default Value**                      |
|------------------------------|----------------------------------------|
| OPENOCD                      | sudo $(shell which openocd)            |
| GDB                          | riscv64-unknown-elf-gdb                |
| ADAPTER_SPEED                | 1000                                   |
| INTERFACE                    | olimex-arm-usb-ocd-h                   |
| BOARD                        | vcu-118                                |
| TARGET                       | smp                                    |
| INITIAL_PC                   | Entry point of $(PAYLOAD)              |
| MEM_BASE_ADDR                | 0x80000000                             |
| NUM_HARTS                    | 2                                      |
| TARGET_FREQ                  | 50000000 (Hz)                          |
| OPENOCD_DIR                  | openocd                                |

## Targets

- **openocd**: Runs OpenOCD with the specified configuration to set up a GDB server.

  ```sh
  make openocd
  ```

- **gdb**: Runs GDB and connects to the OpenOCD server.

  ```sh
  make gdb
  ```

- **gdb-load-payload**: Loads the payload into GDB and sets the program counter for each hart.

  ```sh
  make gdb-load-payload
  ```
  
- **gdb-load-payload-and-run**: Loads the payload into GDB and sets the program counter for each hart, then continues execution.

  ```sh
  make gdb-load-payload
  ```
