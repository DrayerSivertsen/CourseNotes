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

