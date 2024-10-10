# PreProcessor
It allows for programms to be easier to develop, easier to read, easier to Modify, and easier to port to other systems.

## PreProcessor at-Work 
1. it analyzes these statements before the analysis of the C program itself.
2. It's an instruction to your [[Compilers]] to do sth before compiling the [[Source-Code]].
3. it Could be **Anywhere** in your code 

## Utilization of the PreProcessor
1. Create my own constants and macros with the ```#Define ```  [[Statments]]
2. Build your own [[Library]] files with the ``` #Include ``` [[Statments]]
3. Make more powerfull programs with the conditional ``` #ifdef, #endif, #else ``` statments.


### The ``` #Include``` statement
is a  [[PreProcessor]] directive

1. it's not stictly part of the excutable program, however the program won't work without it 

2. THe [[Compilers]] is instructed to **Include** the contents of the file with the name ```.h``` in your program

3. the ```.h``` is called a [[Header-Files]] because it is usually included at the head of the program [[Source-File]]

