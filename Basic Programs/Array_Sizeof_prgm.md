# Array program to find sizeof of array

### Things learnt
  - There is no function is there to find size of array in assembly so direclty written the size of the array based on how many values are there in array
  - There are 5 values so generally integer size is 4bytes so 5 integers are in array then 5 * 4 = 20.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack for array and loop counter |
| `    int myNumbers[] = {10, 25, 50, 75, 100};` | `    mov     DWORD PTR [rbp-32], 10` | Store 10 in the first element of the array |
| | `    mov     DWORD PTR [rbp-28], 25` | Store 25 in the second element of the array |
| | `    mov     DWORD PTR [rbp-24], 50` | Store 50 in the third element of the array |
| | `    mov     DWORD PTR [rbp-20], 75` | Store 75 in the fourth element of the array |
| | `    mov     DWORD PTR [rbp-16], 100` | Store 100 in the fifth element of the array |
| `    printf("%lu", sizeof(myNumbers));` | `    mov     esi, 20` | Move the size of the array (20 bytes) into `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
