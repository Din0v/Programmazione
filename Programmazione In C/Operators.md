# Operators
- Operators are functions that use a symbolic name to perform mathematical or logical functions. 

- Operators are **predefined** in C just like they are in most other languages and most operators tend to be combined with the [[ Infix notation]]

## Types of operators 

1. **Logical Operators:** (Boolean operators) are operators that returns a boolean result that's based on the result of one or two boolean expressions. 

![[Pasted image 20210212160030.png]]

2. **Arithmetic Operators:** is a mathematical [[Functions]] that takes two #Operands operands and performs a calculation on them.

![[Pasted image 20210212160212.png]]

 -- A trick that is usally used in functions is:
 			the unary negation operator ! converts a non -zero operand into 0, and a zero operand into1. a common use of ! is in constrictions like this:
			
```c
if (!valid)  // if not valid
// rather than
if (valid == 0) // it's harder to read
```
 

3. **Other Operators:** may include:
		1. **Assignment** ```=``` it sets a variables to equal values, assigns the value of the expression at it's right to the variable at it's left
		
		2. **Relational** ```<, >, != ``` they will compare variables against each other. 
		
 	3. **Bitwise** ``` <<, >>, ~ ```

we have the ```->``` (arrow operator) which is used to access elements in [[Structures]], [[Unions]]; it's used with a [[Pointers]] variable pointing to a **Struct**. 


---
### Tags 
#Bitwise
#Logical_Operators

