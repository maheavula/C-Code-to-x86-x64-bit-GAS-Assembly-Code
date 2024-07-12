# For loop basic program 

### Things learnt
  - This is quite similar to While loop in syntax of ASM code but differ in C code, it is funny to learn Assembly language.
  - To find difference between While and For loop
  - `For Loop:` Initialization typically happens before the loop starts. This can be seen in the assembly code where the loop counter is set before the loop condition is checked.
  - `While Loop:` Initialization of the loop counter can also happen outside the loop but is often less structured compared to for loops.
  - `For Loop:` Typically has a clear initialization, condition check, and increment.
  - `While Loop:` The condition check is the primary feature, and increments or other changes to the loop variable are more flexible in placement.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i;` | | Declare integer `i` |
| `    for (i = 0; i < 5; i++) {` | `    mov     DWORD PTR [rbp-4], 0` | Initialize `i` to 0 |
| | `    jmp     .L2` | Jump to condition check |
| | `.L3:` | Label for loop body |
| `        printf("%d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move `i` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `    add     DWORD PTR [rbp-4], 1` | Increment `i` |
| | `.L2:` | Label for loop condition check |
| | `    cmp     DWORD PTR [rbp-4], 4` | Compare `i` with 4 |
| | `    jle     .L3` | Jump to `.L3` if `i` <= 4 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
