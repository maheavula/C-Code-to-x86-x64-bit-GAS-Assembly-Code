# For loop practice problem

### Things learnt

  - `sal   DWORD PTR [rbp-4]`  Shift `i` left by 1 bit (multiply by 2)
  - In the place of increment section of for loop, when it is multiplying, we can aslo use `SAL` instruction when it shifts to right by 1bit, the true bit(0000 00`1`0) shifts to left then it will be like (0000 0`1`00)
 = 4. By default it will shift by 1 so they did not mention the number. if it multiplied by 4 then i will be mentioned like `sal DWORD PTR [rbp-4], 2`, here 2 is 2bits means multiplied 2^2 = 4.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i;` | | Declare integer `i` |
| `    for (i = 2; i <= 512; i *= 2) {` | `    mov     DWORD PTR [rbp-4], 2` | Initialize `i` to 2 |
| | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop body label |
| `        printf("%d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move value of `i` to `eax` |
| | `    mov     esi, eax` | Move value of `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    }` | `    sal     DWORD PTR [rbp-4]` | Shift `i` left by 1 bit (multiply by 2) |
| | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 512` | Compare `i` with 512 |
| | `    jle     .L3` | Jump to `.L3` if `i` <= 512 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
