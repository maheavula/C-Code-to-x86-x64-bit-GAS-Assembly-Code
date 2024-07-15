# A function can be called multiple times


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `void myFunction() {` | `myFunction:` | Function entry point for `myFunction` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `  printf("I just got executed!\n");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of the format string into `edi` |
| | `    call    puts` | Call `puts` to print the message |
| `}` | `    nop` | No operation (placeholder) |
| | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `myFunction` |
| `int main() {` | `main:` | Function entry point for `main` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `  myFunction();` | `    call    myFunction` | Call `myFunction` |
| `  myFunction();` | `    call    myFunction` | Call `myFunction` again |
| `  myFunction();` | `    call    myFunction` | Call `myFunction` a third time |
| `  return 0;` | `    mov     eax, 0` | Return 0 from `main` |
| `}` | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `main` |
| | `.LC0:` | |
| | `.string "I just got executed!"` | String literal for `puts` |
