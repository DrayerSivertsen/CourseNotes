# Handling Modes

tswitch is in kernel mode

IRQ handler - puts it in IR mode, then restores the previous mode after execution


Modes:
* user mode
* SVC mode
* kernel mode
* IR mode


General Rule: If you go to kernel mode you may not come back right away

kps() - prints all the proc structures in the kernel

user mode access cannot perform I/O, 
1. security issues if all users can tamper with I/O devices
2. user mode also does not contain the necessary drivers to handle I/O

to perform I/O just switch to kernel mode handle the get/put char and then switch back to user mode

in user space I/O should be handled by the kernel

## User Mode
Operations
* getpid()
* getppid()
* ps()
* chname()
* switch()

all operations are performed with syscalls, identified by a relative number (and optional parameters)

for a small number of parameters arm puts the parameters in registers instead of stack
stack takes memory and registers are faster, with more than 4 they begin to be put on the stack

DO NOT pass more that 4 parameters because you will be slowing down the program

system calls go to kernel, therefore all the user mode operations are handled by the kernel syscalls


swi #0 - used to switch from kernel mode to user mode

by adding user mode and switching to kernel mode to execute commands (syscalls) we are working towards full blown file system

