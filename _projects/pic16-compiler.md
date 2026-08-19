---
title: "pic16cc"
priority: 3
date: 2026-08-15
excerpt: "Experimental compiler written in Rust that transforms a subset of C into Intel HEX firmware and includes a CPU simulator."
status: "Experimental · In development"
role: "Architecture, development, testing, and documentation"
category: "Compilers and embedded systems"
code: "C→HEX"
stack:
  - Rust
  - C
  - PIC16
  - Intel HEX
  - Testing
repo_url: "https://github.com/esettes/PIC16_compiler"
demo_url: ""
cover: "/assets/images/projects/pic16cc.png"
---
## The problem

PIC16 microcontrollers operate with very limited resources and usually depend on specific
toolchains. This project explores how to build an understandable compilation pipeline from
end to end, from C source code to a file ready for programming.

## The solution

`pic16cc` compiles a subset of C directly to Intel HEX without requiring an external
assembler. The repository includes two tools:

- `picc`, which parses, optimizes, and generates the firmware.
- `pic16-sim`, a simulator that runs and verifies the result without hardware.

The complete flow is:

```text
C source -> frontend -> optimization -> machine code -> firmware.hex
                                                     -> PIC16 simulator
```

## Technical decisions

- A staged architecture so each phase can be tested independently.
- Additional symbol maps and instruction listings.
- Configurable profiles that balance code size and functionality.
- Final HEX file validation before accepting it as correct output.
- Explicit documentation of the supported C subset limitations.

## Current result

The compiler supports two PIC16 devices, integer types, structures, arrays, interrupts,
and a limited set of floating-point operations. It remains experimental and is not intended
to replace a production toolchain.

This project demonstrates compiler design, systems architecture, testing, and work close
to the hardware without hiding its current limitations.
