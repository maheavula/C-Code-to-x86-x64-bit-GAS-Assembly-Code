# For loop practice program

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i;` | | Declare integer `i` |
| `    for (i = 0; i <= 10; i = i + 2) {` | `    mov     DWORD PTR [rbp-4], 0` | Initialize `i` to 0 |
| | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop body label |
| `        printf("%d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move value of `i` to `eax` |
| | `    mov     esi, eax` | Move value of `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    }` | `    add     DWORD PTR [rbp-4], 2` | Increment `i` by 2 |
| | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 10` | Compare `i` with 10 |
| | `    jle     .L3` | Jump to `.L3` if `i` <= 10 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
