# User Interface
Chapter 8

## init
P0 is handcrafted, P0 creates P1 with user mode image code. 

Use file descriptors to open device for IO, open with read (fd 0) and write (fd 1).

device char identifier of console (allows for read/write to screen)
tty0


ttyS0 uart

Are all devices IO each tied to a IO driver
ttyS1, ttyS2

using printf before initialization of devices doesnt not print to anywhere

```
exec("login /dev/tty0") // executes the login sequence for the tty0 console
```

# What is a serial port?
```
A serial port is a physical communication interface through which data is transmitted serially, one bit at a time. An OS serial port refers to the software interface provided by the operating system to interact with a serial port on a computer.

In most modern operating systems, the serial port is treated as a file, similar to other input/output devices. The operating system provides a device driver that communicates with the serial port hardware and provides a standard interface for applications to send and receive data.
```

## Login 

When checking a user and password if either is incorrect the program finds that it is invalid and returns a failed login. 

On a real system the passwords are encrypted so to check the password the program encrypts your attempted password and checks it to the saved encryted password for a user. 

if a valid account is found the program changes the uid, gid, usr home directory
each user can have a different home directory

Finally you exec the program for the user account. In our examples we run the sh (shell)

Some gaming computers have users that login directly to a game

name : password : uid : gui : home directory : starting program

Our program will add multiple console to login multiple users

lp = line printer

fd = floppy disk

tty0, ttyS0, ttyS1 are all special


# Dev driver

## Console
write to screen using vid.c driver and reads from keyboard using keyboard driver

## Serial ports
writes to different serial ports using uart.c driver
stored in uart[] array is the serial port ex (tty)


