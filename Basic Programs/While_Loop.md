# While loop basic program

### Things learnt
  - We need to look at the loop position, where to jump and where to need to check condition of loop.
  - When i have written ASM code first but that is not correct at the while loop condition, later i got to know that condition should be at end of the program because it fails then it will exit otherwise that will iterate untill condtion fails.


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i = 0;` | `    mov     DWORD PTR [rbp-4], 0` | Store 0 in `i` (at `rbp-4`) |
| `    while (i < 5) {` | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop start label |
| `        printf("%d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move `i` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load address of format string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        i++;` | `    add     DWORD PTR [rbp-4], 1` | Increment `i` by 1 |
| `    }` | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 4` | Compare `i` with 5 |
| | `    jle     .L3` | Jump to loop start if `i` <= 4 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
