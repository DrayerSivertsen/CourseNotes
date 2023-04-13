# Operating System Level Questions

## What is the difference between page table and stack for a process?


## Is the interrupt handler a process that is always running in the background? 
single CPU system handles the interrupt, it is important for the running process to stop what it is doing and handle the interrupt. It is possible that the interrupt is meant for a previous process in which case the running process handles the interrupt by waking up the desired process.

## It handles interrupts all the way to usermode space? 
Running process will handle interrupt to usermode space and wherever else is necessary

## What clears the registers when switching processes? 
The registers are cleared by reading the registers to the process stack. This saves the registers so they can be read back into the registers when the process becoming the running again.

However there is some optimization by using link registers where when the current process is switched the registers values can be saved for a one time switch (A,B,C A switches to B, B returns to A) but this is dismissed when more than one process switch occurs (A,B,C A switches to B, B switches to C).

link registers is a copy of the registers it makes switching processes quick

Deadlock and starvation

ARM trying to use all tricks to speed up operations

# ARM new version architecture, his new book comes out in summer

new security

switch process and entire table no need to switch entire kernel table always the same

user mode stack is what changes


# x86 architecture that is translated for the ARM architecture?
We write the code and develop on the Linux x86 architecture. This code is then cross compiled to run on the ARM architecture.

# How are mouse drivers different than keyboard?
Typically in embedded operating systems there is no need for a mouse driver as terminal support through keyboard is the most common. Thus the professor has not dived into the workings of a mouse driver.

Do mouse research on your own.

# What pieces existing in the operating system that we have not gone over?
How to combine io devices with files you need to link the file descriptor to devices. TO BE TALKED ABOUT IN CLASS

# What is the difference between operating system and embedded operating system?
The main difference between a general-purpose operating system and an embedded operating system is their design focus. General-purpose operating systems, such as Windows or macOS, are designed to run on a wide range of computer hardware and support a wide range of applications. They are typically larger and more complex than embedded operating systems and offer a broader range of features and functionality.

Embedded operating systems, on the other hand, are designed to run on specific hardware platforms with limited resources, such as memory and processing power. They are typically smaller, faster, and more efficient than general-purpose operating systems and are optimized for specific tasks and applications. They often have real-time processing capabilities, which means they can respond quickly to input and produce output in a predictable and timely manner.

