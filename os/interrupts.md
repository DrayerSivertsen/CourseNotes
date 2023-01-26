# Interrupts

Controllers - Primary and secondary are responsible for determining when an interrupt occurs and which interrupts take priority.

MKI provides support for mours and PS/2 compatible keyboard

For I/O devices a common practice of the computer is to check the status when an interrupt occurs. 

On IBM compatible keyboard the input is not ASCII it is scan code, this is then converted to ASCII through software mapping table.

Underneath every keyboard everything is the same, English, French, Japanese. The mapping table is what changes to accomodate for the language.

## Key Mapping Table
Converts scan code to ASCII
Table has mappings for all shifted keys and unshifted keys

In the driver code a state machine is used to determine if shift is pressed or not. This replaces the key mapping table accordingly.

KBD driver: 
Has two sections
* portion for hardware
* protion for software

KBD -> Interrupt handler -> buffer -> getc() -> Process
Lower-half -> input buffer and control variables -> upper-half

For output devices reverse the roles

Keyboard clock determines the frequency of char when you hold down a character button


## Interrupt handling functions
* IQR handler call the handler in c and return the stack 
  * Interrupt occurs head to IQR handler
  * vicstatus value is checked
  * if keyboard value was sent then head to keyboard handler
* Lock and unlock used to stop and receiving of interrupts


## kbd.c file (keyboard driver)
Define structure intended for multiple copies, holds all the information about device (base, buf, data, room)

initialize data to 0, room to 128

When you get a key you update the data and room.
Input to buffer head
Output from buffer tail
FIFO buffer

### kbd_init
construct keyboard struct
initialize data and room
set the base register

### kbd handler
* get scan code
* check the bit to tell if a key was pressed or released
* our code sends bit when key is pressed 
* place the character at head of buffer (increment, if over 128 reset to 0)
* update room and data (could add condition for if room is 0)

### kgetc
* keep interrupt enables with unlock
* check if data is 0
(if we had a process it would go to sleep)
* if a character set to lock
* gets char from tail and inputs to c
* updates data and room
* unlocks again

### kgetc
* gets characters from string until emtpy

Ctrl + c = kill process
Ctrl + d = end of file

Very important interrupt commands

### Homework
To get cursor to flash every second turn on or off every half second



(normal keyboard also sends for release)
Normal keyboard driver sends message for press and release to handle inputs like holding shift or holding a char. 



