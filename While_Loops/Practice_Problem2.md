# If else conditon inside while loop condition.

### Things learnt
  - Need to look at the flow to make easy, to make less number of jumps in program


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int dice = 1;` | `    mov     DWORD PTR [rbp-4], 1` | Initialize `dice` to 1 |
| `    while (dice <= 6) {` | `    jmp     .L2` | Jump to loop condition check |
| | `.L5:` | Loop body label |
| `        if (dice < 6) {` | `    cmp     DWORD PTR [rbp-4], 5` | Compare `dice` with 5 |
| | `    jg      .L3` | Jump to `.L3` if `dice` > 5 |
| `            printf("No Yatzy\n");` | `    mov     edi, OFFSET FLAT:.LC0` | Load format string address into `edi` (first argument of `puts`) |
| | `    call    puts` | Call `puts` function |
| `        } else {` | `    jmp     .L4` | Jump to end of if-else |
| `            printf("Yatzy!\n");` | `.L3:` | Else block label |
| | `    mov     edi, OFFSET FLAT:.LC1` | Load format string address into `edi` (first argument of `puts`) |
| | `    call    puts` | Call `puts` function |
| `        }` | `.L4:` | End of if-else block |
| `        dice = dice + 1;` | `    add     DWORD PTR [rbp-4], 1` | Increment `dice` |
| `    }` | `.L2:` | Loop condition check label |
| | `    cmp     DWORD PTR [rbp-4], 6` | Compare `dice` with 6 |
| | `    jle     .L5` | Jump to `.L5` if `dice` <= 6 |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
