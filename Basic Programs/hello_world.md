## Hello world program

| C Code                                    | Assembly Code                        | Comments                             |
|-------------------------------------------|--------------------------------------|--------------------------------------|
| ```c                                      | ```assembly                          |                                      |
| #include <stdio.h>                         | .LC0:                                | Label for the string "Hello World!"  |
|                                           | .string "Hello World!"                | String literal stored in .LC0        |
| int main() {                               | main:                                | Entry point for the program          |
|   printf("Hello World!");                  | push    rbp                           | Preserve base pointer               |
|   return 0;                                | mov     rbp, rsp                      | Set up base pointer                 |
| }                                         | mov     edi, OFFSET FLAT:.LC0         | Load address of the string          |
|                                           | mov     eax, 0                        | Return value set to 0                |
|                                           | call    printf                       | Call printf function                |
|                                           | mov     eax, 0                        | Set return value to 0                |
|                                           | pop     rbp                           | Restore base pointer                |
|                                           | ret                                   | Return from main function           |
| ```                                       | ```                                   |                                      |
