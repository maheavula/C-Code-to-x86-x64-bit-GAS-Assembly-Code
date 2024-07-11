# Short hand if else (Terinary operator)

### Things learnt
  - If you compared with if else there is nothing much difference is there. Like just we compare and jump based on condition.
---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int time = 20;` | `    mov     DWORD PTR [rbp-4], 20` | Store 20 in `time` (at `rbp-4`) |
| `(time < 18) ? printf("Good day.") : printf("Good evening.");` | `    cmp     DWORD PTR [rbp-4], 17` | Compare `time` with 18 |
| | `    jg      .L2` | Jump to `.L2` if `time` > 18 (false condition) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Good day." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip false condition |
| | `.L2:` | `.L2:` | Label for false condition |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Good evening." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `.L3:` | `.L3:` | Label for end of comparison |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
