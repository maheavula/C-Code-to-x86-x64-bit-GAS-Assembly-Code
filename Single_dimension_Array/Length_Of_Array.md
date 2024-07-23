# To find the array length 

### Things learnt 
  - In this ASM code also there are no such functions so direclty assigned answer eax register to esi.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack for array and length variable |
| `    int myNumbers[] = {10, 25, 50, 75, 100};` | `    mov     DWORD PTR [rbp-32], 10` | Store 10 in the first element of the array |
| | `    mov     DWORD PTR [rbp-28], 25` | Store 25 in the second element of the array |
| | `    mov     DWORD PTR [rbp-24], 50` | Store 50 in the third element of the array |
| | `    mov     DWORD PTR [rbp-20], 75` | Store 75 in the fourth element of the array |
| | `    mov     DWORD PTR [rbp-16], 100` | Store 100 in the fifth element of the array |
| `    int length = sizeof(myNumbers) / sizeof(myNumbers[0]);` | `    mov     DWORD PTR [rbp-4], 5` | Calculate length of the array (5 elements) and store it in length variable |
| `    printf("%d", length);` | `    mov     eax, DWORD PTR [rbp-4]` | Load length variable into `eax` |
| | `    mov     esi, eax` | Move length into `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
