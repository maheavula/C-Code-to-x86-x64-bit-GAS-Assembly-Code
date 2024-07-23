# IF ELSE conditon program

### Things learnt
  - As usual we need to write opposite condition in ASM code from C code.
  - And think wisely.
  - By practicing we get more clarity and knowledge.

---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int time = 20;` | `    mov     DWORD PTR [rbp-4], 20` | Store 20 in `time` (at `rbp-4`) |
| `    if (time < 18) {` | `    cmp     DWORD PTR [rbp-4], 17` | Compare `time` with 18 |
| | `    jg      .L2` | Jump to `.L2` if `time > 18` (condition false) |
| `        printf("Good day.");` | `    mov     edi, OFFSET FLAT:.LC0` | Load the address of the "Good day." string |
| | `    mov     eax, 0` | Clear `eax` before the function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip the else block |
| `    } else {` | `.L2:` | Label for the else block |
| `        printf("Good evening.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load the address of the "Good evening." string |
| | `    mov     eax, 0` | Clear `eax` before the function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for the code following the if-else block |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
