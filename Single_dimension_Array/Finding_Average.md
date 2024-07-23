# To find the average of an array


### Things learnt
  - To change int to float use cvtsi2ss for single precision only `cvtsi2ss  xmm0, eax` | Convert `ages[i]` from int to float.
  - When doing arthmetic operation the operands should only be register like `add xmmo, xmm1`, should not contain address in any operand like `add DWORD PTR [rbp-4]`.
  - `cvtss2sd   xmm2, DWORD PTR [rbp-16]` | Convert `avg` from float to double

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 48` | Allocate 48 bytes on stack for array and variables |
| `    int ages[] = {20, 22, 18, 35, 48, 26, 87, 70};` | `    mov     DWORD PTR [rbp-48], 20` | Store 20 in the first element of the array |
| | `    mov     DWORD PTR [rbp-44], 22` | Store 22 in the second element of the array |
| | `    mov     DWORD PTR [rbp-40], 18` | Store 18 in the third element of the array |
| | `    mov     DWORD PTR [rbp-36], 35` | Store 35 in the fourth element of the array |
| | `    mov     DWORD PTR [rbp-32], 48` | Store 48 in the fifth element of the array |
| | `    mov     DWORD PTR [rbp-28], 26` | Store 26 in the sixth element of the array |
| | `    mov     DWORD PTR [rbp-24], 87` | Store 87 in the seventh element of the array |
| | `    mov     DWORD PTR [rbp-20], 70` | Store 70 in the eighth element of the array |
| `    float avg, sum = 0;` | `    pxor    xmm0, xmm0` | Clear xmm0 register (used for `sum`) |
| | `    movss   DWORD PTR [rbp-4], xmm0` | Initialize `sum` to 0 |
| `    int i;` | | Declare the loop counter variable |
| `    int length = sizeof(ages) / sizeof(ages[0]);` | `    mov     DWORD PTR [rbp-12], 8` | Calculate length of the array (8 elements) and store it in `length` variable |
| `    for (i = 0; i < length; i++) {` | `    mov     DWORD PTR [rbp-8], 0` | Initialize loop counter `i` to 0 |
| | `    jmp     .L2` | Jump to the loop condition check |
| | `.L3:` | Loop start label |
| `        sum += ages[i];` | `    mov     eax, DWORD PTR [rbp-8]` | Load loop counter `i` into `eax` |
| | `    cdqe` | Sign extend `eax` to `rax` |
| | `    mov     eax, DWORD PTR [rbp-48+rax*4]` | Load `ages[i]` into `eax` |
| | `    pxor    xmm0, xmm0` | Clear xmm0 register |
| | `    cvtsi2ss        xmm0, eax` | Convert `ages[i]` from int to float |
| | `    movss   xmm1, DWORD PTR [rbp-4]` | Load `sum` into xmm1 |
| | `    addss   xmm0, xmm1` | Add `ages[i]` to `sum` |
| | `    movss   DWORD PTR [rbp-4], xmm0` | Store updated `sum` |
| | `    add     DWORD PTR [rbp-8], 1` | Increment loop counter `i` |
| | `.L2:` | Loop condition check label |
| | `    mov     eax, DWORD PTR [rbp-8]` | Load loop counter `i` into `eax` |
| | `    cmp     eax, DWORD PTR [rbp-12]` | Compare `i` with `length` |
| | `    jl      .L3` | If `i < length`, jump to loop start |
| `    avg = sum / length;` | `    pxor    xmm1, xmm1` | Clear xmm1 register |
| | `    cvtsi2ss        xmm1, DWORD PTR [rbp-12]` | Convert `length` from int to float |
| | `    movss   xmm0, DWORD PTR [rbp-4]` | Load `sum` into xmm0 |
| | `    divss   xmm0, xmm1` | Divide `sum` by `length` to get `avg` |
| | `    movss   DWORD PTR [rbp-16], xmm0` | Store `avg` |
| `    printf("The average age is: %.2f", avg);` | `    pxor    xmm2, xmm2` | Clear xmm2 register |
| | `    cvtss2sd        xmm2, DWORD PTR [rbp-16]` | Convert `avg` from float to double |
| | `    movq    rax, xmm2` | Move `avg` to `rax` |
| | `    movq    xmm0, rax` | Move `rax` to xmm0 |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string address into `edi` |
| | `    mov     eax, 1` | Prepare for `printf` call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
