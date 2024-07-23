# Array program to access array values by using for loop

### Things learnt
  - It is similar to writing like for loop but here we need to increment the `i` value and need to access array value, at that time i stuck, for that...
  - The i value should move to eax, then we need to extend the eax to rax(64bit). `mov eax, DWORD PTR [rbp-32+rax*4]:` Calculate the address of the array element A[i] using [rbp-32 + rax*4], and move the value into eax. For i = 0, this is [rbp-32 + 0*4] = [rbp-32] = 25.
  - After calculating the address of arrat element store in eax, to move into function argument `mov esi, eax`.
    

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack for array and loop counter |
| `    int myNumbers[] = {25, 50, 75, 100};` | `    mov     DWORD PTR [rbp-32], 25` | Store 25 in the first element of the array |
| | `    mov     DWORD PTR [rbp-28], 50` | Store 50 in the second element of the array |
| | `    mov     DWORD PTR [rbp-24], 75` | Store 75 in the third element of the array |
| | `    mov     DWORD PTR [rbp-20], 100` | Store 100 in the fourth element of the array |
| `    int i;` | | Declare loop counter `i` |
| `    for (i = 0; i < 4; i++) {` | `    mov     DWORD PTR [rbp-4], 0` | Initialize loop counter to 0 |
| | `    jmp     .L2` | Jump to loop condition check |
| | `.L3:` | Loop start label |
| `        printf("%d\n", myNumbers[i]);` | `    mov     eax, DWORD PTR [rbp-4]` | Move loop counter to `eax` |
| | `    cdqe` | Sign extend `eax` to `rax` |
| | `    mov     eax, DWORD PTR [rbp-32+rax*4]` | Move `myNumbers[i]` to `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `printf`) |
| | `    mov     eax, 0` | Clear `eax` before calling `printf` |
| | `    call    printf` | Call `printf` function |
| `    }` | `    add     DWORD PTR [rbp-4], 1` | Increment loop counter |
| | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 3` | Compare loop counter with 3 |
| | `    jle     .L3` | If loop counter <= 3, jump to loop start |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |

---

![array_for_loop](https://github.com/user-attachments/assets/35cfa89e-c07d-4ffe-8785-6c6cf10230c3)
