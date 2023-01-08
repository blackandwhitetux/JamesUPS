# Leonardo based 12v DC/DC UPS with LifePO4 battery and current monitoring

Based on https://github.com/abratchik/HIDPowerDevice by Alex Bratchik.

![PCB Render](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/ups.png)
![Board photo](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/serial_number_0001.jpg)
A work in progress...

This design is for a 12v adjustable voltage output UPS using the following items:

* Arduino Pro Micro
* XL6009 boost converter
* XL4005 buck converter
* 2x INA180A2IDBVR current sense chips
* 2x FQP30N06L N channel MOSFETS for switching the battery and output

### Additional setup step on Linux hosts

Copy linux/98-upower-hid.rules file to the /etc/udev/rules.d/ folder , then reboot. This is required for

Linux device manager (udev) to recognize the Arduino board as UPS. 
