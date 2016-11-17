# Nefit-Buderus-EMS-bus-Arduino-Domoticz

Readout of Nefit/Buderus EMS interface Protocol by Arduino and transfer of data via HTTP GET requests to Domoticz home automation software (or to other systems).

## Goal:
Readout the Nefit/Buderus EMS interface of a Nefit Trendline gas boiler (gas condensing central heating boiler).

Transfer of data via ethernet to Domoticz home automation software.

## What does it do?
This sketch reads the EMS interface data and depending on the format decodes the data and puts it in variables.
You can then send the values via HTTP GET requests to Domoticz or do whatever you want with it.
Usage is not limited to Domoticz, you can extract the decoding part for other purposes.

## When will the sketch and the schematics be uploaded?
As soon as I have a stable version. I am currently testing it.
For progress updates check the following forum:
http://www.domoticz.com/forum/viewtopic.php?f=38&t=14132

There will be 2 versions.
One version for only reading the EMS but and one version which includes writing to the bus.

## Boiler support
Should support all boilers using the EMS databus.
This includes most Bosch boiler brands like Nefit, Buderus, Worcester.

## Hardware:
* EMS interface circuit
* Arduino Mega + Wiznet Ethernet Shield
* Raspberry Pi with Domoticz

The EMS bus interface can be converted to TTL level by means of a simple circuit.
The TTL-converted signal can then be connected to one of the the Arduino UARTs.

This sketch uses the Arduino Mega and the Wiznet 5100 ethernet shield.
You can also use another Arduino like the Uno but that one only has one hardware serial port.

Serial1 is used for the EMS module.
Serial is used to debug the output to PC. 
EMS serial works with 9700 Baudrate and 8N1.
For sending data to the EMS bus a modified Serial library will be supplied.

Arduino Mega:
* Serial  on pins  0 (RX)  and 1 (TX),
* Serial1 on pins 19 (RX) and 18 (TX),
* Serial2 on pins 17 (RX) and 16 (TX),
* Serial3 on pins 15 (RX) and 14 (TX). 

Arduino non-Mega:
You cannot use Serial1, so you need to use Serial, which does not allow for debugging via serial.

## Where did you find all the information about the bus?
http://www.mikrocontroller.net/topic/309075
http://www.mikrocontroller.net/topic/141831
http://emswiki.thefischer.net/doku.php?id=start

### How about MQTT instead of HTTP GET requests?
That is on my list.
For now it will work exactly like my other Github project ['Vbus-Arduino-Domoticz'](https://github.com/bbqkees/vbus-arduino-domoticz).

#### Additional credits
Sketch is based on the EMS sketches from 'Jvdmeer' from the Nodo forum.

#### Legal Notices
'Worcester, Bosch Group', 'Buderus' and 'Nefit' are brands of Bosch Thermotechnology.

All other trademarks are the property of their respective owners.