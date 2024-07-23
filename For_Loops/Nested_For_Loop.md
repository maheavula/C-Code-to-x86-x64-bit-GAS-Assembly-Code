# Nested loop basic program

### Things learnt
  - We need to analyse that whenever which conditon fails then it exists that loop condition should write at the end of program in ASM code.
  - Then we need to initialize the inner loop value at the end of outer loop printf function, beacuse everytime it enters to inner loop then it will intializes as initial value.
  - This ASM coding very crazy because it is making think like very different possible ways.
    

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int i, j;` | | Declare integers `i` and `j` |
| `    for (i = 1; i <= 2; ++i) {` | `    mov     DWORD PTR [rbp-4], 1` | Initialize `i` to 1 |
| | `    jmp     .L2` | Jump to outer loop condition check |
| | `.L5:` | Outer loop body label |
| `        printf("Outer: %d\n", i);` | `    mov     eax, DWORD PTR [rbp-4]` | Move `i` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        for (j = 1; j <= 3; ++j) {` | `    mov     DWORD PTR [rbp-8], 1` | Initialize `j` to 1 |
| | `    jmp     .L3` | Jump to inner loop condition check |
| | `.L4:` | Inner loop body label |
| `            printf(" Inner: %d\n", j);` | `    mov     eax, DWORD PTR [rbp-8]` | Move `j` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        }` | `    add     DWORD PTR [rbp-8], 1` | Increment `j` |
| | `.L3:` | Inner loop condition check label |
| | `    cmp     DWORD PTR [rbp-8], 3` | Compare `j` with 3 |
| | `    jle     .L4` | Jump to `.L4` if `j` <= 3 |
| `    }` | `    add     DWORD PTR [rbp-4], 1` | Increment `i` |
| | `.L2:` | Outer loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 2` | Compare `i` with 2 |
| | `    jle     .L5` | Jump to `.L5` if `i` <= 2 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
