# Memory Management

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

when program starts memory management is off, it must be turned on