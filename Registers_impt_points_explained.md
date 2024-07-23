# Overview of Assembly Registers

## Introduction

The goal of a compiler is to translate high-level code into Assembly, a language the CPU understands. This involves using various instructions for data manipulation, comparisons, value modifications, and more.

## Registers and Memory

- **Registers vs. Memory**:
  - Registers are faster than memory (RAM) for CPU operations, so CPUs prioritize using registers whenever possible.

## Key Registers

### RIP Register

- **RIP** (Instruction Pointer):
  - Address of the next instruction to be executed.
  - Read-only in nature.

### General Purpose Registers

- **RAX**:
  - 64-bit register.
  - **EAX**: Lower 32 bits of RAX.
  - **AX**: Lower 16 bits of RAX.
  - **AH**: Upper 8 bits of AX.
  - **AL**: Lower 8 bits of AX.
  - Example: If RAX = 0x0123456789ABCDEF,
    - RAX = 0x0123456789ABCDEF
    - EAX = 0x89ABCDEF
    - AX = 0xCDEF
    - AH = 0xCD
    - AL = 0xEF

- **Difference between "E" and "R"**:
  - "E" stands for extended, indicating 32-bit registers.
  - "R" denotes the full 64-bit register. In x32 assembly, you'll use EAX instead of RAX.

### Floating Point Registers

- **YMM0 to YMM15**:
  - 64-bit wide registers.
  - Capable of holding 4 values of 64-bit or 8 values of 32-bit.

- **XMM0 to XMM15**:
  - 32-bit wide registers.
  - Can hold 2 values of 64-bit or 4 values of 32-bit.

- **Array-like Behavior**:
  - These registers can be treated as arrays, enabling storage and manipulation of multiple values simultaneously.
  -  For example, YMM# registers are 256-bit wide each and can hold 4 64-bit values or 8 32-bit values. Similarly, XMM# are 128-bit wide each and can hold 2 64-bit values or 4 32-bit values.

### Integer Registers

- **R8 to R15**:
  - Designed for integer values.
  - Various access sizes:
    - **R8**: Full 64-bit (8 bytes).
    - **R8D**: Lower double word (4 bytes).
    - **R8W**: Lower word (2 bytes).
    - **R8B**: Lower byte (1 byte).
