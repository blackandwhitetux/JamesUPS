# Leonardo based 12v DC/DC UPS with LifePO4 battery and current monitoring

Based on https://github.com/abratchik/HIDPowerDevice by Alex Bratchik.

A work in progress... 

This design is for a 12v adjustable voltage output UPS using the following items:

* Arduino Pro Micro
* XL6009 boost converter to boost the battery from 6.4v to 12-30v
* XL4005 buck converter to charge the battery more efficiently
* 2x INA180A2IDBVR current sense chips, one for battery and one for output rail
* 2x FQP30N06L N channel MOSFETS for switching the battery and output

## todo (basics):

#### work out how to measure the battery voltage on A0
* nominal 6.4v, min 2v, max (3.65*2) 7.3v
* through a 10k/100k resistive divider so should be 1v - 3.65v if analog in reads 0-1024 for 0-5v

#### work out how to measure the input voltage on A1
* as above, hopefully vrange is from 0-5v as input voltage is 12v

#### work out how to measure the output current on A2
* confirm gain function on INA180A2IDBVR (should be 50v/v) and check high-power resistor used (0.05R) gives sane values
* according to the below link, we should get 5v @ 2A, 2.5v @1A, etc
* https://techoverflow.net/2019/12/17/sense-resistor-current-shunt-current-sense-amplifier-calculator/

#### work out how to measure the battery current on A3 and whether it is functional during charge or discharge
* as above

#### decide how to pwm the battery connection so as not to take all the current from the source
* check battery bms works with pwm or if it needs extra caps


## todo (more advanced)

* adapt my measurement code to Alex's UPS sketch
* implement coloumb counting as we know battery voltage and current and time
* implement anti-brownout based auto reset based on output current draw measurements (configurable by jumper bodge wire?)

## PCB design 0.1

![Schematic](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/schematic.png)
![Gerber render 2D](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/gerber_render.png)
![PCB Render 3D](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/board_render.png)
![Board photo](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/serial_number_0001.jpg)

Pro Micro I/O pins as follows:

![MCU Pinouts](https://github.com/blackandwhitetux/JamesUPS/blob/master/pcb_design/mcu_pinout.png)

## PCB design 0.2

still making changes, ideas as follows:

* bidirectional battery current measurement



### Additional setup step on Linux hosts

Copy linux/98-upower-hid.rules file to the /etc/udev/rules.d/ folder , then reboot. This is required for

Linux device manager (udev) to recognize the Arduino board as UPS. 
