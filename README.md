# Troodon-2-Klipper
This is a Klipper configuration for the Troodon 2.0.

For a full video walkthrough on how to switch your Trooodon 2.0 over to Klipper, please refer to the YGK3D YouTube channel (https://www.youtube.com/watch?v=Mjz8hzR5_DE).

If you'd like to support my work, consider joining me on Patreon: https://www.patreon.com/user?u=80746241

After installing Klipper on a Raspberry Pi, follow these instructions.

Instructions:

1) Download both files.
2) Put the firmware.bin file on a blank FAT32 formatted SD card.
3) Rename the printer configuration file to printer.cfg.
3) Open the bottom of the printer and remove the existing SD card from the motherboard.
4) Insert the new SD card and power on the machine
5) Plug the printer into the Raspberry Pi using a USB cable (port is at the back of the machine).
6) Open a web broswer and type the print host path in the url bar (e.g. troodon2.local).
7) Upload the printer.cfg file (overriding the existing one).
8) Restart the firmware.
9) Enjoy Klipper on the Troodon 2.0.


Input Shaping Instructions:

1) Power off printer.
2) Unplug LCD screen.
3) Connect ADXL345 accelerometer to the motherboard via the LCD ribbon cables (see images for wiring reference).
4) Comment [display], [neopixel btt_mini12864] and [delayed_gcode setdisplayneopixel] sections of printer.cfg.
5) Uncomment [adxl345] and [resonance_tester] sections of printer.cfg.
6) Restart firmware.
7) Power on printer.
8) Send ACCELEROMETER_QUERY in the console to ensure that acceleromter is connected correctly.
9) Send TEST_RESONANCES AXIS=X in the console.
10) Send TEST_RESONANCES AXIS=Y in the console.
11) Uncomment [input_shaper] section of printer.cfg and update with the identified shaper parameters.
12) Comment [adxl345] and [resonance_tester] sections of printer.cfg.
13) Uncomment [display], [neopixel btt_mini12864] and [delayed_gcode setdisplayneopixel] sections of printer.cfg.
14) Power off printer.
15) Disconnect accelerometer.
16) Reconnect LCD.
17) Power on printer.
18) Optional: Refer to Klipper documentation for how to generate shaper graphs.
19) Enjoy ringing-free prints.

Note: Sending CALIBRATE_SHAPER will test the resonances of X and Y in sequence and automatically append the shaper parameters to the end of config.g, making step 11 redundant.
