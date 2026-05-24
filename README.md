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
- [Dynamic Memory Management](#dynamic-memory-management)
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
* **`Function Declarations`**: A function can be declared several times in a program, but `all declarations` for a given function must be compatible;
    * the return type is the same
    * the parameters have the same type. 
    ```c
    float square(float x);
    ```
Function declarations do not `allocate storage`.

* **`Function Definitions`**:
    ```c
    float square(float x) {
        return x*x;
    }
    ```

## Type Conversions

## Arrays

## Scope & Name Lookup

[🔼 Back to top](#awesome-c-programming-language-)

## [Pointers](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Pointers.html)

```c
int ival;
double darray[5];
```

- ival has type int; we say &ival is a `"pointer to int."`
- darray has type double[5]; we say &darray is a `"pointer to an array of five doubles."`
- darray[3] has type double; we say &darray[3] is a `"pointer to double."`

You can find more details at the [**link**](https://github.com/cybersecurity-dev/awesome-c-programming-language/blob/main/notebook/C%20language/Declarations/Pointers.md)

[🔼 Back to top](#awesome-c-programming-language-)

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

### [calloc](https://man7.org/linux/man-pages/man3/calloc.3p.html)
```c
#include <stdlib.h>
void *calloc(size_t nelem, size_t elsize);
```

Allocates memory for an array of num objects of size and initializes all bytes in the allocated storage to zero.

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


### [free](https://man7.org/linux/man-pages/man3/free.3p.html)

```c
#include <stdlib.h>
void free(void *ptr);
```
Releases the specified block of memory back to the system.

You can find more details at the [**link**](https://github.com/cybersecurity-dev/awesome-c-programming-language/tree/main/notebook/Dynamic%20memory%20management)

[🔼 Back to top](#awesome-c-programming-language-)

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
[🔼 Back to top](#awesome-c-programming-language-)

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
[🔼 Back to top](#awesome-c-programming-language-)

## [Enumarations](https://cppreference.com/w/c/language/enum.html)

An enumeration (enum) is a user-defined data type that lets you assign names to integer constants.

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

## [Bitwise Operations](https://wikipedia.org/wiki/Bitwise_operations_in_C)

## [C String Handling](https://wikipedia.org/wiki/C_string_handling)

### String Manipulation

| **Byte string** | **Wide string** | **Description** |
|------------------|------------------|------------------|
| `strcpy`         | `wcscpy`         | Copies one string to another |
| `strncpy`        | `wcsncpy`        | Writes exactly *n* bytes/characters, copying from source or adding nulls |
| `strcat`         | `wcscat`         | Appends one string to another |
| `strncat`        | `wcsncat`        | Appends no more than *n* bytes/characters from one string to another |
| `strxfrm`        | `wcsxfrm`        | Transforms a string according to the current locale |

### String Examination

### Miscellaneous

[🔼 Back to top](#awesome-c-programming-language-)

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

[🔼 Back to top](#awesome-c-programming-language-)

## [C Process Control](https://wikipedia.org/wiki/C_process_control)

[🔼 Back to top](#awesome-c-programming-language-)

## Severals
- [cJSON](https://github.com/DaveGamble/cJSON) - Ultralightweight JSON parser in ANSI C.
- [Doxygen](https://doxygen.nl/) -  Doxygen is a widely-used documentation generator tool in software development.

[🔼 Back to top](#awesome-c-programming-language-)

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

### License
[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

[🔼 Back to top](#awesome-c-programming-language-)
