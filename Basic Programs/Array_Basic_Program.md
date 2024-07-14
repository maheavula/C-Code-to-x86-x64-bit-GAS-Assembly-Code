# Array basic program

### Things learnt
  - The ASM code for array intialization is like moving the values into different variables. In this program array values are assigned after declaring the array variable.
  - If you want to initialize the array values while declaration it is quite similar to this program. ` int myNumbers[] = {25, 50, 75, 100};`
  - **To identify if the program has array like data structures**
      - **Sequential Memory Accesses:** Array elements are usually stored in consecutive memory locations. Assembly code that accesses memory locations with a consistent offset pattern often indicates an array.
      - **Loading and Storing Values:** Instructions that load values from and store values to memory locations in a repetitive or indexed manner.
      - **Use of Indexing:** Look for the use of index registers or explicit indexing in memory access instructions.
      - **Looping Constructs:** Array manipulation often involves looping constructs to iterate over the array elements.


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack for the array |
| `    int myNumbers[4];` | | Declare an array of four integers |
| `    myNumbers[0] = 25;` | `    mov     DWORD PTR [rbp-16], 25` | Store 25 in the first element of the array |
| `    myNumbers[1] = 50;` | `    mov     DWORD PTR [rbp-12], 50` | Store 50 in the second element of the array |
| `    myNumbers[2] = 75;` | `    mov     DWORD PTR [rbp-8], 75` | Store 75 in the third element of the array |
| `    myNumbers[3] = 100;` | `    mov     DWORD PTR [rbp-4], 100` | Store 100 in the fourth element of the array |
| `    printf("%d\n", myNumbers[0]);` | `    mov     eax, DWORD PTR [rbp-16]` | Move the first element of the array into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
