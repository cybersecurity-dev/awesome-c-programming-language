# [Signal Handling](https://wikipedia.org/wiki/C_signal_handling)

## Linux Signal Handling

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