# LCD Driver

int fbuf[480x640] 
4-byte integers = |byte3|R|G|B|
The three primary colors red, green, and blue can be combined to make any color
then number of pixels

VGA: Video Graphics Array

For a vga resolution it has 480 x 640 pixels. 
The hardware will take the memory picture and render it. 
Left top corner is 0x0 first location we start
Mailman algorithm to get accurate locations
fbuf[index]:  index = y*640 + x
vid driver is the LCD driver that registers to VGA mode

4KB - 1MB programs can be written for our OS
2MB and larger is defined as our buffer area

‘Volatile’ keyword in c: It is used to inform the compiler that the variable value can be changed any time without any task given by the source code.

Each display image files are compressed and it is very complex to uncompress them using an algorithm.

BMP is Microsoft image type and we will use it because it is not compressed

It is also the only image type that is made from bottom → up
BMP images are stored upside-down, the image is made from the bottom up
Every three bytes is a pixel and the pixel color is defined by the value of the three bytes

BMP picture has a header than contains the width and height
The row size of an image always need to be a multiple of 4 similar to 360 (entry length)
Convert the three color bytes into one integer
If your increment p with rsize the image will be inverted
Font is a bit pattern of the ascii letter
16x8 is the standard font size for terminal
32x16 is a larger scale of the font
For a font x = col*8, y = row*16

Pointer in buf area to beginning of display, to scroll simply move the pointer and all of the display moves

In our case we will use a primative way just by moving all the lines up by ones through copying.

Our task is to display the same font but twice the size

Linux drivers come out by Linux developers reverse engineering a barely working driver. Then they wait until the manufacturer gives up and gives the information for users to make a strong working driver.


Current program:
* prints upsidedown
* incorrect colors
* scale is too big

Correct the display
half size, take every other row, column take every other pixel

Font: a bitmap pattern of an ascii character
Font is a picture of a character that is made up

Character is 8x16 bits

‘<<’ and ‘>>’ shifts bits a certain number of spaces

To display a font twice the size, for every 1 or 0 bit display the row and column twice
First try switching 16 - 32 and the 8 - 16

## IO by interrupt

Memory management unit - translates the virtual memory address to physical memory address

Tells the user what device is where in the memory map

Vector table - memory table that contains pointers. If something occurs it points to the location to go. 

Two modes that deal with interrupts:
* IRQ - interrupt request
* FIQ - fast interrupt request

Interrupt controller is a hardware device, close to CPU

PIC - primary interrupt controller

Timers are very important so they are given priority. 

“Topdog” is the request with the highest priority, if two requests are made a “dogfight” box occurs and the highest priority is sent while the other is suppressed. 

Secondary controller (SIC) is for the lowest requests. The highest request in the secondary controller is brought to the 31 place in the primary controller.

The highest request is sent to the CPU

CPU has internal register called flag register, if the bit is masked out (0 bit) the CPU ignores the request. If the bit is open (1 bit) the CPU takes the interrupt and handles it using the vector table. 

Operating system can not function without timer, every VM has several timers. Timer0 and Timer1 share the same clock, Timer2, and Timer3 share the same hardware clock.

Timer is nothing but a crystal oscillator, temperature can cause drift and affect the timer speed.  
One application of a system timer is to display the curser using ascii 27 (rectangle box) and flash the box on and off every 0.5 sec

stmfd sp!, {r0-r12, lf} // store multiple fd registers into stack

bl IQR_handler  // handle the IQR request instructions (call c code)

 // return back and load

‘knowledge you learn today will become obsolete tomorrow, its important to learn the principle not the specific hardware’

What is the first byte in a pixel for?