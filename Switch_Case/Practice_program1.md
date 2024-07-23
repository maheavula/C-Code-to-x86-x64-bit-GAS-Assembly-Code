# Switch Case Condition Practice Problem

### Things learnt 
  - Just compared directly without working with addresses.
    

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int day = 4;` | `    mov     DWORD PTR [rbp-4], 4` | Store 4 in `day` (at `rbp-4`) |
| `    switch (day) {` | `    cmp     DWORD PTR [rbp-4], 6` | Compare `day` with 6 |
| `    case 6:` | `    je      .L2` | Jump to `.L2` if `day` == 6 |
| `        printf("Today is Saturday");` | `.L2:` | Label for case 6 |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Today is Saturday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L5` | Jump to end of switch |
| `    case 7:` | `    cmp     DWORD PTR [rbp-4], 7` | Compare `day` with 7 |
| | `    je      .L3` | Jump to `.L3` if `day` == 7 |
| `        printf("Today is Sunday");` | `.L3:` | Label for case 7 |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Today is Sunday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L5` | Jump to end of switch |
| `    default:` | `    jmp     .L7` | Jump to default case |
| `        printf("Looking forward to the Weekend");` | `.L7:` | Label for default case |
| | `    mov     edi, OFFSET FLAT:.LC2` | Load address of "Looking forward to the Weekend" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L5:` | Label for end of switch |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
