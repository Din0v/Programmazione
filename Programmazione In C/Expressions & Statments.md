# Expressions & Statements 
 
 
 ## Statements
 **Statements** form the basic program steps of C and most statements are constructed from expressions.
 
 - Statements are the building blocks of a program:
 	1. A program is a series of statements with special syntax ending with a semicolon.
 	2. A complete instruction to the computer.
 	
- C considers any expression to be a statement if you append a semicolon.


### Compund statements:
are two or more statements grouped together by enclosing them in braces (blocks) **{}**

```c
switch (expr) {
case ABC:
case DEF:
	statement;
	break;
case UVW:
	statement;
	/\*FALLTHROUGH\*/
case XYZ:
	statement;
	break;
}
```

 
 ## Expressions
 An expression consists of a combination of operators and operands
 
 - #Operands:
	 1. are what an operator operates on.
	 2. opreands can be constans, varaibles or a combenation of the two.
	 3. every expression has a value. 