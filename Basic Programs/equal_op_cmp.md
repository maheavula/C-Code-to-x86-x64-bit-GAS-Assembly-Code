# The equal to (==) operator to compare different values
### Things Learnt
  - No need to allocate space because values are directly compared at printf function arguments.
  - Copied answer into 'rsi' which is printf function argument.
---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `    printf("%d\n", 10 == 10);` | `    mov     esi, 1` | `10 == 10` is true, so move 1 to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d\n", 10 == 15);` | `    mov     esi, 0` | `10 == 15` is false, so move 0 to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", 5 == 55);` | `    mov     esi, 0` | `5 == 55` is false, so move 0 to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    pop     rbp` | Restore base pointer |
| | `    ret` | Return from function |
