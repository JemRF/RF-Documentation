---
title: Blynk Integration
keywords: interface, integrate, integration, blynk
last_updated: Sep 28, 2020
tags:
summary: "This page explains how to integrate our RF Modules with the Blynk app"
sidebar: mydoc_sidebar
permalink: blynk.html
folder: mydoc
---

Paul's Wasteland
This blog is a dumping ground for small how-to guides I want to write. At work and at home I am always solving problems that do not seem to be documented anywhere on the Internet, although I often find others asking the same questions. So hopefully some of the information I put on here will be found by such people and be of some help. This will mainly involve things around Linux, Open Source software, Debian, Ubuntu, Android, Arduino, Raspberry Pi, Asterisk PBX.....

Wednesday 14 January 2015
Building your own firmware for Ciseco XRF modules (CC1110 System on a Chip) in Linux
In this post are my notes on what was required to write, compile and upload my own firmware to a Ciseco XRF module which is based on a TI CC1110 chipset.

An XRF module is an X-Bee shaped radio device that is designed for adding low power radio communication to things like Arduino or a Raspberry Pi:

http://shop.ciseco.co.uk/xrf-wireless-rf-radio-uart-serial-data-module-xbee-shaped/

I have used them in my own home automation applications, they are very simple to use.  With the firmware you can get from Ciseco they will act as simple serial-to-radio devices allowing something like an Arduino to communication wirelessly with other devices.

Since the XRF module uses a TI CC1110 system-on-chip module (which contains an 8051 CPU, a radio transceiver and some other bits and pieces), it is a microcontroller in it's own right.  You can get firmware from Ciseco which will take readings from temperature probes or active a relay and a few other uses:

https://github.com/CisecoPlc/XRF-Firmware-downloads

I was interested in writing my own firmware for the XRF module, there are some instructions on the Ciseco website:

http://openmicros.org/index.php/articles/81-xrf-projects/144-xrf-building-firmware-with-sdcc

But they are using the developer tools that Texas Instruments (who make the chip) provide and they seem to assume that everyone uses Windows, which I do not.

It took a fair bit of Googling, trial and error and experimentation but I now have a fully working setup for compiling my own firmware and burning it into the memory of an XRF module.


A Word Of Warning
Over-writing the Ciseco supplied firmware with your own is irreversible.  Once you've done this you will never be able to load a Ciseco firmware back onto the module.  It is possible that Ciseco will do this for you if you post the module back to them but they may not be interested in doing that.  I'd imagine it will void any warranty.

You have been warned!

Hardware needed
Assuming you want to continue, here's what I am using.

A Ciseco XRF module.  So far I've only done this with an older v1.5 XRF module as I had a spare one lying around.  I don't see why it shouldn't work on newer ones though.  I will eventually be using a newer SRF (surface mount version of the XRF), so I'll update this in time.  If you haven't got one, buy one from Ciseco - link to their shop is above.
Prototyping board (aka 'breadboard'), a selection of jumper wires, an LED and a resistor of value at least 100ohms.  All this can be supplied by the likes of Farnell or Maplin Electronics or even just from ebay if you don't have them already.
XRF break-out board.  This isn't essential but highly recommended as the XRF has 2mm spaced pins and wont fit into a standard breadboard with 2.54mm pins:  http://shop.ciseco.co.uk/xbbo-break-out-board-for-xbee-shaped-modules/
CC-Debugger.  This is the device for burning the firmware onto the XRF module (or any compatible microcontroller).  It is made by Texas Instruments but fortunately it's quite cheap in comparison to the development kits for some other microcontrollers:  http://shop.ciseco.co.uk/texas-instruments-cc-debugger-iar-compiler/ or http://uk.farnell.com/texas-instruments/cc-debugger/debuggerprogrammer-for-rf-soc/dp/1752232?ost=cc-debugger

Connecting to the CC-Debugger
There's just a few wires needed to connect the XRF module to the cc-debugger.  Here is a diagram showing the connections I used:



Note that the ten-pin connection is shown as you are looking at the end of the ribbon cable with it connected to the cc-debugger, pin one is bottom left).  The debugger itself will supply power (from pin 9) to the XRF and the level select pin so no other power source is needed.
I set this out on my breadboard and ended up with this:



The wire colours in my photo match my diagram above.

Using the CC-Debugger from Linux
At this point you are supposed to install a Windows-only toolkit to use the cc-debugger.  After a bit of searching I did find code that someone has written to allow the debugger to be used from Linux and it's hosted on github.  Use git to download the source and then build it like so:
git clone https://github.com/dashesy/cc-tool.git
cd cc-tool
./configure
At this stage it may say you have some of the build tools or libraries (such as libusb-1.0.0-dev) missing.  Just use your Linux distribution's standard package search and installer tools to install the requirements.  In Debian Wheezy I needed:
libusb-1.0.0-dev
libusb-1.0.0
libboost-all-dev
pkg-config
Then compile and install it:
make
make install
Test it is working with the CC-Debugger connected using the USB cable and wired to the XRF module as above by simply issuing the cc-tool command like so:
sudo cc-tool
Sudo is needed for libusb access on my computer.  You should see this:
Programmer: CC Debugger
Target: CC1110
No actions specified
Which means it has detected both the CC-Debugger and the CC1110 chip you have connected to it!  If you see "no target detected" then you probably don't have the XRF module wired up correctly.
You'll also see the LED on the cc-debugger go green when it is connected correctly to the XRF module.

Compiling code
Next, you want to be able to write code, compile it and burn it to the memory of the XRF module.
The "Small-Devices-C-Compiler" (SDCC) is used for this.  Simply install the sdcc package from your Linux distribution's package installer.
In Debian I noticed that there is a package called "cc1111" which says it is a fork of sdcc with improvements for TI 8051-based RF SOCs, which includes the CC1110.  I used this package and it works well.  It seems to be a drop-in replacement for sdcc.
sudo apt-get install cc1111
 Then the command "sdcc --version" will show you something like:
paul:~$ sdcc --version
SDCC : mcs51 2.9.0 #5416 (Jun 30 2012) (UNIX)

Hello World
When learning a new programming language, the first thing to do is to write a "hello world" program.  The equivalent when trying out a new microcontroller is to blink an LED.
Here is some c code which I wrote to do this:
#include <cc1110.h>

void delay(int msec) {
  int i,j;

  for (i=0; i<msec; i++)
    for (j=0; j<1000; j++);
}
void main(void) {
  P0DIR |= 0x01;
  P0_0 = 0;

  while (1) {
    P0_0 ^= 1;
    delay(1000);
  }
}
Firstly, this includes the libraries for the cc1110 chip.  Then it defines a simple function to delay the CPU for a small amount of time (it's not very accurate but a decent enough example for this).  It's not a million miles off milliseconds.  Then there is a main function which is what gets executed when the XRF boots up.
The pins of the cc1110 are grouped into "ports" which can have 8 pins in each one.  The first port is P0 and P0 can have pins P0_0 to P0_7.  Note that not all pins are present on the cc1110 and even less are broken out to a physical pin on the XRF module.  The documentation on the Ciseco website shows which pins you can access.  In my example I am using P0_0 which is the first pin of port 0 and equates to pin 12 of the XRF module (2nd from bottom on the right hand side from the top of the module).
P0DIR sets the direction of the pins on port 0, I'm setting the first pin to 1 here using a bitmask which means P0_0 will be an output.  This is essential because all pins are inputs by default.  Then I set the level of P0_0 to 0 to turn the pin off.
The while loop (which will just run forever), toggles pin P0_0 from 0 to 1 and back using a bitwise XOR and then calls the delay function to wait for approximately one second.  This will cause the LED to flash slowly.
With an LED and a suitable current limiting resistor (100ohms or higher) wired up to P0_0, I ended up with this:




Compiling the code
Now to cross-compile the c code for the 8051 architecture and generate an Intel hex file which can be burnt to the XRF module.  This is what sdcc will do.  I used the following 'make' file that I found on the Internet and edited a bit:
#
# CC Debugger - Example Payload
# Fergus Noble (c) 2011
#
CC = sdcc
CFLAGS = --model-small --opt-code-speed
LDFLAGS_FLASH = \
 --out-fmt-ihx \
 --code-loc 0x000 --code-size 0x8000 \
 --xram-loc 0xf000 --xram-size 0x300 \
 --iram-size 0x100
ifdef DEBUG
CFLAGS += --debug
endif
SRC = test.c
ADB=$(SRC:.c=.adb)
ASM=$(SRC:.c=.asm)
LNK=$(SRC:.c=.lnk)
LST=$(SRC:.c=.lst)
REL=$(SRC:.c=.rel)
RST=$(SRC:.c=.rst)
SYM=$(SRC:.c=.sym)
PROGS=test.hex
PCDB=$(PROGS:.hex=.cdb)
PLNK=$(PROGS:.hex=.lnk)
PMAP=$(PROGS:.hex=.map)
PMEM=$(PROGS:.hex=.mem)
PAOM=$(PROGS:.hex=)
%.rel : %.c
 $(CC) -c $(CFLAGS) -o$*.rel $<
all: $(PROGS)
test.hex: $(REL) Makefile
 $(CC) $(LDFLAGS_FLASH) $(CFLAGS) -o test.hex $(REL)
clean:
 rm -f $(ADB) $(ASM) $(LNK) $(LST) $(REL) $(RST) $(SYM)
 rm -f $(PROGS) $(PCDB) $(PLNK) $(PMAP) $(PMEM) $(PAOM)
Save this into a file called "Makefile" in the same folder as your c code - which needs to be in a file called test.c.  You can reuse this Makefile by changing the source file name and other places the filenames appear.
To compile your code simply type "make" in the same folder as your c code and Makefile.
You'll end up with a few files generated.  The important one will be called "test.hex".  This is the firmware to load onto the XRF module.
Use cc-tool to upload to the connected XRF module with this command (note, this is the point of no return, once you've ran this your XRF module will no longer work with any standard Ciseco firmware files):
sudo cc-tool -v -e -w test.hex
That's it, your LED should now be flashing!


Paul Hayes at Wednesday, January 14, 2015
Share
20 comments:

Bi0H4z4rD15 August 2015 at 12:52
Your schematics are wrong. DD and DC are pins 3 and 4, and NOT 5 and 6

Reply

Paul Hayes17 August 2015 at 09:42
You were quite right, a mistake in the diagram. I have updated this to show the correct connections.

Reply

Unknown2 September 2016 at 08:04
This is really excellent information. Especially useful following the demise of CISECO/WirelessThings due to problems with the parent company.

Richard
Reply

Paul Hayes2 September 2016 at 09:05
Hi. Yes it's a real shame these aren't going to be available any more. I have asked them if they would be interested in open sourcing the firmware code you can download binaries for here:

https://github.com/CisecoPlc/XRF-Firmware-downloads

That would be great. To be fair, the SRF module they sold isn't that complicated a design and the TI CC1110/CC1111 SoC is readily available, I am considering making my own boards.

I've messed about with ESP8266 modules and while they are easy to work with, they use a *lot* more power than the CC1110, you couldn't run one off a CR2032 coin cell for several years (or at all!) like I do with some of my XRF modules running as temperature sensors.

Reply

Unknown20 November 2016 at 20:14
Great article. I've also been looking for a replacement for the SRF which I use. Do you think you instructions will work on something like this: http://www.ebay.com/itm/1PCS-CC1101-wireless-module-Long-Distance-Transmission-Antenna-868MHZ-/191745832339?hash=item2ca4f13593:g:3DUAAOSwp5JWVRp5

Also do you have any more source code?

Reply

Paul Hayes21 November 2016 at 11:58
Hi, I think the device in that ebay link probably would work.

I've got more source code here:

https://github.com/hayesey/srf_lightswitch

Consider it experimental only though.

Reply

Unknown22 November 2016 at 04:38
Impressive, thanks for sharing that. Where did you learn about programming the CC1101?

Reply

Paul Hayes22 November 2016 at 09:24
mostly by reading the TI CC1110 datasheet PDF which is on the texas instruments website:

http://www.ti.com/product/CC1110-CC1111/technicaldocuments

But I also got a lot of help from reading the code others had written for the same chip such as:

https://github.com/tobyjaffey/cctl


Reply

Unknown22 November 2016 at 12:38
I see that's a link to a bootloader for the CC1110/CC1111. Do you know of there is a bootloader for the CC1101 that can load the .bin files from WirelessThings (CISECO)?

Reply

Paul Hayes22 November 2016 at 12:46
Unfortunately the Ciseco bootloader was their own which they never released in any shape or form. I know once you've written your own firmware to a Ciseco XRF/SRF etc... then you will never be able to put a Ciseco firmware on it ever again. Unless someone figures out their bootloader but I suspect it requires some kind of encryption key in order to use it.

Reply

Paul Hayes22 November 2016 at 12:48
and of course, you wont be able to put their firmwares onto that other device. Which is a real shame. Essentially their firmware is useless to you for anything other than an XRF/SRF bought from them. This is to protect their IP (since it's easy for someone to copy the hardware) but unfortunately makes it difficult to keep using existing systems now they've gone out of business.

Reply

Unknown4 December 2016 at 23:25
I had success with the LED blink tutorial, also using a couple XRF's I had. However I can't get your lightswitch program to work. It gets stuck on the transmit. Did you you manage to get it working? Would be good just to find a simple "hello world" transmit and receive example somehwere.

Reply

Paul Hayes5 December 2016 at 13:24
it works for me yes, I'm using that code in a couple of desk lamps to remotely control them. What are you using to burn the firmware? I use the proper cc-debugger, never tried it with anything else.


Reply

Unknown5 December 2016 at 16:55
I have a cc-debugger that I got from TI, but I used the windows version of SDCC. Perhaps it's your makefile that included some compiler config that I haven't applied. I'll try SDCC on my Raspberry Pi as per your instructions. Thanks for your feedback and help, much appreciated!

Reply

Unknown6 December 2016 at 03:10
After using the Linux compiler and your makefile it works well! Now you and I are the last ones keeping the LLAP flag flying!

Reply

Unknown25 December 2016 at 00:53
Looking at the register settings in radio_init() the transmission frequency seems strange. The following settings configure the radio to 940mhz.

FREQ2 = 0x24;
FREQ1 = 0x2D;
FREQ0 = 0x24;

However the XRF's i use are all 868mhz.

Did you get the register settings in radio_init() from CISECO?




Reply
Replies

Paul Hayes22 November 2017 at 15:55
there's definitely something I've got wrong or misunderstood in the RF registers. According to what I read and SmartRF, the frequency settings should be:

FREQ2 = 0x24;
FREQ1 = 0x2D;
FREQ0 = 0xDD;

But when I use those settings, I see no traffic coming from my existing Ciseco XRF/SRF modules.

If I change the settings to:

FREQ2 = 0x24;
FREQ1 = 0x2D;
FREQ0 = 0x24;

Then it starts working. So even though those settings don't seem right, they seem to work for me.

Since then I have tried to figure out the settings to put the radio down to 1.2kbaud (ATDR3 in the Ciseco serial settings). I've been unable to get this to work though.



Paul Hayes23 November 2017 at 16:36
I've re-worked all the rf register settings now and have also borrowed a windows laptop in order to use SmartRF Studio to compare with.

I have pushed an update to my github repo. My settings now match what comes out of smartrf.

https://github.com/hayesey/srf_lightswitch/blob/master/firmware/radio.c

I am having problems getting 1.2k working though, 250k is fine.

I have a feeling it might be interference as I have several systems using 868mhz here now (I am also playing around with Lorawan devices). So I will test more back at home where I have nothing else using 868mhz but my XRF/SRF network.

Reply

Paul Hayes29 December 2016 at 14:10
hmm, I am wondering if I made a typo there as by my reckoning it should be 0xDD, 0x2D, 0x24. Strange that it works though. I can't remember how I got those numbers now. I need to solder another of my test boards together and mess around with it.

Reply

uDude3 March 2021 at 23:02
Even in 2020, excellent infos. Hard find sdcc examples program ti cc chips with 8051. Thank you.

Reply