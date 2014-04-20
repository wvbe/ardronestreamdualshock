AR Drone Steam DualShock
=============
##Prerequisites
Nodejs, Gulp, Compass

##How to install stuff
Linux users may have to install a few additional libs for a dependency, node-hid (it connects to USB devices for you), to work:
```
sudo apt-get install libudev-dev
```

Ubuntu versions missing libusb.h:
```
sudo apt-get install libusb-1.0-0-dev
```

Then, after cloning this repository, you can:
```
npm install
```

Before running, you may want to connect your AR Drone to the same (wireless enabled) network your PC is on, instead of connecting your computer to the drone's hotspot. Telnet to your drone and type into BusyBox:
```
echo iwconfig ath0 mode managed essid NAME_OF_YOUR_NETWORK > /data/ap.sh
echo ifconfig ath0 192.168.1.1 netmask 255.255.255.0 up >> /data/ap.sh
echo route add default gw 192.168.1.254 >> /data/ap.sh
chmod 755 /data/ap.sh
```

Now every time your drone reboots, telnet to the drone again and run:
```
/data/ap.sj
```

##How to run stuff

Gulp tasks do most of the stuff

```gulp server``` - Runs the Dualshock, AR Drone, Dronestream and Express servers

```gulp watch``` - Runs the LiveReload server (use in combination with Chrome extension) and watch for SASS/Jade changes

```gulp once``` - Compile all SASS and Jade once

```gulp``` - Default, run all of the above

Now, once you have gulp (```gulp server``` at minimum) running, browse your ass to http://localhost:5555. There is a socket.io server on port 8082, Express on 5556 (for static files) and dronestream on port 5555 (also serves the index.html)

Note: You may require root privileges to access the DualShock controller through USB, if so, run ```sudo gulp```

##Tested with
* Parrot AR 2.0 Drone
* Dualshock 3 controller (CECHZC2E)
