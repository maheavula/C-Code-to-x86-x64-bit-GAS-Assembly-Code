# Logical Not operator 

### Things learnt 
  - tommorrow.

---


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int x = 9;` | `    mov     DWORD PTR [rbp-4], 9` | Store 9 in `x` (at `rbp-4`) |
| `    int y = 3;` | `    mov     DWORD PTR [rbp-8], 3` | Store 3 in `y` (at `rbp-8`) |
| `    printf("%d", !(x > 3 && x < 10));` | `    cmp     DWORD PTR [rbp-4], 3` | Compare `x` with 3 |
| | `    jle     .L2` | Jump to `.L2` if `x` <= 3 |
| | `    cmp     DWORD PTR [rbp-4], 9` | Compare `x` with 9 |
| | `    jle     .L3` | Jump to `.L3` if `x` <= 9 |
| | `.L2:` | `.L2:` | Label for true condition |
| | `    mov     eax, 1` | Set `eax` to 1 (true) if condition is met |
| | `    jmp     .L4` | Jump to `.L4` |
| | `.L3:` | `.L3:` | Label for false condition |
| | `    mov     eax, 0` | Set `eax` to 0 (false) if condition is not met |
| | `.L4:` | `.L4:` | Label for end of comparison |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
