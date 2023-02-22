# Software Vulnerabilities Part 1
* pervasive

### CVSS 
Score 0 - 10 where 0 is low and 10 is critical 

* CVSS is not popular
    * three versions
        * V2, V3, V3.1
        * each version drastically different from other 
            * requires redoing of previous version scores
    * arbitrary score weights
    * still remains a symbol of being an insider, passion
        * knowing about CVSS will make you stand out in interviews

### Classification
* SW vulnerabilities can be classified into three categories
    * time-induced
    * design-induced
    * implementation-induced
* time-induced
    * as automation increases, our ability to exploit increases
    * hardest to solve, some say unsolvable
* design-induced
    * flaws in a system design, leading to vulnerabilities
    * hard to solve
* implementation-induced
    * errors in implementating a flawless design, leading to vulnerabilities
    * easier to solve


### Memory Stacks
* core of any computer instruction
* X86 memory stack architecture
    * buffers
        * stack: local variables, function parameters
        * heap: dynamic variables e.g. malloc
    * static: common machine code e.g. precursors
    * code: user issued instructions

### Memory Corruption
* corrupt a memory stack by overflowing buffers (stack or heap)
* overflowing

### Potential Attacks
* potential attacks using memory corruption
    * stack-base buffer overflow
    * return address corruption (side effect of overflow)
    * instruction execution order corruption (side effect of overflow)

### Defense
* stack canaries
    * random value added to a stack
    * verify the random value and its location before return
    * proves integrity of the stack's memory registers

canarie: a random number or string

* access control
    * configure
        * code to be rx but not w
        * memory stacks to be rw but not x

* address space layout randomization (ASLR)
    * randomize memory addresses for each execution

inode = index node


# Software Vulnerabilities Part 2

### Input Validation and Representation
* untrusted inputs accepted by programs
    * no input validation
    
### Temporal and State-based
* incorrect assumptions regarding time and state of the program
    * result of complexity due to concurrency and shared system resources
* attacks
    * race condition
    * deadlock
    * reused authentication sessions
### API Abuse
* API - contract between a client and server
    * either party may fail to uphold their part of the contract
* possible abuses
    * malware injection
    * unchecked return value
    * misuse of privilege management
    * string manipulation functions

