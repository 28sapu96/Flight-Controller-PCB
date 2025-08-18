# Flight-Controller-PCB
A FC design with 3 interconnected boards, each with 2 layers. This is a prototype design, I just went through the first iteration and there were significant problems that I need to solve in the next version. This repository is just a way for me to keep track of my progress.

**TOP BOARD**
The top board contains the logic and a GNSS module (ATGM336H-5N31). During flight and programming, data is fed into the ESP32 via I2C, UART, Serial, and SPI interfaces. Currently, the ESP32 works, and does respond to computer signals, but I haven't gotten the GNSS Module to work yet. To load program into the ESP32, the BOOT button must be held down during power up. When programming for the first time, both the RST and BOOT button must be held down. There are 2 output headers on this layer, for SPI and Serial communication.

**MIDDLE BOARD**
This board houses all the output headers for 5V power, 3V3 power, the signal, and it houses the sensors (Accelerometers (ICM-42688-P), Gyroscopes (ICM-42688-P), & a barometric pressure sensor (BMP-388). This board was also supposed to have a 12v to 3V3 step-down converter, but I messed up somewhere and it is 4.2V instead, which is higher than the threshold voltage for both sensors (3.6V), so I ended up frying everything. The data from the sensors goes up to the top board through header pins, and the signals come down from the top board into the bottom board and out through the header pins. 

**BOTTOM BOARD**
This board has all the power systems required. The previous design had a 12-36V to 5V converter (@ 5A), and 12V pads to distribute power from the main battery to all the ESCs. The new design now has a 12-36V to 3V3 converter on the bottom along with the aforementioned features. 
