# For loop practice problem 

### Things learnt
  - I wrote everything correct initially, but it went wrong where multipling and moving arguments to function.
  - First we need to multiple the because we are following `FASCALL` function call conventions so we move from last to first arguments in stack.
  - `imul    eax, DWORD PTR [rbp-4]` -> Temporarily holds various values throughout the loop, such as 2, the product, and the intermediate results.
  - `mov     ecx, eax`   Holds the product of the multiplication.
  - `mov     edx, DWORD PTR [rbp-4]`  Holds the current multiplier(i)
  - `mov     eax, DWORD PTR [rbp-8]`  2
  -  `mov     esi, eax`  Holds the constant multiplier (2) for printf. first argument after foramt string.
  -  `mov edi, OFFSET FLAT:.LC0` Holds the address of the format string for printf.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int number = 2;` | `    mov     DWORD PTR [rbp-8], 2` | Initialize `number` to 2 |
| `    int i;` | | Declare integer `i` |
| `    for (i = 1; i <= 10; i++) {` | `    mov     DWORD PTR [rbp-4], 1` | Initialize `i` to 1 |
| | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop body label |
| `        printf("%d x %d = %d\n", number, i, number * i);` | `    mov     eax, DWORD PTR [rbp-8]` | Move value of `number` to `eax` |
| | `    imul    eax, DWORD PTR [rbp-4]` | Multiply `eax` by `i` |
| | `    mov     ecx, eax` | Move result to `ecx` |
| | `    mov     edx, DWORD PTR [rbp-4]` | Move value of `i` to `edx` |
| | `    mov     eax, DWORD PTR [rbp-8]` | Move value of `number` to `eax` |
| | `    mov     esi, eax` | Move value of `eax` to `esi` (third argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    }` | `    add     DWORD PTR [rbp-4], 1` | Increment `i` by 1 |
| | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 10` | Compare `i` with 10 |
| | `    jle     .L3` | Jump to `.L3` if `i` <= 10 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |

---
![for loop tables](https://github.com/user-attachments/assets/007a8626-e599-4d56-8a28-2f7e3f88b72f)


