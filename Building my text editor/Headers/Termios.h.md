# Termios.h 

i think it's an abbriviation for 
**Terminal input/output stream**

the official discription is: 
a file that contians information used by subroutines ( mini programs ) that apply to terminal files. 

 Commands how i understood them: 
 
 ``` tcgetattr()``` is terminal command get attribute, basically reading it. and adding it to the struct. 
 
 ```tcsetattr()``` terminal command set attribute it writes down the new terminal attribures.
 
``` TCSAFLUSH``` it specifies when to apply the change to an attribute. 

```c_iflag``` C input flag

```c_oflag``` C output flag 

```c_cflag``` C control flag 

```ECHO```  is a [[Bit field]] or bit flag 



---
#Kilo