# While loop program to print countown and printing string

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int countdown = 3;` | `    mov     DWORD PTR [rbp-4], 3` | Initialize `countdown` to 3 |
| `    while (countdown > 0) {` | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop body label |
| `        printf("%d\n", countdown);` | `    mov     eax, DWORD PTR [rbp-4]` | Move `countdown` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        countdown--;` | `    sub     DWORD PTR [rbp-4], 1` | Decrement `countdown` |
| `    }` | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 0` | Compare `countdown` with 0 |
| | `    jg      .L3` | Jump to `.L3` if `countdown` > 0 |
| `    printf("Happy New Year!!\n");` | `    mov     edi, OFFSET FLAT:.LC1` | Load format string address into `edi` (first argument of `puts`) |
| | `    call    puts` | Call `puts` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
