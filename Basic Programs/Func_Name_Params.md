# The function takes a string of characters with name as parameter. When the function is called, we pass along a name, which is used inside the function to print "Hello" and the name of each person.

### Things learnt
  - 

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `void myFunction(char name[]) {` | `myFunction:` | Function entry point for `myFunction` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on the stack for local variables |
| `  printf("Hello %s\n", name);` | `    mov     QWORD PTR [rbp-8], rdi` | Store the address of `name` parameter in `[rbp-8]` |
| | `    mov     rax, QWORD PTR [rbp-8]` | Move `name` address to `rax` |
| | `    mov     rsi, rax` | Move `rax` (address of `name`) to `rsi` (second argument to `printf`) |
| | `    mov     edi, OFFSET FLAT:.LC0` | Move the address of the format string into `edi` (first argument to `printf`) |
| | `    mov     eax, 0` | Prepare for `printf` call |
| | `    call    printf` | Call `printf` to print the message |
| `}` | `    nop` | No operation (placeholder) |
| | `    leave` | Restore stack pointer and base pointer of the caller |
| | `    ret` | Return from `myFunction` |
| `.LC0:` | `.string "Hello %s\n"` | String literal for `printf` format |
| `.LC1:` | `.string "Liam"` | String literal for `"Liam"` |
| `.LC2:` | `.string "Jenny"` | String literal for `"Jenny"` |
| `.LC3:` | `.string "Anja"` | String literal for `"Anja"` |
| `int main() {` | `main:` | Function entry point for `main` |
| | `    push    rbp` | Save base pointer of the caller |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    mov     edi, OFFSET FLAT:.LC1` | Move the address of `"Liam"` into `edi` (argument for first `myFunction` call) |
| | `    call    myFunction` | Call `myFunction("Liam")` |
| | `    mov     edi, OFFSET FLAT:.LC2` | Move the address of `"Jenny"` into `edi` (argument for second `myFunction` call) |
| | `    call    myFunction` | Call `myFunction("Jenny")` |
| | `    mov     edi, OFFSET FLAT:.LC3` | Move the address of `"Anja"` into `edi` (argument for third `myFunction` call) |
| | `    call    myFunction` | Call `myFunction("Anja")` |
| `  return 0;` | `    mov     eax, 0` | Return 0 from `main` |
| `}` | `    pop     rbp` | Restore base pointer of the caller |
| | `    ret` | Return from `main` |
