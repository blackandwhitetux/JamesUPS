# Leonardo based 12v DC/DC UPS with LifePO4 battery and current monitoring

Based on https://github.com/abratchik/HIDPowerDevice by Alex Bratchik.



![Schematic](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/schematic.png)
![Gerber render 2D](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/gerber_render.png)
![PCB Render 3D](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/board_render.png)
![Board photo](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/serial_number_0001.jpg)

A work in progress...

This design is for a 12v adjustable voltage output UPS using the following items:

* Arduino Pro Micro
* XL6009 boost converter
* XL4005 buck converter
* 2x INA180A2IDBVR current sense chips
* 2x FQP30N06L N channel MOSFETS for switching the battery and output

Pro Micro I/O pins as follows:

![MCU Pinouts](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/mcu_pinout.png)


### Additional setup step on Linux hosts

Copy linux/98-upower-hid.rules file to the /etc/udev/rules.d/ folder , then reboot. This is required for

Linux device manager (udev) to recognize the Arduino board as UPS. 
