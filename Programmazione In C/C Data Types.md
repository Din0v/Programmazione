# Data Types 

A data type  represents a type of data which you can process using your program.

**Examples Include**: ```int, float, doubles, etc```

it corresponds to byte sizes on the platform of your program. 

[[Primitive DataTypes]]: are types which aren't [[Objects]] and store all sorts of data. 

## Some of the basic C DataTypes:
1. The difference between types is the amount of memory they occupy and the range of values they can hold.
2. The amount of storage that is allocated to store a particular type of data. 
3. depends on the computer you are running ==Machine-Dependent==
4. an integer might take up 32bits on your computer or perhaps it might take 64bits. 

- If an integer is preceded by a zero and the letter x ```0x / 0X ``` the value is taken as being expressed in hexadecimals. 

### Float
means number that contains decimals.
floating points can be expressed in Scientific notation.

### Double
The type is same as the type float, only with roughly twice the **precision**, most of computers represnt doubles using 64bits. 
all floating point constants are taken as a double by the C [[Compilers]]

To **explicitly** express a float constants, append either an ==f== or an ==F== to the end of the number. 
```c
float x = 3.14f; // appending the F
```

### Bool
is a data type used to store just the values 1 or 0 used for indicating ==on/off== , ==true/false== or any binary choice.
- bool variables are used in programs that need to indicate a boolean condition.
- A variable of this type might be used to indicate whether all data has been read from a file. 

## C Provides additional DataTypes 
1. it gives the programmer the option of matching a type to a particular use case
2. integer types vary in the range of values offered and in whether negative numbers can be used. 

==Examples==: ``` Short, long and unsigned```

### ENUMS 
#### [[Enumeration Constant]]
The **enumerated type**
are a data type that allows a programmer to define a variable and specify the valid values that could be stored into that variable. 
*It's basically a custom datatype*

#### How to use the enum type:
1. You need to define it and give it a name
2. Initiated by the keyword enum
3. Then the name of the enumerated data type
4. Then the list of identifieres (enclosed in a set of curly braces **{}**)  that defines the permissiable values that can be assigned. 

```c
enum week{Mon, Tue, Wed, Thur, Fri, Sat, Sun}; 
  
int main() 
{ 
    enum week day; // abbiamo creato una variable di tipo week di nome day.
    day = Wed; 
    printf("%d",day); // stampa il numero del elemento nella lista
    return 0; 
} 
```

 ### Char
 chars represent a single character such as letter =='a'== the digit character =='6'== or a semicolon ==';'==
 
- you can also declare char variables as **unsigned**. 

==Examples==

```c 
char pincopallino; 
pincopallino = 'T';
```

- If you omit the quotes the [[Compilers]] will think that T is the name of a variable.

- If you use a double quote the compiler will think that you are using a [[String]].

- You can use the Numerical [[ASCII]] code to assign values. 
```c 
char grade = 65;
==> out: 'A'
```
