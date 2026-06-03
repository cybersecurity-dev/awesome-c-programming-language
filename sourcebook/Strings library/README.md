# Strings library

| **Byte string** | **Wide string** | **Description** |
|------------------|------------------|------------------|
| `strcpy`         | `wcscpy`         | Copies one string to another |
| `strncpy`        | `wcsncpy`        | Writes exactly *n* bytes/characters, copying from source or adding nulls |
| `strcat`         | `wcscat`         | Appends one string to another |
| `strncat`        | `wcsncat`        | Appends no more than *n* bytes/characters from one string to another |
| `strxfrm`        | `wcsxfrm`        | Transforms a string according to the current locale |

## Null-terminated byte string

### String Manipulation

* `strcpy` : 👉 `Copies one byte string into another`
    ```c
    char dest[20];
    strcpy(dest, "Hello World!..");
    printf("%s", dest);       // Output: Hello World!..
    ```

* `strncpy` : 👉 `Copies exactly n characters`
    ```c
    char dest[20];
    strncpy(dest, "Hello World!..", 5);
    dest[5] = '\0'
    printf("%s", dest);       // Output: Hello
    ```

* `strcat` : 👉 `Appends a byte string to the end of another`
    ```c
    char dest[20] = "Hello;
    strcat(dest, " World!..");
    printf("%s", dest);       // Output: Hello World!..
    ```

* `strncat` : 👉 `Appends no more than n characters`
    ```c
    char dest[20] = "Hello;
    strncat(dest, " World!..", 6);
    printf("%s", dest);       // Output: Hello World
    ```

## Null-terminated multibyte string



## Null-terminated wide string

### String Manipulation

* `wcscpy`: 👉 `Copies one wide string into another`
    ```c
    wchar_t dest[20];
    wcscpy(dest, L"Hello World!..");
    wprintf(L"%ls", dest);    // Output: Hello World!..
    ```
* `wcsncpy`: 👉 `Copies exactly n characters`
    ```c
    wchar_t dest[20];
    wcsncpy(dest, L"Hello World!..", 5);
    dest[5] = L'\0'
    wprintf(L"%ls", dest);    // Output: Hello
    ```
* `wcscat`: 👉 `Appends a wide string to the end of another`
    ```c
    wchar_t dest[20] L"Hello;
    wcscat(dest, L" World!..");
    wprintf(L"%ls", dest);    // Output: Hello World!..
    ```

* `wcsncat`: 👉 `Appends no more than n characters`
    ```c
    wchar_t dest[20] L"Hello;
    wcsncat(dest, L" World!..", 6);
    wprintf(L"%ls", dest);    // Output: Hello World
    ```