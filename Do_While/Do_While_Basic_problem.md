# Do while loop basic problem

### Things learn
  - Initinally i decided to write this ASM code myself, while writing i failed at beginning later after thinking deeply about Do while loop i just realized to print first value wether condition is true or not.
  - After initializing then i wrote code for the printing first value then i tried to increment with value 1 then checked for condition. Thats all it will print untill condition gets fail.



| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i = 0;` | `    mov     DWORD PTR [rbp-4], 0` | Store 0 in `i` (at `rbp-4`) |
| `    do {` | `.L2:` | Loop start label |
| `        printf("%d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move `i` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load address of format string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        i++;` | `    add     DWORD PTR [rbp-4], 1` | Increment `i` by 1 |
| `    } while (i < 5);` | `    cmp     DWORD PTR [rbp-4], 4` | Compare `i` with 5 |
| | `    jle     .L2` | Jump to loop start if `i` <= 4 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
