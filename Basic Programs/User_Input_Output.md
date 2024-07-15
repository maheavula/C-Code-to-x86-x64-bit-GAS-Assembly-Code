# To write a program take input from user and print the value

### Things learnt
  - Puts function is used for to display prompts before reading inputs from user.
  - Printf function is used for write the output to user.

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack for local variables |
| `    int myNum;` | | Declare an integer variable to store user input |
| `    printf("Type a number and press enter: \n");` | `    mov     edi, OFFSET FLAT:.LC0` | Load the address of the format string into `edi` |
| | `    call    puts` | Call `puts` to print the prompt |
| `    scanf("%d", &myNum);` | `    lea     rax, [rbp-4]` | Load the address of `myNum` into `rax` |
| | `    mov     rsi, rax` | Move the address of `myNum` into `rsi` |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load the format string address into `edi` |
| | `    mov     eax, 0` | Prepare for the `scanf` call |
| | `    call    __isoc99_scanf` | Call `scanf` to get user input |
| `    printf("Your number is: %d", myNum);` | `    mov     eax, DWORD PTR [rbp-4]` | Load `myNum` into `eax` |
| | `    mov     esi, eax` | Move `myNum` into `esi` for `printf` |
| | `    mov     edi, OFFSET FLAT:.LC2` | Load the format string address into `edi` |
| | `    mov     eax, 0` | Prepare for the `printf` call |
| | `    call    printf` | Call `printf` to print the user's number |
| `    return 0;` | `    mov     eax, 0` | Return 0 from `main` |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
