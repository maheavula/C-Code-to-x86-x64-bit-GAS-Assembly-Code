# Basic function program

### Things learnt
  - We need to write the program from where function declartion has started with separate labeling like `MyFunction:`.
  - At the end of every function we need to `Restore base pointer of the caller` and `Return from myFunction`.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `void myFunction() {` | `myFunction:` | Function entry point for `myFunction` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `  printf("I just got executed!");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of the format string into `edi` |
| | `    mov     eax, 0` | Prepare for `printf` call |
| | `    call    printf` | Call `printf` to print the message |
| `}` | `    nop` | No operation (placeholder) |
| | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `myFunction` |
| `int main() {` | `main:` | Function entry point for `main` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `  myFunction();` | `    mov     eax, 0` | Prepare for `myFunction` call |
| | `    call    myFunction` | Call `myFunction` |
| `  return 0;` | `    mov     eax, 0` | Return 0 from `main` |
| `}` | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `main` |
| | `.LC0:` | |
| | `.string "I just got executed!"` | String literal for `printf` |
