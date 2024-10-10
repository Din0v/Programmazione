# Example on structures 
[[Structures]]

#### Esempio 1 : 
Nota Bene: 
- come si usa il **Dot** operator (.) per accedere ai struct e modificarli. 
- **attenzione al punto virgola dopo la fine di ogni struct.**
- we use the arrow **(- >)** to access a struct Pointer
- 

```c 
#include <stdio.h>
#include <string.h> // perchè abbiamo usato strcpy.
struct Books{ // [Books] is the tag of the stuct
	char title[50];
	char author[50];
	char subject[100];
	int book_id;
}; // they end with a semicolon.

  

int main(){
	struct Books Book1; // First book of type book
	struct Books Book2; // Second book of type book
	
	//Book 1 specs, Notice how we use the dot(.) operator to access the element of a struct just like java.
	strcpy( Book1.title, "C Programming");
	strcpy( Book1.author, "PincoPallino");
	strcpy( Book1.subject, "ProgrammingTutorial");
	Book1.book_id = 696942;
	/* book 2 specification */
	strcpy( Book2.title, "Telecom Billing");
	strcpy( Book2.author, "Zara Ali");
	strcpy( Book2.subject, "Telecom Billing Tutorial");
	Book2.book_id = 6495700;
	
	  
	
	/* print Book1 info */
	
	printf( "Book 1 title : %s\n", Book1.title);
	printf( "Book 1 author : %s\n", Book1.author);
	printf( "Book 1 subject : %s\n", Book1.subject);
	printf( "Book 1 book_id : %d\n\n", Book1.book_id);
	
	/* print Book2 info */
	
	printf( "Book 2 title : %s\n", Book2.title);
	printf( "Book 2 author : %s\n", Book2.author);
	printf( "Book 2 subject : %s\n", Book2.subject);
	printf( "Book 2 book_id : %d\n\n", Book2.book_id);

return 0;

}
```

### Tags 
[[Structures]]
#Explainer 
#Basics 