# Interprocess Communication

## Semaphores
Work similar to a pipe, for sending and receiving messages

int spinlock // used for multi processor systems

### P
flag register to hold the current status 
copy to semaphore

### V
paste from semaphore

Semaphore allows a process to get whole lines instead of just a char
Solves the problem of process communication

When writing to mbuf must lock, then lock again when reading from mbuf

# Send and Receive Message
Utilize P and V to handle lock and unlock for writing to mbuf asynchonously

Every process has a message queue associated with it, when a process wants to receive a message the message is held within its own message queue.

Midterm 3 - add code to see who is sending/receiving in the message process

Modify the PROC structure: 
message queue ~ add linked list of message structure - start with null
semaphore ~ start with zero - no message yet, keeps track of messages in the queue

