# Copmaring two variables after initializing at printf function argument
### Things Leant
  - How does x > y compared directly in printf function
      - `cmp     eax, DWORD PTR [rbp-8]`
      - `setg` is used to set the `al = 1` if 1st variable is greater than 2nd variable or otherwise `al = 0`
      -  `mov     esi, eax` is second argument of printf function. which is answer of x > y.
      -  `mov     edi, OFFSET FLAT:.LC0` is first arument moved into stack of printf function. which is string `%d`.
---
  
| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int x = 10;` | `    mov     DWORD PTR [rbp-4], 10` | Store 10 in `x` (at `rbp-4`) |
| `    int y = 9;` | `    mov     DWORD PTR [rbp-8], 9` | Store 9 in `y` (at `rbp-8`) |
| `    printf("%d", x > y);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `x` into `eax` |
| | `    cmp     eax, DWORD PTR [rbp-8]` | Compare `x` with `y` |
| | `    setg    al` | Set `al` to 1 if `x > y`, otherwise 0 |
| | `    movzx   eax, al` | Zero-extend `al` to `eax` |
| | `    mov     esi, eax` | Move comparison result to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
