<div align="center">
    <p align="center">
        <a href="https://wikipedia.org/wiki/C_standard">
          <img width="10%" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/C_logo.svg" />
        </a>
    </p>

# **`Awesome`** [C](https://wikipedia.org/wiki/ANSI_C) Programming [Language](https://wikipedia.org/wiki/C_(programming_language)) [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[**`ANSI C`**](https://wikipedia.org/wiki/ANSI_C) | [**`C99`**](https://wikipedia.org/wiki/C99) | [**`C11`**](https://wikipedia.org/wiki/C11_(C_standard_revision)) | [**`C17`**](https://wikipedia.org/wiki/C17_(C_standard_revision)) | [**`C23`**](https://wikipedia.org/wiki/C23_(C_standard_revision))
</div>

[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiV8oriwlPA6uUzB_SB0GzxY&si=aZ40OWv_hIcQA1U2)
[![Reddit](https://img.shields.io/badge/Reddit-FF4500?style=for-the-badge&logo=reddit&logoColor=white)](https://www.reddit.com/r/cprogramming/new/)

<p align="center">
    <a href="https://github.com/cybersecurity-dev/"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/github.svg" alt="GitHub"></a>
    &nbsp;
    <a href="https://www.youtube.com/@CyberThreatDefence"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/youtube.svg" alt="YouTube"></a>
    &nbsp;
    <a href="https://cyberthreatdefence.com/my_awesome_lists"><img height="20" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/blog.svg" alt="My Awesome Lists"></a>
    <img src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/bar.gif">
</p>

## 📖 Contents
- [Pointers](#pointers)
    - [Pointer to pointer](#pointer-to-pointer)
    - [void pointers](#void-pointers)
    - [Function Pointers](#function-pointers)
- [Dynamic Memory Management](#dynamic-memory-management)
    - [malloc](#malloc)
    - [calloc](#calloc)
    - [realloc](#realloc)
    - [free](#free) 
- [Structures](#structures)
- [Unions](#unions)
- [Enumarations](#enumarations)
- [Bitwise Operations](#bitwise-operations)
- [C String Handling](#c-string-handling)
- [C Signal Handling](#c-signal-handling)
- [C Process Control](#c-process-control)
- [My Other Awesome Lists](#my-other-awesome-lists)
- [Contributing](#contributing)
- [Contributors](#contributors)

## Declarations & Definitions

## Type Conversions

## Arrays

## Scope & Name Lookup

## [Pointers](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Pointers.html)

```c
int ival;
double darray[5];

```

- ival has type int; we say &ival is a `"pointer to int."`
- darray has type double[5]; we say &darray is a `"pointer to an array of five doubles."`
- darray[3] has type double; we say &darray[3] is a `"pointer to double."`


### Pointer Arrays

### Pointer to pointer

- `A T *` points to a **`T`**.
- `A T **` points to a **`T *`**.


### [void pointers](https://wikipedia.org/wiki/Void_type)
**`void *`** is needed in `C` to allow generic programming and type‑independent memory operations in language. For example; void * is the type returned by malloc and calloc. So it works for any type with void pointer.

```c
// Allocate memory for 5 integers
void *raw = malloc(5 * sizeof(int));
if (!raw) return 1;

int *arr = (int *)raw;
//...

free(arr);

```

### [Function Pointers](https://wikipedia.org/wiki/Function_pointer)

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
## [Dynamic Memory Management](https://wikipedia.org/wiki/C_dynamic_memory_allocation)

### [malloc](https://man7.org/linux/man-pages/man3/malloc.3p.html)

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

### [calloc](https://man7.org/linux/man-pages/man3/calloc.3p.html)
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

### [realloc](https://man7.org/linux/man-pages/man3/realloc.3p.html)

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

### [free](https://man7.org/linux/man-pages/man3/free.3p.html)

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


## [Structures](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Structures.html)
A struct in C is a  user-defined data type grouped together under one name.
Its members can be of different data types (_unlike arrays_).

```c
struct Person {
    char name[50];
    int age;
    float height;
};

int main() {
    struct Person p1;

    // Assign values
    strcpy(p1.name, "Alex");
    p1.age = 25;
    p1.height = 1.75f;

    printf("Name:\t%s\n", p1.name);
    printf("Age:\t%d\n", p1.age);
    printf("Height:\t%.2f\n", p1.height);

    return 0;
}
```

## [Unions](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Unions.html)
A `union` is like a struct, but all members share the same memory location. This means:
- A union can store only one member at a time
- Size of union = size of its **largest member**
- Writing to one member affects all others (because they `overlap in memory`)
```c
union Data {
    int ival;
    float fval;
    char cval;
};

int main() {
    union Data Dval;

    Dval.ival = 26;
    printf("Dval.ival = %d\n", Dval.ival);

    Dval.fval = 3.14;
    printf("Dval.fval = %.2f\n", Dval.fval);

    Dval.cval = 'A';
    printf("Dval.cval = %c\n", Dval.cval);

    return 0;
}
```

## [Enumarations](https://cppreference.com/w/c/language/enum.html)

* `Basic Enum` Example
    ```c
    enum Day {
        MONDAY,
        TUESDAY,
        WEDNESDAY,
        THURSDAY,
        FRIDAY,
        SATURDAY,
        SUNDAY
    };
    
    int main() {
        enum Day today = SATURDAY;
        printf("Today is day number: %d\n", today);
        return 0;
    }
    ```
* Enum with `Custom Values`
    ```c
    enum ErrorCode {
        OK = 0,
        WARNING = 1,
        ERROR = 5,
        CRITICAL = 10,
        NOT_FOUND = 404
    };
    
    int main() {
        enum ErrorCode status = NOT_FOUND;
        printf("Status code: %d\n", status);
        return 0;
    }
    ```
* Using Enum in a `switch`
    ```c
    enum TrafficLight {
        RED,
        YELLOW,
        GREEN
    };
    
    int main() {
        enum TrafficLight light = GREEN;
    
        switch (light) {
            case RED:
                printf("Stop!\n");
                break;
            case YELLOW:
                printf("Get Ready!\n");
                break;
            case GREEN:
                printf("Go!\n");
                break;
        }
    
        return 0;
    }
    ```
## [Bitwise Operations](https://wikipedia.org/wiki/Bitwise_operations_in_C)

## [C String Handling](https://wikipedia.org/wiki/C_string_handling)

## [C Signal Handling](https://wikipedia.org/wiki/C_signal_handling)

* ❌ `SIGKILL` cannot be handled, caught, ignored, or blocked
* ❌ `SIGSTOP` cannot be handled either.

This is a rule of Unix/Linux systems — no C program can override this. These two signals are designed to always work, even if the process is misbehaving.
**`SIGKILL`** immediately stops (`kills`) the process — the **kernel** does not let your program run anything in response.

| Signal Number | `Name`    | Meaning         | `Catchable?` |
|---------------|---------|------------------|-------------|
| 9             | SIGKILL | Kill immediately | ❌ No       |
| 19            | SIGSTOP | Stop immediately | ❌ No       |

```c
// Signal handler function
void handle_signal(int sig)
{
    printf("\nReceived signal %d : ", sig);

    switch (sig) {
        case SIGINT:  printf("SIGINT\t(Ctrl + C)\n"); break;
        case SIGTERM: printf("SIGTERM\t(termination request)\n"); break;
        case SIGABRT: printf("SIGABRT\t(abort)\n"); break;
        case SIGFPE:  printf("SIGFPE\t(floating point exception)\n"); break;
        case SIGSEGV: printf("SIGSEGV\t(segmentation fault)\n"); break;
        case SIGILL:  printf("SIGILL\t(illegal instruction)\n"); break;
        case SIGQUIT: printf("SIGQUIT\t(Ctrl+\\)\n"); break;
        case SIGTSTP: printf("SIGTSTP\t(Ctrl+Z)\n"); break;
        default:      printf("Unhandled signal\n"); break;
    }

    // exit on specific signals
    if (sig == SIGTERM || sig == SIGINT) {
        printf("Exiting program...\n");
        exit(0);
    }
}

int main() {
    printf("Process ID: %d\n", getpid());
    printf("Waiting for signals... Press Ctrl+C to exit.\n\n");

    // List of signals we want to catch
    int signals_to_catch[] = {
        SIGINT, SIGTERM, SIGABRT, SIGFPE,
        SIGSEGV, SIGILL, SIGQUIT, SIGTSTP
    };

    int count = sizeof(signals_to_catch) / sizeof(int);

    // Register each signal handler
    int iter;
    for ( iter = 0 ; iter < count; ++iter) {
        if (signal(signals_to_catch[iter], handle_signal) == SIG_ERR) {
            perror("signal");
        }
    }

    // Keep program alive to receive signals
    while (1) {
        pause();  // wait for signal
    }

    return 0;
}
```

| Signal Number | `Name`      | Meaning                                      | `Catchable?` |
|---------------|-------------|----------------------------------------------|------------|
| 1             | SIGHUP      | Hangup detected                              | ✔ Yes      |
| 2             | SIGINT      | Interrupt (Ctrl+C)                           | ✔ Yes      |
| 3             | SIGQUIT     | Quit (Ctrl+\)                                | ✔ Yes      |
| 4             | SIGILL      | Illegal instruction                          | ✔ Yes      |
| 5             | SIGTRAP     | Trace/breakpoint trap                        | ✔ Yes      |
| 6             | SIGABRT     | Abort                                        | ✔ Yes      |
| 7             | SIGBUS      | Bus error                                    | ✔ Yes      |
| 8             | SIGFPE      | Floating‑point exception                     | ✔ Yes      |
| 9             | SIGKILL     | Kill immediately                             | ❌ No      |
| 10            | SIGUSR1     | User-defined signal 1                        | ✔ Yes      |
| 11            | SIGSEGV     | Segmentation fault                           | ✔ Yes      |
| 12            | SIGUSR2     | User-defined signal 2                        | ✔ Yes      |
| 13            | SIGPIPE     | Broken pipe                                  | ✔ Yes      |
| 14            | SIGALRM     | Alarm clock                                  | ✔ Yes      |
| 15            | SIGTERM     | Termination request                          | ✔ Yes      |
| 16            | SIGSTKFLT   | Stack fault (Linux specific)                 | ✔ Yes      |
| 17            | SIGCHLD     | Child stopped/terminated                     | ✔ Yes      |
| 18            | SIGCONT     | Continue executing                           | ✔ Yes      |
| 19            | SIGSTOP     | Stop the process                             | ❌ No      |
| 20            | SIGTSTP     | Stop (Ctrl+Z)                                | ✔ Yes      |
| 21            | SIGTTIN     | Background read from TTY                     | ✔ Yes      |
| 22            | SIGTTOU     | Background write to TTY                      | ✔ Yes      |
| 23            | SIGURG      | Urgent condition on socket                   | ✔ Yes      |
| 24            | SIGXCPU     | CPU time limit exceeded                      | ✔ Yes      |
| 25            | SIGXFSZ     | File size limit exceeded                     | ✔ Yes      |
| 26            | SIGVTALRM   | Virtual alarm clock                          | ✔ Yes      |
| 27            | SIGPROF     | Profiling timer expired                      | ✔ Yes      |
| 28            | SIGWINCH    | Window size change                           | ✔ Yes      |
| 29            | SIGIO       | I/O now possible                             | ✔ Yes      |
| 30            | SIGPWR      | Power failure                                | ✔ Yes      |
| 31            | SIGSYS      | Bad system call                              | ✔ Yes      |

## [C Process Control](https://wikipedia.org/wiki/C_process_control)

## Severals
- [cJSON](https://github.com/DaveGamble/cJSON) - Ultralightweight JSON parser in ANSI C.
- [Doxygen](https://doxygen.nl/) -  Doxygen is a widely-used documentation generator tool in software development.

## Compiler/Debugger
- [MSVC & GCC & Clang](https://github.com/cybersecurity-dev/PowerShell-Toolkit/#install-c-cpp) - installation step of MSVC/GCC/Clang compiler in **Windows**
- [GCC & Clang](https://github.com/cybersecurity-dev/Bash-Toolkit/#install-c-cpp) - installation step of GCC/Clang compiler in **Linux**
- [OnlineGDB](https://www.onlinegdb.com/) - **Online** compiler and debugger for C/C++

## 

### My Other Awesome Lists
You can access the my other awesome lists [here](https://cyberthreatdefence.com/my_awesome_lists)

### Contributing
[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

### Contributors
[Thanks goes to these contributors](https://github.com/cybersecurity-dev/awesome-c-programming-language/graphs/contributors)!

[🔼 Back to top](#awesome-c-programming-language-)
