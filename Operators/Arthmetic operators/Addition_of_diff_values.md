
## Addition of different data types values

| C Code                                | Assembly Code                                           | Comments                            |
|---------------------------------------|---------------------------------------------------------|-------------------------------------|
| ```c                                   | ```asm                                                   | Explanation                         |
| #include <stdio.h>                     | .LC2:                                                   | Label for string constant           |
| int main() {                           | .string "The sum of a, b, and c is %f."                  | String constant for printf         |
|   int a = 3;                           | main:                                                   | Entry point of the program         |
|   float b = 4.5;                       | push    rbp                                             | Prologue                            |
|   double c = 5.25;                     | mov     rbp, rsp                                         | Set up stack frame                 |
|   float sum;                            | sub     rsp, 32                                          | Allocate space for local variables |
|   sum = a + b + c;                     | mov     DWORD PTR [rbp-4], 3                             | Store integer variable a           |
|   printf("The sum of a, b, and c is %f.", sum); | movss   xmm0, DWORD PTR .LC0[rip]                       | Load float variable b              |
|   return 0;                            | movss   DWORD PTR [rbp-8], xmm0                          | Store float variable b             |
| }                                     | movsd   xmm0, QWORD PTR .LC1[rip]                        | Load double variable c             |
|                                       | movsd   QWORD PTR [rbp-16], xmm0                         | Store double variable c            |
|                                       | pxor    xmm0, xmm0                                       | Clear xmm0 register                |
|                                       | cvtsi2ss        xmm0, DWORD PTR [rbp-4]                  | Convert integer to float in xmm0   |
|                                       | addss   xmm0, DWORD PTR [rbp-8]                          | Add float b to xmm0                |
|                                       | cvtss2sd        xmm0, xmm0                               | Convert xmm0 from single to double |
|                                       | addsd   xmm0, QWORD PTR [rbp-16]                         | Add double c to xmm0               |
|                                       | cvtsd2ss        xmm0, xmm0                               | Convert xmm0 from double to single |
|                                       | movss   DWORD PTR [rbp-20], xmm0                         | Store result in float sum          |
|                                       | pxor    xmm1, xmm1                                       | Clear xmm1 register                |
|                                       | cvtss2sd        xmm1, DWORD PTR [rbp-20]                 | Convert float sum to double        |
|                                       | movq    rax, xmm1                                        | Move xmm1 to rax for printf        |
|                                       | movq    xmm0, rax                                        | Move rax to xmm0 for printf        |
|                                       | mov     edi, OFFSET FLAT:.LC2                             | Load address of string constant   |
|                                       | mov     eax, 1                                           | Set printf return value to 1      |
|                                       | call    printf                                           | Call printf function              |
|                                       | mov     eax, 0                                           | Set return value to 0             |
|                                       | leave                                                   | Epilogue                          |
|                                       | ret                                                     | Return to caller                  |
| ```                                   | ```                                                      | End of assembly code              |
