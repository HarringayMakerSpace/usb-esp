# How to make a tiny USB powered WiFi Web Server or IoT Device from an ESP8266/Arduino ESP-12S

![Alt text](/doc/Running1.jpg?raw=true "Tiny USB powered ESP-12S")

This shows how to make a little USB powered ESP8266 that can run descretly plugged into USB socket, such as a USB phone charger or power bank, for a cost of just a few pounds.

Have it running as your own little web server, or add sensors to make a tiny IoT device.  

# What you need

![Alt text](/doc/IMAG0607a.jpg?raw=true "Parts")

You need:

1. A USB LED Light

   You can find these from Internet sellers, eg. [Banggood](http://www.banggood.com/0_2W-WhiteWarm-White-Mini-USB-Mobile-Power-Camping-LED-Light-Lamp-p-969441.html) currently have them for less than 50p when buying 3 or more.

2. An XC6206 3.3V regulator

   The SOT-89 package, eg. these for 10 cents each from [AliExpress](https://www.aliexpress.com/item/20pcs-lot-XC6206P332PR-XC6206P332-XC6206-3-3V-SOT-89/32701818048.html)

3. An ESP-12S

   This **must** be the "S" version of the ESP-12. The "S" version has built-in pull-up/down resistors and bypass capacitors so you don't need to add these as external components. Eg. these for £1.89 on [EBay](http://www.ebay.co.uk/itm/New-ESP8266-ESP-12S-Serial-Wireless-WIFI-Transceiver-Sender-Receiver-LWIP-AP-STA-/291971729155)
  
# Assembly

![Alt text](/doc/Assembly.jpg?raw=true "Assembly")

First remove the resistor and three LED's from the USB stick. They come off quite easily heated up with a soldering iron and lifted with a small screw driver. The LED's are wired in parallel with all the bottom pads connected to the USB +5V and the left pad of the resistor connected to the USB GND.

Next solder on the XC6206 regulator. The SOT-89 package format just happens to fit perfectly where the resistor used to be and with the top tag of the regulator on the middle LED pad, with the correct GND and 5V input. A blob of BlueTack helps get it aligned and held in place while you solder it. 

Next, turn the USB stick over and with a couple of drops of super glue stick on the ESP-12.

Finally add a short wires from each side of the XC6206 to the bottom pins on each side of the ESP-12 for the GND and +3V connections. Also, if its going to use deepSleep then add the connection between the ESP-12 pins 16 and Reset (thats the small white wire on the top right in the photo, connected to the top right pin and the 4th pin down).  

Thats it! You can now plug it into a USB socket it will start running.

# Add environment sensor

You can add small sensors on the back, for example, make an environment sensor by adding a BME280 which measures temperature, air pressure and humidity (about £3 from [AliExpress](https://www.aliexpress.com/item/BME280-Digital-Sensor-Temperature-Humidity-Barometric-Pressure-Sensor-New/32659765502.html)).

***Note***, the ESP8266 uses about 70mA when running so gets noticably warm, which will effect the readings of any temperature sensor mounted on the back. To avoid that the ESP needs to use deep sleep most of the time and only wake up briefly to send the sensor readings. I've found it needs to deep sleep for at least about 3 minutes per sensor publish to avoid the heat problem.   

![Alt text](/doc/BME280.jpg?raw=true "BME280")

# Code

You need to program the ESP8266. Mounted on the USB stick like this it is most convenient to use the Over-The-Air (OTA) programming which enables you to "flash" or re-program it wirelessly. However that does still require initializing the ESP-12 for OTA support ***before*** it is attached to the USB stick.

You need to install the Arduino IDE with ESP8266 support, as described [here](https://github.com/esp8266/Arduino#installing-with-boards-manager).

For the initial code you can just use the BasicOTA sketch that comes as an IDE example. Find that with the IDE menu bar "File -> Examples -> ArduinoOTA -> BasicOTA", and update the sketch with your Wifi netword SSID and password:

![Alt text](/doc/BasicOTA.jpg?raw=true "BasicOTA")
