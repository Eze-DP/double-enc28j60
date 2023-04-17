# double-enc28j60
Drivers for having a second enc28j60 port on a raspberry pi. 

# Integration
Add the .dtbo file to your /boot/overlays directory in the raspberry pi. 

If needed, use the .dts file to make modifications. Use the following command to get a .dtbo file: 

sudo dtc -I dts -O dtb -o /boot/overlays/enc28j60-spi1.dtbo enc28j60-spi1-overlay.dts

# Example of use 
Modify the config.txt file in /boot to contain the following lines:

dtparam=spi=on
dtoverlay=enc28j60,spi0-cs1,interrupt=25 
dtoverlay=enc28j60-spi1
dtoverlay=spi1-1cs,cs0_spidev=off,cs0_pin=16

The GPIOs will be: 

SPI0: 
MOSI - GPIO10
MISO - GPIO9
SCLK - GPIO11
INT - GPIO25
CS - GPIO8

SPI1:
MOSI - GPIO20
MISO - GPIO19
SCLK - GPIO21
INT - GPIO26
CS - GPIO16

# Why? 
Using this library it is possible to either make a multi-port managed router or network switch on the raspberry pi with the enc28j60 chip. 

