# Arthmetic operations with 2 values

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int num1, num2;` | | Local variables `num1` and `num2` |
| `    printf("Enter two integers: ");` | `    mov     edi, OFFSET FLAT:.LC0` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    scanf("%d %d", &num1, &num2);` | `    lea     rdx, [rbp-8]` | Load address of `num2` |
| | `    lea     rax, [rbp-4]` | Load address of `num1` |
| | `    mov     rsi, rax` | Move address of `num1` to `rsi` |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    __isoc99_scanf` | Call `scanf` function |
| `    printf("Addition: %d + %d = %d\n", num1, num2, num1 + num2);` | `    mov     edx, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     eax, DWORD PTR [rbp-8]` | Load `num2` |
| | `    lea     ecx, [rdx+rax]` | Calculate `num1 + num2` |
| | `    mov     edx, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, eax` | Move `num1` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC2` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("Subtraction: %d - %d = %d\n", num1, num2, num1 - num2);` | `    mov     edx, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     eax, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     ecx, edx` | Move `num1` to `ecx` |
| | `    sub     ecx, eax` | Calculate `num1 - num2` |
| | `    mov     edx, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, eax` | Move `num1` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC3` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("Multiplication: %d * %d = %d\n", num1, num2, num1 * num2);` | `    mov     edx, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     eax, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     ecx, edx` | Move `num1` to `ecx` |
| | `    imul    ecx, eax` | Calculate `num1 * num2` |
| | `    mov     edx, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, eax` | Move `num1` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC4` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("Division: %d / %d = %d\n", num1, num2, num1 / num2);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, DWORD PTR [rbp-8]` | Load `num2` |
| | `    cdq` | Sign extend `eax` to `edx:eax` |
| | `    idiv    esi` | Divide `edx:eax` by `esi` |
| | `    mov     ecx, eax` | Move quotient to `ecx` |
| | `    mov     edx, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, eax` | Move `num1` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC5` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    printf("Modulus: %d %% %d = %d\n", num1, num2, num1 % num2);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     edi, DWORD PTR [rbp-8]` | Load `num2` |
| | `    cdq` | Sign extend `eax` to `edx:eax` |
| | `    idiv    edi` | Divide `edx:eax` by `edi` |
| | `    mov     ecx, edx` | Move remainder to `ecx` |
| | `    mov     edx, DWORD PTR [rbp-8]` | Load `num2` |
| | `    mov     eax, DWORD PTR [rbp-4]` | Load `num1` |
| | `    mov     esi, eax` | Move `num1` to `esi` |
| | `    mov     edi, OFFSET FLAT:.LC6` | Load format string |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
