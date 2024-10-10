# Format Specifiers
- Format specifiers are used when displaying variables as outputs, they specify the type of data of the variable to be displayed. 

- Format specifiers are specified using ```%``` symbol.

- Arguments are sperated by a comma ``` ,```. 

- The character that immidiately follows the percent sign specifies what type of value is displayed. 

**The Chart**:

![[Format specifiers.jpeg]]

%g is a nice floating number format specifier!!

```c
#include <stdio.h>
main() {
   char ch = 'B';
   printf("%c\n", ch); //printing character data
   //print decimal or integer data with d and i
   int x = 45, y = 90;
   printf("%d\n", x);
   printf("%i\n", y);
   float f = 12.67;
   printf("%f\n", f); //print float value
   printf("%e\n", f); //print in scientific notation
   int a = 67;
   printf("%o\n", a); //print in octal format
   printf("%x\n", a); //print in hex format
   char str[] = "Hello World";
   printf("%s\n", str);
   printf("%20s\n", str); //shift to the right 20 characters including the string
   printf("%-20s\n", str); //left align
   printf("%20.5s\n", str); //shift to the right 20 characters including the string, and print string up to 5 character
   printf("%-20.5s\n", str); //left align and print string up to 5 character
}
```