# Raspberry Pi

**Power**

Pi3 is powered by +5.1V micro USB supply. Current requirement depends on what you connect it to. In general 2.5A power supply provides you ample current to power the Pi. Model B typically uses 700-1000 mA. Model A can use as little as 500 mA.

##### Hardware Required

```
Raspberry Pi
Micro SD card (atleast 16 GB)
Power supply (ateast 2Amp)
Display + Cable to connect to your display
Keyboard + Mouse (get a wireless or a USB hardware)
```

##### Setup

```
NOOBS           # OS Installer https://www.raspberrypi.org/downloads/noobs/
Raspbian        # Operating System

First things first. Install NOOBS on the SD card
Plug-in the card in Raspberry Pi, connect the display and power supply.
The moment you connect the power supply, the Pi will boot up.

https://www.raspberrypi.org/documentation/setup/
```

##### Connecting to a screen

```
Option 1:
Connect your monitor using HDMI cable. If your monitor does not support HDMI connection, you may have to buy adapter.

Option 2:
You'll need option 1 to start temporarily.
In your raspberry Pi, go to Home -> Preferences -> Raspberry Pi configuration
This opens up a panel. Navigate to "Interfaces" tab, enable "VNC" and click OK.
You'll see VNC server icon on top right. Click on it to find out the IP to connect to. Do NOT enable WiFi.
Note down the IP address to connect, from the VNC server. Now you can disconnect your monitor.

Laptop: Connect your Pi with your laptop using an Ethernet cable.
All you have to do is install VNC client and enter the IP to connect to the screen. You should be all set!
```

##### Documentation

```
https://elinux.org/R-Pi_Troubleshooting
https://www.raspberrypi.org/downloads/noobs/
https://www.element14.com/community/welcome
```

##### Tutorials

```
https://www.youtube.com/watch?v=IbKY-n71XCE
https://www.youtube.com/watch?v=wdHgvrRozlQ
```

##### Projects

```
https://www.youtube.com/watch?v=ZszlVVY1LXo
https://www.youtube.com/watch?v=ZtQyOvrW_K8
```

##### Ordering Resources

```
https://www.gearbest.com
https://www.aliexpress.com/
```

##### 



