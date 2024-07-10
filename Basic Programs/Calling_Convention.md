# Windows x64 Calling Convention

When a function is called, you could theoretically pass parameters via registers, the stack, or even on disk. You just need to be sure that the function you are calling knows how you are calling it. This isn't too big of a problem if you are using your own functions, but things would get messy when you start using libraries. To solve this problem, we have calling conventions that define how parameters are passed to a function, who allocates space for local variables, and who cleans up the stack.

The callee refers to the function being called, and the caller is the function making the call.

There are several different calling conventions including `cdecl`, `syscall`, `stdcall`, `fastcall`, and many more. Because we are going to be reverse engineering on x64 Windows, we will mostly focus on x64 `fastcall`. When we get into the DLL chapter, we will also have to know `cdecl`. If you plan on reversing on other platforms, be sure to learn the calling convention(s).

You will usually see a double underscore prefix (`__`) before a calling convention's name. For example: `__fastcall`. I won't be doing this because it's not necessary.

## Fastcall

`Fastcall` is the calling convention for x64 Windows. Windows uses a four-register fastcall calling convention by default. Fastcall pushes function parameters backward (right to left). When talking about calling conventions, you will hear about something called the "Application Binary Interface" (ABI). The ABI defines various rules for programs such as calling conventions, parameter handling, and more.

### How does the x64 Windows calling convention work?

- The first four arguments/parameters are passed in registers. 
    - Parameters that are not floating point values (floats or doubles) will be passed via `RCX`, `RDX`, `R8`, and `R9` (in that order). Non-floating point values include pointers, integers, booleans, chars, etc.
    - Floating-point parameters will be passed via `XMM0`, `XMM1`, `XMM2`, and `XMM3` (in that order). Floating-point values include floats and doubles.
    - If the parameter being passed is too big to fit in a register, then it is passed by reference. Parameters are never spread across multiple registers.
    - Any other parameters are put on the stack.
- All parameters, even ones passed through registers, have space reserved on the stack for them. Also, there is always space made for 4 parameters on the stack even if there are no parameters passed. This space isn't completely wasted because the compiler can, and often will, use it.
- The base pointer (`RBP`) is saved so it can be restored.
- A function's return value is passed via `RAX` if it's an integer, bool, char, etc., or `XMM0` if it's a float or double.
- Member functions (functions that are part of a class/struct) have an implicit first parameter for the "this" pointer. Because it's a pointer, it will be passed via `RCX`.

### Caller Responsibilities

- The caller is responsible for allocating space for parameters for the callee. The caller must always allocate space for 4 parameters even if no parameters are passed.
- The registers `RAX`, `RCX`, `RDX`, `R8`, `R9`, `R10`, `R11` are considered volatile and must be considered destroyed on function calls (unless otherwise safety-provable by analysis such as whole program optimization).
- The registers `RBX`, `RBP`, `RDI`, `RSI`, `RSP`, `R12`, `R13`, `R14`, and `R15` are considered nonvolatile and must be saved and restored by a function that uses them.
