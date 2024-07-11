# If else conditions example problems solving

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int doorCode = 1337;` | `    mov     DWORD PTR [rbp-4], 1337` | Store 1337 in `doorCode` (at `rbp-4`) |
| `    if (doorCode == 1337) {` | `    cmp     DWORD PTR [rbp-4], 1337` | Compare `doorCode` with 1337 |
| | `    jne     .L2` | Jump to `.L2` if `doorCode` is not equal to 1337 (false condition) |
| `        printf("Correct code.\nThe door is now open.");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Correct code.\nThe door is now open." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip false condition |
| `    } else {` | `.L2:` | Label for false condition |
| `        printf("Wrong code.\nThe door remains closed.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Wrong code.\nThe door remains closed." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for end of comparison |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |

---

### Things learnt
  - The given conditon `myNum < 0` need to check whether given number is less than 0, so in the ASM code we checked to know sign of given number we used `jns` stands for `Jump if Not Sign`, meaning it will jump to the label .L4 if the value compared in the previous instruction is non-negative (greater than or equal to zero).
  - Other than this everthing is same.


| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int myNum = 10;` | `    mov     DWORD PTR [rbp-4], 10` | Store 10 in `myNum` (at `rbp-4`) |
| `    if (myNum > 0) {` | `    cmp     DWORD PTR [rbp-4], 0` | Compare `myNum` with 0 |
| | `    jle     .L2` | Jump to `.L2` if `myNum` <= 0 (false condition) |
| `        printf("The value is a positive number.");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "The value is a positive number." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip other conditions |
| `    } else if (myNum < 0) {` | `.L2:` | Label for false condition |
| | `    cmp     DWORD PTR [rbp-4], 0` | Compare `myNum` with 0 |
| | `    jns     .L4` | Jump to `.L4` if `myNum` >= 0 (false condition) |
| `        printf("The value is a negative number.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "The value is a negative number." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip the final condition |
| `    } else {` | `.L4:` | Label for final condition (myNum == 0) |
| `        printf("The value is 0.");` | `    mov     edi, OFFSET FLAT:.LC2` | Load address of "The value is 0." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for end of comparison |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |

---

# 

| C Code | Assembly Code | Comments |
|--------|----------------|----------|
| `#include <stdio.h>` | | Include the standard input/output library |
| `int main() {` | `main:` | Function entry point |
| | `    push    rbp` | Save base pointer |
| | `    mov     rbp, rsp` | Set base pointer to stack pointer |
| | `    sub     rsp, 16` | Allocate 16 bytes on stack |
| `    int myAge = 25;` | `    mov     DWORD PTR [rbp-4], 25` | Store 25 in `myAge` (at `rbp-4`) |
| `    int votingAge = 18;` | `    mov     DWORD PTR [rbp-8], 18` | Store 18 in `votingAge` (at `rbp-8`) |
| `    if (myAge >= votingAge) {` | `    mov     eax, DWORD PTR [rbp-4]` | Move `myAge` to `eax` |
| | `    cmp     eax, DWORD PTR [rbp-8]` | Compare `eax` (myAge) with `votingAge` |
| | `    jl      .L2` | Jump to `.L2` if `myAge` < `votingAge` |
| `        printf("Old enough to vote!");` | `    mov     edi, OFFSET FLAT:.LC0` | Load address of "Old enough to vote!" string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| | `    jmp     .L3` | Jump to `.L3` to skip the else part |
| `    } else {` | `.L2:` | Label for else part |
| `        printf("Not old enough to vote.");` | `    mov     edi, OFFSET FLAT:.LC1` | Load address of "Not old enough to vote." string into `edi` |
| | `    mov     eax, 0` | Prepare for function call |
| | `    call    printf` | Call `printf` function |
| `    }` | `.L3:` | Label for end of if-else |
| `    return 0;` | `    mov     eax, 0` | Return 0 |
| `}` | `    leave` | Restore base pointer |
| | `    ret` | Return from function |
