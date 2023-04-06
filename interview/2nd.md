# 2nd Round Interview with Apple

# Leetcode question
Input a phone number, return the first found duplicate number in the phone number


# Questions I have
Is the interrupt handler a process that is always running in the background?
single CPU system handles the interrupt, it is important for the running process to stop what it is doing and handle the interrupt. It is possible that the interrupt is meant for a previous process in which case the running process handles the interrupt by waking up the desired process. 

It handles interrupts all the way to usermode space?
Running process will handle interrupt to usermode space and wherever else is necessary

What clears the registers when switching processes?
The registers are cleared by reading the registers to the process stack. This saves the registers so they can be read back into the registers when the process becoming the running again. 

However there is some optimization by using link registers where when the current process is switched the registers values can be saved for a one time switch (A,B,C A switches to B, B returns to A) but this is dismissed when more than one process switch occurs (A,B,C A switches to B, B switches to C).

link registers is a copy  of the registers it makes switching processes quick

Deadlock and starvation



ARM trying to use all tricks to speed up operations

ARM new version architecture, his new book comes out in summer

new security 

switch process and entire table no need to switch entire kernel table always the same

user mode stack is what changes