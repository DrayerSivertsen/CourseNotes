# Last 460 Assignment

P0 handling iterrupt handler for password login, all other processes are sleeping and waiting for login

login: root
passsword: 12345

when a command is run it locates the command in the bin directory, forks a child to run the command, the child runs the command and wakesup the parent when the program is complete

```test``` runs a test program output

You can make any new .c files and then run them in your shell
```mku test``` compiles the program to a binary and stores it in bin

piping is also handled ```ls /bin | more``` shows one page at a time of bin

replace KC init and login with our own 
fork multiple logins, where each one will be its own terminal
the login process then obtains three file descriptors stdin, stdout, stderr

2, 3, 4 are the primary children of P1
P1 is on the QEMU waiting for child processes, P2, P3, P4 all waiting for login

interrupt handler handled by P0

what is serial port (serial port interrupt handler)


# Lab 7
Two different buffer calls
1. Get the whole block in 
2. Get partial block and modify before writing back

bp in dev list = write a search function in dev list

We have to write the code for getblk and brelse (in pseudo code) all other code is given

Everytime you get a block implement the requests by 1, if in dev list increment hits by 1

emacs @4200

needed pts/1
make new terminal and us ps to verify pttys/1

```
A TTY (TeleTYpewriter) is a physical or virtual device that allows a user to enter and receive data through a terminal. The term "TTY" is often used interchangeably with "terminal".

A PTS (pseudo-terminal slave) is a type of virtual terminal that emulates a hardware terminal. It is created by a program called a "pseudo-terminal master" and provides a bidirectional communication channel with the master. The master and slave terminals are connected by a pair of virtual TTY devices, named /dev/ptmx and /dev/pts/N (where N is a number).

The PTS (pseudo-terminal slave) is used by many programs in Linux to provide a terminal-like interface to users, even if the program doesn't have a built-in terminal. For example, if you use an SSH client to connect to a remote server, the remote server will create a PTS for your SSH session, allowing you to interact with the server through a terminal interface.
```

