

#include <stdio.h>

void myFunction(char name[], int age) {
  printf("Hello %s. You are %d years old\n", name, age);
}

int main() {
  myFunction("Liam", 3);
  myFunction("Jenny", 14);
  myFunction("Anja", 30);
  return 0;
}

 .LC0:
        .string "Hello %s. You are %d years old\n"
myFunction:
        push    rbp
        mov     rbp, rsp
        sub     rsp, 16
        mov     QWORD PTR [rbp-8], rdi
        mov     DWORD PTR [rbp-12], esi
        mov     edx, DWORD PTR [rbp-12]
        mov     rax, QWORD PTR [rbp-8]
        mov     rsi, rax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        nop
        leave
        ret
.LC1:
        .string "Liam"
.LC2:
        .string "Jenny"
.LC3:
        .string "Anja"
main:
        push    rbp
        mov     rbp, rsp
        mov     esi, 3
        mov     edi, OFFSET FLAT:.LC1
        call    myFunction
        mov     esi, 14
        mov     edi, OFFSET FLAT:.LC2
        call    myFunction
        mov     esi, 30
        mov     edi, OFFSET FLAT:.LC3
        call    myFunction
        mov     eax, 0
        pop     rbp
        ret
