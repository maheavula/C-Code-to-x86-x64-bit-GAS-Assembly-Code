# If else conditions example problem solving

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int doorCode = 1337;` | `    mov     DWORD PTR [rbp-4], 1337` | Store 1337 in `doorCode` (at `rbp-4`) |
| `    if (doorCode == 1337) {` | `    cmp     DWORD PTR [rbp-4], 1337` | Compare `doorCode` with 1337 |
| | `    jne     .L2` | Jump to `.L2` if `doorCode` is not equal to 1337 (false condition) |
| `        printf("Correct code.\nThe door is now open.");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Correct code.\nThe door is now open." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip false condition |
| `    } else {` | `.L2:` | Label for false condition |
| `        printf("Wrong code.\nThe door remains closed.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Wrong code.\nThe door remains closed." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for end of comparison |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
