# Buffer Management
https://eecs.wsu.edu/~cs460/IObuffering.pdf

generate buffer by deleting the buffer.o file then calling 

```
mkk buffer
```

P() - locks the semaphore

V() - unlocks/frees the semaphore



write getblk and brelease

copy, read data, write to buffer (before disk)

when buffer is used you need to write out then reuse buffer

## Structures to support buffer management
Device table contains device buffer mapping

Request, and hit are used to define how manytime you find a buffer in the buffer cache

semaphore used to lock/unlock access to the buffer

## Steps of getting buffer
1. Stage a buffer from the free list
2. Check the device list(cache) for buffer
    - if found return if not busy
    - otherwise use staged buffer as new buffer
        - write to the buffer
        - assign it to device list
3. return bp 

## Release buffer
If buffer dirty clear it and add it to the tail of free list
LRU - least recently used (common to maintain order of use)

## IO
READ
- buffer op code is for read
    - get block
    - bp to valid
- buffer op code to write
    - put block
    - bp to invalid

## Delayed write
Make use of buffer instead of always writing directly to disk

Direct read works but is not optimized

bread() is much smarter, checks cache to see if data is already read in a buffer, then indirectly reads/writes

The buffer will hold data at the location and even get written to the buffer area, this can be held and used quickly with the cache and does not need to be written to the disk. 

The problem occurs when a system shuts down before everything has been written back to disk. 
*This can be overcome with a sync, where periodically writes to the disk to prevent too much data from being lost. 

sync goes through buffer cache and writes out all buffers to disk

real user io used paging
system calls use buffers (e.g. ls)

