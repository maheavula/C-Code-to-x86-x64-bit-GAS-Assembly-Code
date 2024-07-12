# Switch Case conditional statement program

### Things learnt
  - There is no case is above 7 so intially checked for if the given number is above 7 then program exits with instruction of `ja  .L2` > Jump to `.L2` if day > 7.
  - `mov rax, QWORD PTR .L4[0+rax*8]` this is new to us so here why it is used, In assembly, jump tables are used for efficient branching based on the value of a variable. Instead of using a series of conditional jumps (cmp and jz, jnz, etc.), a jump table allows the program to directly jump to the appropriate code section.
  - Suppose rax is 4:
  - The offset calculation: `4 * 8 = 32 bytes.`
  - Accessing `.L4[0+rax*8]` means accessing `.L4 + 32.`
  - At `.L4 + 32`, the entry is .quad .L7, which means the address stored there is the address of label .L7.
  - Each `qword address` is `8bytes` so starts from `8bytes` through `.L10` and then next `16bytes` through `.L9`.

# Jump Table Example

The following is an example of a jump table in assembly. Each entry in the jump table points to a different label.

## Jump Table Definition

```assembly
.L4:
    .quad   .L2     ; Address of .L2    .L2: .L4 + 0 bytes
    .quad   .L10    ; Address of .L10   .L2: .L4 + 8 bytes
    .quad   .L9     ; Address of .L      .L2: .L4 + 16 bytes
    .quad   .L8     ; Address of .L8    .L2: .L4 + 24 bytes 
    .quad   .L7     ; Address of .L7    .L2: .L4 + 32 bytes
    .quad   .L6     ; Address of .L6    .L2: .L4 + 40 bytes
    .quad   .L5     ; Address of .L5    .L2: .L4 + 48 bytes
    .quad   .L3     ; Address of .L3    .L2: .L4 + 56 bytes
```
    

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int day = 4;` | `    mov     DWORD PTR [rbp-4], 4` | Store 4 in `day` (at `rbp-4`) |
| `    switch (day) {` | `    cmp     DWORD PTR [rbp-4], 7` | Compare `day` with 7 |
| | `    ja      .L2` | Jump to `.L2` if `day` > 7 |
| | `    mov     eax, DWORD PTR [rbp-4]` | Move `day` to `eax` |
| | `    mov     rax, QWORD PTR .L4[0+rax*8]` | Get address of case label |
| | `    jmp     rax` | Jump to case label |
| `    case 1:` | `.L10:` | Label for case 1 |
| `        printf("Monday");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Monday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 2:` | `.L9:` | Label for case 2 |
| `        printf("Tuesday");` | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Tuesday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 3:` | `.L8:` | Label for case 3 |
| `        printf("Wednesday");` | `    mov     edi, OFFSET FLAT:.LC2` | Load address of "Wednesday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 4:` | `.L7:` | Label for case 4 |
| `        printf("Thursday");` | `    mov     edi, OFFSET FLAT:.LC3` | Load address of "Thursday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 5:` | `.L6:` | Label for case 5 |
| `        printf("Friday");` | `    mov     edi, OFFSET FLAT:.LC4` | Load address of "Friday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 6:` | `.L5:` | Label for case 6 |
| `        printf("Saturday");` | `    mov     edi, OFFSET FLAT:.LC5` | Load address of "Saturday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    jmp     .L2` | Jump to end of switch |
| `    case 7:` | `.L3:` | Label for case 7 |
| `        printf("Sunday");` | `    mov     edi, OFFSET FLAT:.LC6` | Load address of "Sunday" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `        break;` | `    nop` | No operation, end of switch case |
| `    }` | `.L2:` | Label for end of switch |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
