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


## Pointer Arrays

## Pointer to pointer

- `A T *` points to a **`T`**.
- `A T **` points to a **`T *`**.


## [void pointers](https://wikipedia.org/wiki/Void_type)
**`void *`** is needed in `C` to allow generic programming and type‑independent memory operations in language. For example; void * is the type returned by malloc and calloc. So it works for any type with void pointer.

```c
// Allocate memory for 5 integers
void *raw = malloc(5 * sizeof(int));
if (!raw) return 1;

int *arr = (int *)raw;
//...

free(arr);

```

## [Function Pointers](https://wikipedia.org/wiki/Function_pointer)

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
## Dynamic Memory Management

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

## Enumarations

## Bitwise Operations

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
