# How to make a tiny USB powered ESP-12S

![Alt text](/doc/IMAG0624a.jpg?raw=true "Tiny USB powered ESP-12S")

This shows how to make a little USB powered ESP8266 that can run descretly plugged into a USB phone charger, for a cost of less than £2.50.

# What you need

![Alt text](/doc/IMAG0607a.jpg?raw=true "Parts")

You need:

1. A USB LED Light
   You can find these from Internet sellers, eg. [Bangood]([I'm an inline-style link](https://www.google.com)) currently have them for less than 50p if you buy 3 or more.

2. An XC6206 3.3V regulator
   The SOT-89 package, eg. these for 10 cents each from [AliExpress](https://www.aliexpress.com/item/20pcs-lot-XC6206P332PR-XC6206P332-XC6206-3-3V-SOT-89/32701818048.html)

3. An ESP-12S

   This **must** be the "S" version of the ESP-12. The "S" version has built-in pull-up/down resistors and bypass capacitors. Eg. these for £1.89 on [EBay](http://www.ebay.co.uk/itm/New-ESP8266-ESP-12S-Serial-Wireless-WIFI-Transceiver-Sender-Receiver-LWIP-AP-STA-/291971729155)
  
# Assembly

![Alt text](/doc/Assembly.jpg?raw=true "Assembly")

# Add environment sensor

You can add sensors on the back, for example, an environment sensor by adding a BME280 which measures temperature, air pressure and humidity (about £3 from [AliExpress](https://www.aliexpress.com/item/BME280-Digital-Sensor-Temperature-Humidity-Barometric-Pressure-Sensor-New/32659765502.html)).

***Note***, the ESP8266 uses about 70mA when running so gets noticably warm, which will effect the readings of any temperature sensor mounted on the back. To avoid that the ESP needs to use deep sleep most of the time and only wake up breifly to send the sensor readings. I've found it needs to deep sleep for at least about 3 minutes per sensor publish to avoid the heat problem.   

![Alt text](/doc/BME280.jpg?raw=true "BME280")
