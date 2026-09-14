# [Pointers](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Pointers.html)

```c
int ival;
double darray[5];
```

- ival has type int; we say &ival is a `"pointer to int."`
- darray has type double[5]; we say &darray is a `"pointer to an array of five doubles."`
- darray[3] has type double; we say &darray[3] is a `"pointer to double."`


## Pointer Arrays

## Pointer to pointer

- `A T *` points to a **`T`**.
- `A T **` points to a **`T *`**.


## [Pointers to void](https://wikipedia.org/wiki/Void_type)
**`void *`** is needed in `C` to allow generic programming and type‑independent memory operations in language. For example; void * is the type returned by malloc and calloc. So it works for any type with void pointer.

```c
// Allocate memory for 5 integers
void *raw = malloc(5 * sizeof(int));
if (!raw) return 1;

int *arr = (int *)raw;
//...

free(arr);

```

## [Pointers to functions](https://wikipedia.org/wiki/Function_pointer)

A `function pointer` in C is a variable that stores the **address of a function**, just like a normal pointer stores the address of data.

```c
// Simple Functions
int add(int a, int b) { return a + b; }
int mul(int a, int b) { return a * b; }

int main(void) {
    // Declare a pointer to a function taking (int, int) and returning int
    int (*ptrF)(int, int);

    // Point it to 'add' and call
    ptrF = add;
    printf("add(2, 3) = %d\n", ptrF(2, 3));

    // Re-point it to 'mul' and call
    op = mul;
    printf("mul(5, 7) = %d\n", ptrF(5, 7));

    return 0;
}
```