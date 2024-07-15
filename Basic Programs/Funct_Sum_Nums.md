# Calculating the Sum of Numbers

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `void calculateSum() {` | `calculateSum:` | Function entry point for `calculateSum` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on the stack for local variables |
| `  int x = 5;` | `    mov     DWORD PTR [rbp-4], 5` | Store the value 5 in local variable `x` at `[rbp-4]` |
| `  int y = 10;` | `    mov     DWORD PTR [rbp-8], 10` | Store the value 10 in local variable `y` at `[rbp-8]` |
| `  int sum = x + y;` | `    mov     edx, DWORD PTR [rbp-4]` | Move the value of `x` into `edx` |
| | `    mov     eax, DWORD PTR [rbp-8]` | Move the value of `y` into `eax` |
| | `    add     eax, edx` | Add `edx` (x) and `eax` (y), result in `eax` |
| | `    mov     DWORD PTR [rbp-12], eax` | Store the result in local variable `sum` at `[rbp-12]` |
| `  printf("The sum of x + y is: %d", sum);` | `    mov     eax, DWORD PTR [rbp-12]` | Move the value of `sum` into `eax` |
| | `    mov     esi, eax` | Move `eax` into `esi` (second argument to `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Move the address of the format string into `edi` (first argument to `printf`) |
| | `    mov     eax, 0` | Prepare for `printf` call |
| | `    call    printf` | Call `printf` to print the message |
| `}` | `    nop` | No operation (placeholder) |
| | `    leave` | Restore stack pointer and base pointer of the caller |
| | `    ret` | Return from `calculateSum` |
| `int main() {` | `main:` | Function entry point for `main` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| `  calculateSum();` | `    call    calculateSum` | Call `calculateSum` |
| `  return 0;` | `    mov     eax, 0` | Return 0 from `main` |
| `}` | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `main` |
| | `.LC0:` | |
| | `.string "The sum of x + y is: %d"` | String literal for `printf` |
