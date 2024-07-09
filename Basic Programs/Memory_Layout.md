# Assembly Memory Layout

## Assembly Segments
There are different segments/sections in which data or code is stored. They are laid out in the following order:

1. **Stack** - Holds non-static local variables. Discussed more in-depth soon.
2. **Heap** - Contains dynamically allocated data that can be uninitialized at first.
3. **.data** - Contains global and static data initialized to a non-zero value.
4. **.bss** - Contains global and static data that is uninitialized or initialized to zero.
5. **.text** - Contains the code of the program.

## Overview of Memory Sections
Here is a general overview of how memory is laid out in Windows. This is extremely simplified.

![Memory Sections Diagram](memory_sections.png)

> Important:
> The diagram above shows the direction variables (and any named data, even structures) are put into or taken out of memory. The actual data is put into memory differently. This is why stack diagrams vary so much. You'll often see stack diagrams with the stack and heap growing towards each other or high memory addresses at the top. I will explain more later. The diagram I'm showing is the most relevant for reverse engineering. Low addresses being at the top is also the most realistic depiction.

### Stack
- **Description**: Area in memory used for static data allocation. Imagine the stack with low addresses at the top and high addresses at the bottom, identical to a normal numerical list. Data is read and written as "last-in-first-out" (LIFO).
- **Example**: 
    ```c
    int Square(int x){
        return x * x;
    }
    
    int main(){
        int num = 5;
        Square(5);
    }
    ```
- **Registers**:
    - **Stack Pointer (RSP/ESP/SP)**: Keeps track of the top of the stack.
    - **Base Pointer (RBP/EBP/BP)**: Keeps track of the base/bottom of the stack.

### Explanation
When `main()` is called, a stack frame is created. This includes the local variable `num` and the parameters passed to it. When `main()` calls `Square()`, the base pointer (RBP) and the return address are both saved.

### Assembly Example
```assembly
mov RAX, 15    ; RAX = 15
call func      ; Call func. Same as func();
mov RBX, 23    ; RBX = 23. This line is saved as the return address for the function call.
```

### Heap
- **Description**: Used for dynamic allocation and is a little slower to access. Typically used for data that is dynamic (changing or unpredictable). When you add data to the heap it grows towards higher addresses.

## Program Image
- **Description**: This is the program/executable loaded into memory. On Windows, this is typically a Portable Executable (PE).
## TEB and PEB
- **TEB**: The Thread Environment Block stores information about the currently running thread(s).
- **PEB**: The Process Environment Block stores information about the process and the loaded modules.
## Endianness
Given the value of 0xDEADBEEF, how should it be stored in memory?

 - Big Endian: The most significant byte (far left) is stored first (0xDEADBEEF).
 - Little Endian: The least significant byte (far right) is stored first (0xEFBEADDE).

