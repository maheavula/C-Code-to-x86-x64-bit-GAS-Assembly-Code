# If condition statement program

### Things learnt
  - As this is just if condition, actuall C code condition is true, but in ASM code it written as opposite to condition to print statement condition as false.

---


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int x = 20;` | `    mov     DWORD PTR [rbp-4], 20` | Store 20 in `x` (at `rbp-4`) |
| `    int y = 18;` | `    mov     DWORD PTR [rbp-8], 18` | Store 18 in `y` (at `rbp-8`) |
| `    if (x < y) {` | `    mov     eax, DWORD PTR [rbp-4]` | Move the value of `x` into `eax` |
| | `    cmp     eax, DWORD PTR [rbp-8]` | Compare `x` with `y` |
| | `    jge     .L2` | Jump to `.L2` if `x >= y` (condition false) |
| `        printf("x is greater than y");` | `    mov     edi, OFFSET FLAT:.LC0` | Load the address of the format string |
| | `    mov     eax, 0` | Clear `eax` before the function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L2:` | Label for the code following the if block |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
