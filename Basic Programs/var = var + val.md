# The Arthmetic operators is often used to add together two values and the arthmetic operators is often used to together two values or more.

### Things learnt
  - `int sum2 = sum1 + 250;` while this is being moved, sum1 should first and then 250.
  - `mov     DWORD PTR [rbp-4], 150` here 100 + 150 is added before and after that directly included and moved to address
  - ` mov     eax, DWORD PTR [rbp-4]` here the 150 values address is moved to eax reg and 
  - `sub     eax, 250`  then sub operation has done
  - The above instructions repeated in overall program
  - and before call printf function `call printf`, we need to assign the result of operation in `eax` reg like `mov     eax, DWORD PTR [rbp-4]` for every operation.
---

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 32` | Allocate 32 bytes on stack |
| `    int sum1 = 100 + 50;` | `    mov     DWORD PTR [rbp-4], 150` | Store 150 in `sum1` (at `rbp-4`) |
| `    int sum2 = sum1 - 250;` | `    mov     eax, DWORD PTR [rbp-4]` | Load `sum1` into `eax` |
| | `    sub     eax, 250` | Subtract 250 from `eax` |
| | `    mov     DWORD PTR [rbp-8], eax` | Store result in `sum2` (at `rbp-8`) |
| `    int sum3 = sum2 + sum2;` | `    mov     eax, DWORD PTR [rbp-8]` | Load `sum2` into `eax` |
| | `    add     eax, eax` | Add `sum2` to `eax` |
| | `    mov     DWORD PTR [rbp-12], eax` | Store result in `sum3` (at `rbp-12`) |
| `    int sum4 = sum1 - sum2;` | `    mov     eax, DWORD PTR [rbp-4]` | Load `sum1` into `eax` |
| | `    sub     eax, DWORD PTR [rbp-8]` | Subtract `sum2` from `eax` |
| | `    mov     DWORD PTR [rbp-16], eax` | Store result in `sum4` (at `rbp-16`) |
| `    int sum5 = sum2 * sum4;` | `    mov     eax, DWORD PTR [rbp-8]` | Load `sum2` into `eax` |
| | `    imul    eax, DWORD PTR [rbp-16]` | Multiply `eax` by `sum4` |
| | `    mov     DWORD PTR [rbp-20], eax` | Store result in `sum5` (at `rbp-20`) |
| `    printf("%d\n", sum1);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `sum1` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d\n", sum2);` | `    mov     eax, DWORD PTR [rbp-8]` | Load `sum2` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("%d\n", sum3);` | `    mov     eax, DWORD PTR [rbp-12]` | Load `sum3` into `eax` |
| | `    mov     esi, eax` | Move `eax` to `esi` (second argument of `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
