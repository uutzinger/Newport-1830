# New Port 1830
Newport Power Meter, Serial Communcation
This software was written because the averaging function on the power meter can not be set to very slow averaging. I needed to average data over at least 2 seconds.
The 3rd party NI driver was written for GPIB communcation and I needed serial communcation.

## Requirements
LabView software development platform.
You will need to connect the powermeter with a serial cable to the host computer. 
You will need a serial port such as the 9 pin RS232 port. You can purchase USB to serial adapaters.  
The serial cable can **not** be a Null Modem cable and will need to have two female ends.  
To test the cable make sure that pin 2 (RX) and pin 3 (TX) are connected to the same pin on both ends of the cable. Make sure that pin 5 is also connected to pin 5 (GND).
The 1830-C only works at 9600 baud. Set Bad 9600 and 8 bit, no parity and 1 stop bit in the device manager of your computer.

## Installation and Usage
Attach the serial cable.  
Open putty or a terminal program that has ability to connect to a serial port.  
Open correct serial port (e.g. COM10). Your device manager will list all the serial ports. Usally serial port COM0 and COM1 are internal ports and if you use an USB to serial adapter it will start at COM3 or higher.  
Type U? and hit enter in the terminal. You should receive a response like "1" followed by a new line. If you dont receive a response, you have a connection problem.  

Copy the software to a folder and open the example Power Meter Control Panel.
Start the labview program.
You can read current setings or change the settings. You can read one value or you can read continous values. The original software has filter/conversion functions which are undocumented and not necessary to operate the power meter.

## Credits
This program is based on the 3rd party labview driver on the NI driver website.
It was modified to work with VISA serial port and the communication routines were changed to use minimal delays, continously reading data until a New Line character is received.
A chart display was added and the averaging software was updated using a ringbuffer.

## Updates
If your powermeter communicates at speeds higher than 9600 you should try 115200 (The 1830-C lists higher commmunication speeds, but they dont work). The data transfer rate is limitted by the serial communcation speed. For regular measurements I achieve about 30 readings per second, for short text transmissions (e.g. low powers) I achieve 50-60 readings per second. If youy have ability to transmitt faster you might want to search the delay functions,especially the ones in the float query function and use lower values.

Urs Utzinger 2020
