sizeof is an [[Operators]] and it's ==NOT== a function.

the difference being, that an operator is compiled to a sequence of instructions by the compiler, but if he code calls a [[Functions]], it has to jump to a separate piece of code.

hence ```sizeof``` is calculated when the program is compiled and the [[Compilers]] determine the size of the storage at compile time. 

```c
sizeof( A pointer); 
```

usually returns 4 or 8 bytes depending on the system architechture. 
either it's a 32Bit system or a 64Bit one. 



--- 
### Tags 
#Basics 