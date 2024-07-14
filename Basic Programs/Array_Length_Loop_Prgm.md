# Array program to accessing the array values using length of array.


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack for array and variables |
| `    int myNumbers[] = {25, 50, 75, 100};` | `    mov     DWORD PTR [rbp-32], 25` | Store 25 in the first element of the array |
| | `    mov     DWORD PTR [rbp-28], 50` | Store 50 in the second element of the array |
| | `    mov     DWORD PTR [rbp-24], 75` | Store 75 in the third element of the array |
| | `    mov     DWORD PTR [rbp-20], 100` | Store 100 in the fourth element of the array |
| `    int length = sizeof(myNumbers) / sizeof(myNumbers[0]);` | `    mov     DWORD PTR [rbp-8], 4` | Calculate length of the array (4 elements) and store it in length variable |
| `    int i;` | | Declare the loop counter variable |
| `    for (i = 0; i < length; i++) {` | `    mov     DWORD PTR [rbp-4], 0` | Initialize loop counter `i` to 0 |
| | `    jmp     .L2` | Jump to the loop condition check |
| | `.L3:` | Loop start label |
| `        printf("%d\n", myNumbers[i]);` | `    mov     eax, DWORD PTR [rbp-4]` | Load loop counter `i` into `eax` |
| | `    cdqe` | Sign extend `eax` to `rax` |
| | `    mov     eax, DWORD PTR [rbp-32+rax*4]` | Load `myNumbers[i]` into `eax` |
| | `    mov     esi, eax` | Move `myNumbers[i]` into `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    }` | `    add     DWORD PTR [rbp-4], 1` | Increment loop counter `i` |
| | `.L2:` | Loop condition check label |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load loop counter `i` into `eax` |
| | `    cmp     eax, DWORD PTR [rbp-8]` | Compare `i` with `length` |
| | `    jl      .L3` | If `i < length`, jump to loop start |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
