# Segmentation Fault
is an error that you get when you access a part of the memory that you shouldn't!!

i ecoutered this problem when i mistakenly typed the following:

```c
printf("n Enter the value to insert: \n");
scanf("%d, &k");
```

instead of the correct form of $taking \ of \ the \ asterisk$

```c 
printf("n Enter the value to insert: \n");
scanf("%d", &k);
```

look at ==*insertIntoArray.c*== in the exercises 

it is usually triggered when i mistankenly fuck up [[C Format Specifiers]].




### Tags
#Debugging 
#Erros