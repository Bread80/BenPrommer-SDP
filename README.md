Enhanced Software for the Ben Eater Breadboard EEPROM Programmer
================================================================

More details in my article at http://bread80.com/?p=222

Code for an EEPROM programmer based on Ben Eater's breadboard design !!!with a few changes!!!

* Also includes code to deal with Software Data Protection (SDP) on, e.g. the 28C256 - either to disable, enable, or program while enabled.

* I've done some optimisation to the code to it's a whole heap faster: programming a full 32Kb EEPROM takes about 15 seconds. 

I've removed most of the explicit delay() calls as my chip didn't seem to need them. YMMV. I've left them in but commented out in case you have problems. There's also a few calls to change the CHIP_EN line which the datasheet seems to imply they are needed but I've got along fine without them. Again they are there but commented out in case you need them.

And for a final bonus, there's some code to program an enhanced version of Ben's 8-bit to 4x 7 segment display decoder: Updated to strip leading zeroes. Updated to display the minus sign immediately to the left of the number. 

This code has only been tested against a single ATMEL 28C256 chip bought from eBay, so it could be anything.

This code should be easy to modify to program NORFlash chips. They use similar command sequences (see the DisableSDP and WriteEEPROMSDP functions). For NORFlash 'erase' routines, calling writeWait with 0xff should work for the operation wait delay. You might need to increase the maximum 'timeout'.

Hardware changes: 
Connect /OE and /CE to the Arduino, move /WE to a different Arduino pin - see #defines for details. (The connection from the 74HC595 to /OE of the EEPROM is no longer needed).
And also some 0.1uF decoupling capacitors - the code is /very/ unreliable without them!!

Based on original code by Ben Eater

Modifications by Mike Sutton - Bread80.com





