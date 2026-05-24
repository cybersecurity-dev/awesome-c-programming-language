# [Dynamic Memory Management](https://wikipedia.org/wiki/C_dynamic_memory_allocation)

## [malloc](https://man7.org/linux/man-pages/man3/malloc.3p.html)

```c
#include <stdlib.h>
void *malloc(size_t size);
```

```c
int ptrIArray[10];
```

`malloc()` takes a single argument (**the amount of memory to allocate in bytes**).

```c
// without a cast
void *raw = malloc(10 * sizeof(int));
if (!raw) return 1;

int *ptrIArray = (int *)raw;
```

```c
// with a cast
int *ptrIArray = (int*)malloc(10 * sizeof(int));
```

## [calloc](https://man7.org/linux/man-pages/man3/calloc.3p.html)
```c
#include <stdlib.h>
void *calloc(size_t nelem, size_t elsize);
```

Allocates memory for an array of num objects of size and initializes all bytes in the allocated storage to zero.

```c
int *ptrIArray = (int *) calloc(5, sizeof(int));
for (iter = 0; iter < 5; ++i) {
    printf("%d ", ptrIArray[iter]);   // contains -> 0
}
```

```c
int *ptrIArrayMalloc = (int *) malloc(5, sizeof(int));
int *ptrIArrayCalloc = (int *) calloc(5, sizeof(int));
for (iter = 0; iter < 5; ++i) {
    printf("%d ", ptrIArrayMalloc[iter]);   // contains -> garbage value
    printf("%d ", ptrIArrayCalloc[iter]);   // contains -> 0
}
```

* When to Use What?
    * ✔ `Use malloc()` when:
        * You will immediately assign data to all elements.
        * You want slightly faster allocation.

    * ✔ `Use calloc()` when:
        * You need zero-initialized memory.
        * You want to avoid uninitialized garbage data.
        * You are creating:
            * Arrays
            * Buffers
            * Structs
            * Strings

## [realloc](https://man7.org/linux/man-pages/man3/realloc.3p.html)

`realloc()` is used to resize previously allocated memory (from `malloc()`, `calloc()`, or a previous `realloc()` call). It allows you to:
* increase array size
* shrink array size
* avoid losing existing data
* avoid manually copying the old array

```c
#include <stdlib.h>
void *realloc(void *ptr, size_t size);
```

* If ptr is a `null pointer`, realloc() shall be equivalent to malloc() for the specified size.


```c
int main() {
    void *raw;
    int *arr;
    int iter;

    // Allocate initial memory for 5 integers
    raw = malloc(5 * sizeof(int));
    if (raw == NULL) {
        printf("malloc failed\n");
        return 1;
    }
    arr = (int *)raw;
    // Fill initial values
    for (iter = 0; iter < 5; ++iter) {
        arr[iter] = iter + 1;
    }

    printf("Initial array:\n");
    for (iter = 0; iter < 5; ++iter) {
        printf("%d ", arr[iter]);
    }
    printf("\n");

    // Resize memory to hold 10 integers
    raw = realloc(arr, 10 * sizeof(int));
    if (raw == NULL) {
        // Always check for failure
        printf("realloc failed\n");
        free(arr); // Must free
        return 1;
    }
    arr = (int *)raw; // Assign back after successful realloc

    // Fill new elements
    for (iter = 5; iter < 10; ++iter) {
        arr[iter] = (iter + 1) * 10;
    }

    printf("Array after realloc:\n");
    for (iter = 0; iter < 10; ++iter) {
        printf("%d ", arr[iter]);
    }
    printf("\n");

    // Free memory
    free(arr);
    return 0;
}
```

* If `realloc()` can resize the block in-place, Then no old memory is freed, because the block stays in the same location.
* If `realloc()` cannot extend in-place, Then it will:
    * allocate a new block (different memory address)
    * copy old data to the new memory
    * free the old block


* If `realloc()` **fails** (returns `NULL`) Then:
    * old memory is NOT freed
    * old pointer is still valid
    * you must free manually if you want

## [free](https://man7.org/linux/man-pages/man3/free.3p.html)

```c
#include <stdlib.h>
void free(void *ptr);
```
Releases the specified block of memory back to the system.

❗`free()` does NOT know the array size.

❗`free()` does NOT need the array size.

❗`free()` only needs the pointer.

```
            ptrIArray pointer ↓
┌──────────────┬──────────────────────────┐
│ metadata     │  your allocated memory   │
└──────────────┴──────────────────────────┘
```

```c
free(ptrIArray);
```

The memory allocator:

* looks at the pointer
* steps backwards to read the hidden metadata
* gets the size and allocation info
* frees the correct amount of memory

**`That's why you do NOT provide the size to free()`**.