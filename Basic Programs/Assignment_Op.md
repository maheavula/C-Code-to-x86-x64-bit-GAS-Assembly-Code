# Basic assignment operations with some variables.

### Things learnt
  - to assign something like `x += 10` it is just like adding value to the address of x. `add     DWORD PTR [rbp-4], 5`
  - `sar     DWORD PTR [rbp-20], 2` shift arthmetic right operation
  - each intializing value is 4bytes like `sub 16` so when 4 values exeeds `sub rsp, 32` need to write in asm code, include rsp when it is 32 bytes.

---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack |
| `    int x = 10;` | `    mov     DWORD PTR [rbp-4], 10` | Store 10 in `x` (at `rbp-4`) |
| `    int y = 20;` | `    mov     DWORD PTR [rbp-8], 20` | Store 20 in `y` (at `rbp-8`) |
| `    int z = 5;` | `    mov     DWORD PTR [rbp-12], 5` | Store 5 in `z` (at `rbp-12`) |
| `    int a = 6;` | `    mov     DWORD PTR [rbp-16], 6` | Store 6 in `a` (at `rbp-16`) |
| `    int b = 7;` | `    mov     DWORD PTR [rbp-20], 7` | Store 7 in `b` (at `rbp-20`) |
| `    x += 5;` | `    add     DWORD PTR [rbp-4], 5` | Add 5 to `x` |
| `    y *= x;` | `    mov     eax, DWORD PTR [rbp-8]` | Load `y` into `eax` |
| | `    imul    eax, DWORD PTR [rbp-4]` | Multiply `eax` by `x` |
| | `    mov     DWORD PTR [rbp-8], eax` | Store result back in `y` |
| `    z &= 5;` | `    and     DWORD PTR [rbp-12], 5` | Bitwise AND `z` with 5 |
| `    a ^= 7;` | `    xor     DWORD PTR [rbp-16], 7` | Bitwise XOR `a` with 7 |
| `    b >>= 2;` | `    sar     DWORD PTR [rbp-20], 2` | Arithmetic right shift `b` by 2 |
| `    printf("%d", x);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `x` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", y);` | `    mov     eax, DWORD PTR [rbp-8]` | Load `y` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", z);` | `    mov     eax, DWORD PTR [rbp-12]` | Load `z` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", a);` | `    mov     eax, DWORD PTR [rbp-16]` | Load `a` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d", b);` | `    mov     eax, DWORD PTR [rbp-20]` | Load `b` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
