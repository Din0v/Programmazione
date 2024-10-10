# Linked Lists 
simply... 
are composed of single elements connected to each other with a [[Pointers]]

memebers of a linked list are contiguos elements, but since they are dynamically allocated, with [[Malloc]], they are technically scattered all around in the memory. 

prototipo di una funzione linkedList
```c
void list_int(List *list, void (*destroy)(void *data))

```

Linked lists have:
1. Head: where the list begins 
2. Nodes: is the block of data and pointer to the next element 
3. Edge: is the Next pointer

