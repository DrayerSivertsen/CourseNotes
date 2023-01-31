# Operating system

Operating system is simply a software platform to run processes

## Miderm 1

Bunch of proccesses

Ready queue contains all the processes that are ready to run
Only one process can run at one time

The ready queue points to the current process that is running. The process runs then upon completion returns to the body. Ready queue runs FIFO

switch: changes the process

fork: creates a new process

All processes have priority one except process 0 which has priority 0

All kernel commands are done by the current process. So if fork is called the current process makes a child process. 

(Keyboard driver does not handle space or backspace, if command typed incorrectly need to rerun)


Process and program are different. They can run the same code but it is run differently. 
Program is dead meat until the CPU runs it. 

In a real program the processes are adjusted dynamically. Whichever process has run longer (clock time) is switch to lower priority.

### vid.c
IO driver - not needed for the process lab

### kbd.c
keyboard driver - not needed for process lab

### ts.s
Used to start the VM
* prepares the stack
* need a vector for interrupt
* irq_stack to handle interrupts
* in SVC mode (CPU mode) call main to get program running
* tswitch: save information of caller, save process CPU register to stack
* dequeue the top of the ready queue and set to running
* store stack pointer and resume
Functions as a black box, one things comes into tswitch and something else comes out. 
* tswitch code
  * switch box, process calls piece of code
  * controlled way of saving
    * save process information
    * make new process and save information
    * resume as new process
If pocess dies it does to return to ready queue. It dies and becomes a zombie, it will then later be found and buried by the parent. 

MUST BE DONE IN ASSEMBLY (cannot save registers, etc in c)

### t.c
used to help our system copy_vectors

main initializes kernel - at this point no process is running yet
* after completion new process is forked and switched to P1


### kernel.c
Comment of proc struct in file for convenience.

Array of PROC's, linked list of running, freelist, readyqueue, sleeplist

LINKED LIST IS A DOMINATE TYPE STRUCTURE

freelist points to process zero, can see all the processes now
readyqueue is NULL

whatever running points at is the running process

Create P0 using brute force initalize the struct, calls kfork

kfork (to create new process)
take a PROC structure from free list (doesnt matter which)
if p == 0 we have run out of processes (have a finite number of processes)
initialize struct (set parent information)
sets all the registers to zero
save stack pointer in last register (-14)

return to where tswitch was called. Automatically returns to func(body)

### q.c
enqueue function already implemented
put process into queue by priority, FIFO, address must be passed (could be empty)

dequeue
takes the top dog in queue, first one has the highest priority

printlist
prints queue or linked list

### type.h
proc struct:
represents a process, must have this representation. 

pid - personal id number
ppid - parent pid, all process have a parent except P0
priority - priority number
status - free, ready to run, zombie
event - how to sleep, how to die

pointers to parent, child, sibling

stack area 1024 bytes, process has a stack (push, pop all occur here)
if a new process is defined it has a new stack location

### wait.c
functions to implement

INTERNAL SYNCHRONIZATION OF UNIX - sleep, wake

sleep
can be found in 5.6.1, indicate the value you want to sleep on, (ex 1 = printer, 2 = blank)
each proc structure has an event
switch process

wakeup
find if it asleep and call the even to wakeup
only finds calls that are alseep, if interrupt occurs and it is setting the event in sleep but it hasn't been set to sleep it will be missed by wakeup.

sleep perfect in book
wake - little different, 

American way - if event is ready give them all the chance, wake everyone up and see who wins the fight over it, all others back to sleep
china and russia - better efficiency, comprimise depends on location


scheduler
in tswitch after save call scheduler, if ready put yourself in ready queue, if you sleep you are not ready so don't go in queue




## Real queue
includes multiple queues with levels, depending on the amount of CPU runtime it will switch the level of the queue this adjusts the priority

Beginning of chapter 5 is what has been shown