#Leonardo based 12v DC/DC UPS with LifePO4 battery and current monitoring

Based on https://github.com/abratchik/HIDPowerDevice by Alex Bratchik.

A work in progress.

This design is for a 12v adjustable voltage output UPS using the following items:

* Arduino Pro Micro
* XL6009 boost converter
* XL4005 buck converter
* 2x INA180A2IDBVR current sense chips
* 2x FQP30N06L N channel MOSFETS for switching the battery and output

== Additional setup step on Linux hosts ==
Copy linux/98-upower-hid.rules file to the /etc/udev/rules.d/ folder , then reboot. This is required for
Linux device manager (udev) to recognize the Arduino board as UPS. 

== License ==

Copyright (c) Alex Bratchik 2020. All right reserved.

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
