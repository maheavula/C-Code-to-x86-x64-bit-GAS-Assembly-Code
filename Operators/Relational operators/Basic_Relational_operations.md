
# What are changes to be made in basic relational operations between 2 variables, changes can happen in asm code when variables are more.
### Things learnt
  - Based on the relational operation just we need to change mnemonics. Just like
  - `sete    al`
  - `setge (>=)`
  - `setle (<=)`
  - `setne (!=)`
  - `sete (==)`
  - `setl`
  - `setg`
---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int myAge = 25;` | `    mov     DWORD PTR [rbp-4], 25` | Store 25 in `myAge` (at `rbp-4`) |
| `    int votingAge = 18;` | `    mov     DWORD PTR [rbp-8], 18` | Store 18 in `votingAge` (at `rbp-8`) |
| `    printf("%d", myAge == votingAge);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `myAge` into `eax` |
| | `    cmp     eax, DWORD PTR [rbp-8]` | Compare `myAge` with `votingAge` |
| | `    sete    al` | Set `al` to 1 if `myAge == votingAge`, otherwise 0 |
| | `    movzx   eax, al` | Zero-extend `al` to `eax` |
| | `    mov     esi, eax` | Move comparison result to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
