# Propagator Thermostat
Single-channel temperature monitor with output to control a relay powering a propagator heater element.

Requires:
- The [GPIO Library](https://code.google.com/p/raspberry-gpio-python/) (Already on most Raspberry Pi OS builds).
- The [Flask web server](https://www.raspberrypi.org/learning/python-web-server-with-flask/worksheet/). Install command:
  - sudo apt-get install python3-flask
- A [Raspberry Pi](http://www.raspberrypi.org/).
- Hardware with [MAX31855 temperature monitors](https://www.maximintegrated.com/en/products/analog/sensors-and-sensor-interface/MAX31855.html).
- Hardware to control a heater element. In my case this was a propagator with a faulty control unit re-wired to drive the relay from the Raspberry Pi.

Installation:
- Copy files to a folder on the Raspberry Pi.
- Edit /etc/rc.local to autorun application:
   - sudo nano /etc/rc.local
   - Add: python /home/pi/.../propagator.py where ... is the location of your file.
- Edit config.xml to define your system hardware. The defaults match my hardware.
    
Recommendations (to make life easier):
- Set a [static IP address](https://www.modmypi.com/blog/tutorial-how-to-give-your-raspberry-pi-a-static-ip-address).
- Define a [hostname](http://www.simonthepiman.com/how_to_rename_my_raspberry_pi.php).
- Create a [fileshare](http://raspberrypihq.com/how-to-share-a-folder-with-a-windows-computer-from-a-raspberry-pi/).
- Install [VNC](https://www.raspberrypi.org/documentation/remote-access/vnc/) for full headless access.

## Use

See wiki.

## Changelog

### V1.4
Added log of min and mix propagator temperature measurements

### V1.3
Added timed temperature schedule, e.g. to allow different day/night temperature profile

Removed ability to set the temperature from the web page

### V1.2
Added proportion of time heater is on and air temperature to log

### V1.1
Modified display to use the last value measured for heater control

Added calibration for main sensor

### V1.0
Added store and display of heater state

### V0.4
Added ability to set temperature and right back to file (so that after restart the set temperature is unchanged)

### V0.3
Added read of temperature from text file

### V0.2
Corrected code to run threading

Updated config to match my hardware build

### V0.1
Initial trial code.

Supports one temperature monitoring channel. While I have re-used code from a multi-channel temperature logger, it is not currently intended that this code drives more than one propagator however it is likely that the way the code has been written that it would work.

MAX31855 driver modified from https://github.com/Tuckie/max31855.
