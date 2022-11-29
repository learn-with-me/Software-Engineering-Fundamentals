# Arduino

> Arduino is a brand name. Most of their hardware and software is open source. The schematics are available online, so if you don't want to purchase a ready-made product, you are free to buy individual components and make it on your own.

The Arduino is a full development system, or prototyping system. It includes a complete circuit board and support hardware to help make using the microcontroller easier.  Some things that the Arduino provides to help you out:

* **Voltage regulators :** help provide clean, stable power.
* **Timing oscillators :** There is a 16MHz quartz crystal oscillator to give the USB controller an accurate, stable time base; and a 16MHz ceramic oscillator for the main microcontroller clock.
* **USB interface :** allows you to plug the Arduino into your PC to download your programs.  It can also provide power to the Arduino. Includes the USB connector, a USB controller \(which is a separate microcontroller\), transmit/receive status LEDs, and the 16MHz timing crystal.
* **Power Plug :** to plug into a wall adapter for power.
* **Reset switch, and a test output LED :** Convenient items to include on a prototyping board.
* **Stackable "headers" :** these rows of connectors make it easy to plug in additional add-on daughter boards \(called "Shields"\).  These allow you to easily expand and customize the features of the Arduino.

##### Official Documentation

    Arduino Programming Language
    https://www.arduino.cc/en/Reference/HomePage

    Getting Started Guide
    https://www.arduino.cc/en/Guide/HomePage
    https://create.arduino.cc/getting-started

    Arduino Project Hub
    https://create.arduino.cc/projecthub?f=1

    Editor (IDE)
    https://create.arduino.cc/getting-started                // Web Editor
    https://www.arduino.cc/en/Main/Software                  // Desktop Editor
    https://processing.org/                                  // IDE & Programming language is based on `Processing`

##### Connectivity

Arduino can operate

1. Independently \(like a robot\)
2. Connected to a computer \(thereby extending its capability like sensor data from outside world, etc\)
3. Connected to other Arduino\(s\), electronic devices and controller chips

##### Cost

An official complete Uno board costs $25, and a clone Uno as little as $4.

##### Arduino Hardware

```
Arduino UNO
Arduino Mega - Chip ATmega2560
Arduino Micro - Chip Atmega32u4
Arduino MKR1000 - Chip 32-bit ATSAM ARM

Arduino Compatible: Make sure
1. The chip is either Atmel ATmega328 or Atmega328P
2. There are headers for plugging wires into
3. It runs at 5V (check the product documentation)
4. It has a USB-serial chip on board, such as FT232, FT231x, PL2303 or CP2102/CP2103/CP2104 which are the most popular
    and a USB plug

Adapter
Any adapter. Center positive and 7-12VDC output. 9VDC is recommended.
Arduino are fairly rugged and can survive upto 20V accidentally.
```

##### Projects to refer

```
http://www.bakertweet.com/
https://create.arduino.cc/projecthub/lagsilva/digital-clock-with-mirrored-display-driven-by-accelerometers-b2651b
https://diyhacking.com/arduino-motion-sensor-tutorial/
Large DC Motor https://www.youtube.com/watch?v=OW-Bf3yjUyE
```



