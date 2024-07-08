# Basic logical OR operation program

### Things learnt
  - while writing asm code from c code, after analysing answer from the c code we need to write according to the opposite conditions form of c, here it is like `x > 3` - `jle     .L2` and `x < 10` - `jle     .L3`.
  - As we knew that if first condition is true in `logical OR` conditon then no need to check other condition directly we can say answer is `1`.
  - And aslo for `logicaly AND` operation, we need to check both but if first condition fails to be true then directly the answer is `0`.


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int x = 9;` | `    mov     DWORD PTR [rbp-4], 9` | Store 9 in `x` (at `rbp-4`) |
| `    int y = 3;` | `    mov     DWORD PTR [rbp-8], 3` | Store 3 in `y` (at `rbp-8`) |
| `    printf("%d", (x < 3 || x < 10));` | `    cmp     DWORD PTR [rbp-4], 2` | Compare `x` with 3 |
| | `    jle     .L2` | Jump to `.L2` if `x` <= 3 |
| | `    cmp     DWORD PTR [rbp-4], 9` | Compare `x` with 9 |
| | `    jg      .L3` | Jump to `.L3` if `x` > 9 |
| | `.L2:` | `.L2:` | Label for true condition |
| | `    mov     eax, 1` | Set `eax` to 1 (true) if either condition is met |
| | `    jmp     .L4` | Jump to `.L4` |
| | `.L3:` | `.L3:` | Label for false condition |
| | `    mov     eax, 0` | Set `eax` to 0 (false) if neither condition is met |
| | `.L4:` | `.L4:` | Label for end of comparison |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
