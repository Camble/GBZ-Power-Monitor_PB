# GBZ-Power-Monitor V1.0 by Popcorn

This is a Power Management utlity for the Gameboy Zero project.  This adds graceful shutdowns and automatic low battery alerts when the battery level is low.  This is meant to be used in concert with the Gameboy Zero hardware and Retropie 3.7+ environment.

Required Hardware and Components
--------------------------------
- Raspberry Pi Zero (or Model B+, Raspberry Pi 2 and Pi 3)
- Adafruit Powerboost 1000C
- Pololu Mini Slide Switch LV or Pololu Mini Push Button LV
- 2N3904 NPN transistor
- 47k resistor
- A mini SPDT or DPDT latching push and hold switch
- Original DMG (or equivalant) SPDT Slide Power Switch

Dependancies
-----------
- Retropie 3.7+
- Python 2.7 and Python Module RPi.GPIO (comes installed with Retropie 3.7)
- omxplayer (comes installed with Retropie 3.7)
- Must be run as a sudoer user (the default Pi user on Retropie 3.7 is a sudoer)

Wiring Diagram
-------------
![alt tag](http://i.imgur.com/FpPDcmK.png)
Notes

- The built-in slide switch on the Pololu switch in the diagram must be flipped into the off position to work
- If using the alternate Pololu Mini Push Button LV, just map UART TX to the CTRL pin instead of the On pin
- the 2nd VOUT & GND from the Pololu switch (labeled Video DC) can go to the power strip from Wermy's latest guide number 4
- In the latest wiring video guide number 4 by Wermy, he wires the main power switch to be closed when OFF, this needs to be inverted for the Pololu switch.  Use the other pin on the switch which closes when ON.  These will be mapped to the A and B pins of the Pololu switch instead

Installation
-----------

You will need to connect the PI Zero to Wifi and from another computer on the same WiFI network, SSH in (or use Putty on PCs):

```
ssh pi@retropie.local
```

Default password is 'raspberry'.  Next at the command prompt, copy this monitor and the video assets with the following command:

```
cd ~;git clone https://github.com/NullCorn/GBZ-Power-Monitor.git
```

Now, launch the Monitor manually and test that it's working properly
```
python ~/GBZ-Power-Monitor/gbz_power_monitor.py
```

Once you are satified that the monitor behaves properly, add the monitor to the startup process to complete the installation

```
echo "@reboot     /usr/bin/python ~/GBZ-Power-Monitor/gbz_power_monitor.py" >> mycron; crontab mycron;rm mycron
```

Video Examples
--------------
https://www.youtube.com/watch?v=TRkEfD04unk
Low Battery Warning

https://www.youtube.com/watch?v=nRJ42oSrIg4
Power Switch test

Links
-----
More detail can be found on this thread:

http://sudomod.com/forum/viewtopic.php?f=8&t=97

Contact
-------
Questions, Comments, Kudos, Free Beer to abandonedemails@gmail.com. Please put "sudomod" somewhere in the subject or your message will not be received.
