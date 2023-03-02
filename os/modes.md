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

pg table 2048 

entries in page table start at 2048
```
pgdir[2048] = 0x80032
```

Page table is contiguous virtually but point to physical addresses in different locations

fork, grab new process and initalize it to ready queue. Now we will be adding an additional step of creating the process with a user mode image

When a system call is made from user mode it causes it ot enter the kernel to execute SVC handler, the user mode is saved in a register into empty stack

Stack contains user mode registers and kernel mode registers

# Initalizing kstack for switch between kernel and user mode
1. clear all the "saved" registers to 0
2. set saved ksp to kstack
3. set KLR = goUmode, so that p will resume to goUmode
4. set ULR to VA(0), so that p will execute from VA=0 in Umode
5. set new process usp to point at utack TOP and uspsr to Umode

Every 16mb is a different processes page table

A page table has 4k entries each entry has:
- domain
- kernel rw
pattern of page table: 0x 4 1 2

in newer versions of ARM the domain has been removed

page table entry setting 258 entries because
256 mb of ram + 2 mb of I/O

80000 = 80mb

0xC32 sets the page table entry to be read/writable by user mode process

change p->usp (int*)VA(0x100000); to 2mb

once at virtual address you can locate the physical address using the page table 

on average half of an os memory was used, each allocated memory has a hole on either side now page table allows for contiguous memory.