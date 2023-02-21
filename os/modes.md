# Handling Modes

tswitch is in kernel mode

IRQ handler - puts it in IR mode, then restores the previous mode after execution


Modes:
* user mode
* SVC mode
* kernel mode
* IR mode


General Rule: If you go to kernel mode you may not come back right away

kps() - prints all the proc structures in the kernel

user mode access cannot perform I/O, 
1. security issues if all users can tamper with I/O devices
2. user mode also does not contain the necessary drivers to handle I/O

to perform I/O just switch to kernel mode handle the get/put char and then switch back to user mode

in user space I/O should be handled by the kernel