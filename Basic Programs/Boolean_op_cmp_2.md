# This is not limited to only compare numbers. This can also compare boolean variables
### Things Learnt
  - after `cmp   al, BYTE PTR [rbp-2]` instruction, `sete` is used to set the al = 0 or al = 1 if both variables are equal
  - To comp to variables no need to move 2 addresses into 2 different register, we can move one address of value into `eax` reg then `eax` is compared with another values of address like
  - `movzx   eax, BYTE PTR [rbp-1]`
  - `cmp     eax, BYTE PTR [rbp-2]`
---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `#include <stdbool.h>` | | Include the boolean header file |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    bool isHamburgerTasty = true;` | `    mov     BYTE PTR [rbp-1], 1` | Set `isHamburgerTasty` to true (1) |
| `    bool isPizzaTasty = true;` | `    mov     BYTE PTR [rbp-2], 1` | Set `isPizzaTasty` to true (1) |
| `    printf("%d", isHamburgerTasty == isPizzaTasty);` | `    movzx   eax, BYTE PTR [rbp-1]` | Load `isHamburgerTasty` into `eax` |
| | `    cmp     eax, BYTE PTR [rbp-2]` | Compare `isHamburgerTasty` with `isPizzaTasty` |
| | `    sete    al` | Set `al` to 1 if they are equal, otherwise 0 |
| | `    movzx   eax, al` | Zero-extend `al` to `eax` |
| | `    mov     esi, eax` | Move comparison result to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
