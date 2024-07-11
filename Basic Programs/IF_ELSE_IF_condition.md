# If else if conditional program.

### Things learnt
  -  In this conditional statement the differece is another condition is verified when first condition is failed.
  -  I got to know that when in C code condition failed then in ASM code should do opposite because the statement block should not be printed. That should go to next condition right.

---
| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int time = 22;` | `    mov     DWORD PTR [rbp-4], 22` | Store 22 in `time` (at `rbp-4`) |
| `    if (time < 10) {` | `    cmp     DWORD PTR [rbp-4], 9` | Compare `time` with 10 |
| | `    jg      .L2` | Jump to `.L2` if `time` >= 10 |
| `        printf("Good morning.");` | `    mov     edi, OFFSET FLAT:.LC0` | Load format string "Good morning." |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip other conditions |
| `    } else if (time < 20) {` | `.L2:` | Label for `else if` condition |
| | `    cmp     DWORD PTR [rbp-4], 19` | Compare `time` with 20 |
| | `    jg      .L4` | Jump to `.L4` if `time` >= 20 |
| `        printf("Good day.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load format string "Good day." |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip remaining conditions |
| `    } else {` | `.L4:` | Label for `else` condition |
| `        printf("Good evening.");` | `    mov     edi, OFFSET FLAT:.LC2` | Load format string "Good evening." |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for end of conditions |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
