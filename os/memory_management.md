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