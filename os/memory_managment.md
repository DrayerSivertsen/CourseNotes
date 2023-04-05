# Memory Management
https://eecs.wsu.edu/~cs460/mem.pdf

Virtual address used by program
Physical address used by computer

Highest memory locations are used for input/output registers

## Memory mapping hardware
1. translate/map vitual address to physical address
2. check permissions, do you have access to this memory location (protection)

Co-processer, has registers
c1 - control register, specifies configuration of MMU
c2 - translation table base register, points to the base of the table
c3 - domain access control register, additional level of control (not in newer versions of ARM)
c4 - not currently used
c5 - fault status register, domain and type of access attempted when abort occurred
c6 - fault address register, hold virtual address of the access when fault occurred
c7 - controls the caches and the write buffer
c8 - TLB operations register, used to invalidate TLB entries
c9 - accesses the cache lockdown and TCM region register on some ARM board equipped with TCM
c10 - the TLB lockdown register

when program starts memory management is off, it must be turned on

smaller pages sizes make memory more efficient, but must add two level mapping (from 1mb to 4000kb)

ID mapping, mapping virtual address to real address, can be done in assembly or C code

segfault is a memory management error, die with 11 code = segmentation fault

ps to show active processes, then kill -11 5902 to kill the process with a segmentation fault
kill -8 = floating point exception

kill: send a signal to a process

A process cannot ignore the kill -9 signal

## Typical C errors that generate kill
dereferenced illegal pointer

# Memory Management
In a real system when you kfork(filename) new process to run filename, we allocate a Umode image memory by the filename size

In the kernel we are developing we assume that the first 8MB are already in use, therefore free memory begins at 8MB to 128MB
New allocated memory is allocated from the free memory area

Kernel occupies 0MB to 8MB. The kernel must build a data structure to map where the holes in free memory are (available free memory)

Look for the first hole space large enough for the new allocation, add the request to the HIGH end of the hole

First fit algorithm performs the best over best fit and worst fit

The algorithm starts with them allocated contiguously however when processes die holes form and thus the hold algorithm becomes important

Compaction of the holes is extremely difficult and time consuming, thus not used

## Releasing Memory
case 1: no adjacent hole
case 2: has a hole on the left or has a hole on the right
case 3: has holes on BOTH sides

In the freeMem list, there should be NO adjacent holes, each hole is of maximal size

mallac() and mfree() allocate memory in heap area (not kernel)
if you need more heap area goes to kernel and asks for 8MB more


## Fork
fork() creates a process identical to parent
child process has different Umode image however they are identical

non 0 pid we have the parent

```
if (pid){
    // parent execute
}
else {
    // child execute
}
```

Book chpt 7

## EXEC
Runs a new image for the current process overwritting the previous image of the parent

If the new image is larger than the current space we will have to return the image location to the freelist and move to a large enough area


Steps:
1. fetch combline from Umode space
2. tokenize cmdline to get cmd filename
3. check cmd file exists and is executable; return -1 if fails
4. load cmd file into process Umode image area
5. copy cmdline
6. reinitialize