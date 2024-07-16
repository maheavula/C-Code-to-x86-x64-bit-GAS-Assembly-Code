.LC0:
        .string "The sum of %d + %d is: %d\n"
calculateSum:
        push    rbp
        mov     rbp, rsp
        sub     rsp, 32
        mov     DWORD PTR [rbp-20], edi
        mov     DWORD PTR [rbp-24], esi
        mov     edx, DWORD PTR [rbp-20]
        mov     eax, DWORD PTR [rbp-24]
        add     eax, edx
        mov     DWORD PTR [rbp-4], eax
        mov     ecx, DWORD PTR [rbp-4]
        mov     edx, DWORD PTR [rbp-24]
        mov     eax, DWORD PTR [rbp-20]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        nop
        leave
        ret
main:
        push    rbp
        mov     rbp, rsp
        mov     esi, 3
        mov     edi, 5
        call    calculateSum
        mov     esi, 2
        mov     edi, 8
        call    calculateSum
        mov     esi, 15
        mov     edi, 15
        call    calculateSum
        mov     eax, 0
        pop     rbp
        ret





#include <stdio.h>

void calculateSum(int x, int y) {
  int sum = x + y;
  printf("The sum of %d + %d is: %d\n", x, y, sum);
}

int main() {
  calculateSum(5, 3);
  calculateSum(8, 2);
  calculateSum(15, 15);
  return 0;
}

 
