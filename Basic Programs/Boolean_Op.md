# Boolean opeartions

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | |
| `#include <stdbool.h>` | | Import the boolean header file |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    bool isProgrammingFun = true;` | `    mov     BYTE PTR [rbp-1], 1` | Set `isProgrammingFun` to true (1) |
| `    bool isFishTasty = false;` | `    mov     BYTE PTR [rbp-2], 0` | Set `isFishTasty` to false (0) |
| `    printf("%d\n", isProgrammingFun);` | `    movzx   eax, BYTE PTR [rbp-1]` | Load `isProgrammingFun` |
| | `    mov     esi, eax` | Move `isProgrammingFun` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", isFishTasty);` | `    movzx   eax, BYTE PTR [rbp-2]` | Load `isFishTasty` |
| | `    mov     esi, eax` | Move `isFishTasty` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
