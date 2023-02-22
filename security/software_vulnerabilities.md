# Software Vulnerabilities
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