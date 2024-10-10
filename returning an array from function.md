# Return array from function 

i encountered this issue solving the [3rd problem](https://www.hackerrank.com/challenges/compare-the-triplets/) on HackerRank


```C 
int* compareTriplets(int a_count, int* a, int b_count, int* b, int* result_count) {
    int sumA = 0, sumB = 0, i; 
    for (i = 0; i < a_count; i++) {
        if (a[i] > b[i]) {
            sumA = sumA + 1;
        } else if (a[i] < b[i]) {
            sumB = sumB + 1;
        }
    }

    *result_count = 2;
    int *res = (int*)malloc(*result_count * sizeof(int));
   
    res[0] = sumA;
    res[1] = sumB;

    return res;
}
```
# Return array from function 

```C 
int* compareTriplets(int a_count, int* a, int b_count, int* b, int* result_count) {
    int sumA = 0, sumB = 0, i; 
    for (i = 0; i < a_count; i++) {
        if (a[i] > b[i]) {
            sumA = sumA + 1;
        } else if (a[i] < b[i]) {
            sumB = sumB + 1;
        }
    }

    *result_count = 2;
    int *res = (int*)malloc(*result_count * sizeof(int));
   
    res[0] = sumA;
    res[1] = sumB;

    return res;
}
```

To return the integer array from the function, you should:
- Store the size of the array to be returned in the result_count variable.
- Allocate the array statically or dynamically.

**For example**:

```c
  int* return_integer_array_using_static_allocation(int* result_count) {
      *result_count = 5;
 
      static int a[5] = {1, 2, 3, 4, 5};
 
      return a;
  }

/*----------------------------------------------*/

  int* return_integer_array_using_dynamic_allocation(int* result_count) {
      *result_count = 5;
 
      int *a = malloc(5 * sizeof(int));
 
      for (int i = 0; i < 5; i++) {
          *(a + i) = i + 1;
      }
 
      return a;
  }
 

```


### Tags 
#Arrays 
#Functions 
#Cool_trick 
#Algorithms 
