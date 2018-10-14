# hpwirelesstest

Test purpose not commercial

# Installation

    Compile the driver with: gcc -o kbdusb kbdusb.c
    Copy kbdusb and hp_keyboard.sh to /usr/local/bin
    Copy 85-hp-keyboard.rules to the udev rules directly, on Ubuntu 16.04 anf higher, it is /lib/udev/rules.d/
    reload udev rules with: udevadm control --reload-rules
    and it should work...

# If not working

Ubuntu have the uinput device at /dev/uinput, it seems that some Linux distro have it at /dev/uinput/uinput, just change the path in the source it if your case. I found it useful to modify the udev rule line calling the script like:

ATTRS{idVendor}=="17ef", ATTRS{idProduct}=="609b", RUN+="/bin/bash -x /usr/local/bin/hp_keyboard.sh 2> /tmp/kbd.trace  &"

Look at the trace file if you can identify what is causing the error. Finally, you can enable the DEBUG variable in the source and recompile. With debug, you can run the lenovo_keyboard.sh script in foreground.

Thanks
