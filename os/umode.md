# User Mode

Chapter 7 in OS book

```
// copy cmdline to high end of Ustack in Umode image
```
needs to be modified to make use of two MB area

The first fork of a process upon starting up the OS takes place using kfork before user mode has taken place. After this all calls will be fork instead as it is Unix/Linux compatible and standard for a user to use.

## kfork
kernel fork system call, takes place by copying the parent process image and stack for the child process to use in its own location

