# Pointers in Assembly and C/C++

Assembly has its ways of working with pointers and memory addresses like C/C++ does. In C/C++, you can use dereferencing to get the value inside a memory address. For example:

```c
int main() {
    int num = 10;
    int* ptr = &num;        // ptr is now the address of num
    /* 
    ptr is dereferenced so it prints what's inside of the address 
    that it's holding. The value inside of the address that it's 
    holding is 10.
    */
    printf("%d", *ptr);   
}
```
Two of the most important things to know when working with pointers and addresses in Assembly are LEA and square brackets.

### Square Brackets
Square brackets signify "address pointed to". For example, [var] is the address pointed to by var. In other words, when using [var] we want to access the memory address that var is holding.

### LEA (Load Effective Address)
Ignore everything about square brackets when working with LEA. LEA is short for Load Effective Address, and it's used for calculating and loading addresses. It's important to note that when working with the LEA instruction, square brackets do not dereference.

It's important to note that when working with the LEA instruction, square brackets do not dereference.

It's important to note that when working with the LEA instruction, square brackets do not dereference.

Have I said it enough? Don't let this confuse you. People who don't know that LEA breaks the rules when working with square brackets get extremely confused very quickly. LEA is used to load and calculate addresses, NOT data. It doesn't matter if there are square brackets or not, it's dealing with addresses ONLY. LEA tends to mess with many people's heads. Don't let it do that to you.

*Example of Dereferencing and a Pointer in Assembly
assembly
Copy code*

`lea RAX, [var]`

`mov [RAX], 12`

In the example above, the address of var is loaded into RAX. This is LEA we are working with, there is no dereferencing. RAX is essentially a pointer now. Then 12 is moved into the address that RAX holds (often said as the address pointed to by RAX). The address pointed to by RAX is the var variable. If that Assembly was executed, var would be 12.

Earlier I said that LEA can be used to calculate addresses, and it often is.

assembly
Copy code

`lea RAX, [RCX+8]`    ; This will set RAX to the address of RCX+8.

`mov RAX, [RCX+8]`   ; This will set RAX to the value inside of RCX+8.

One more time:
It's important to note that when working with LEA, square brackets do not dereference.

You'll see LEA and MOV used all the time so be sure you understand this. I know it can be a tad confusing, but just remember that LEA is for addresses.
