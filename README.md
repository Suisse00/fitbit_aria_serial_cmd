# fitbit aria
Contains some informations about the serial port commands on the fitbit aria scale.

## Serial port

UART on UART1
Baud: 115200
Data bits: 8
Stop bits: 1
Parity: None
Pin out (standard TTL-232RG):
1. GND
2. CTS#
3. VCC
4. TXD
5. RXD
6. RTS#

Pin out (standard TTL-232RG):
1. GND
2. CTS#
3. VCC
4. TXD
5. RXD
6. RTS#

Credit: http://pooloferrors.com/project/2015/01/10/fitbit-teardown.html

## Notes

* Do not use navigations keys (arrow keys) nor delete or backspace.
* Commands results end with ```END.```
* Enter should process the latest commmand
* Console may not work while the device is sleeping, you have to wake it up (the only know way I know it to step into it)

## Commands
This documentation is based on manual tests and not by reverse engineering the firmware

* fwver  : Return the firmware version
* hwrev  : Return the hardware version?
 * deviceid  : Return versions
* bat  : Return battery informations
* lcdtext <text> : Display text on the screen (case sensitive)
Know character availables :
    * a = display a checkbox
    * -- = display ...
    * A-Z
    * 0-9
    * /
    * .
    * !
    * %
    * ?
    * (
    * )
* lcdpat <hexa value from 0 up to FFFF> : Allow you to manually control some lcd segments
    * bit 1: display a "x" and refresh icon as well as the upper rounded bar (where pixels are alternatively on and off)
    * bit 2 to 7 display one line of the text line (2 is the top line and 7 is the bottom line; where pixels are alternatively on and off in the same line)
    * bit 8 Display the "wifi" icon, the no battery icon and the upper rounded bar (where pixels are alternatively on and off)
* icon <0 from 16> specific led of the upper rounded bar to turn off. 
0 hide the bar while 16 display it full
* pbar <value between 0 up to 16> : Allow you to control the upper rounded bar (the bar use to display the progression when "thinking"). LCD will turn on from the left to right.
* pwm <value from 0 to 10> : control the brightness of the screen
        getsn  : Get serial number of the device
        getmac  : Get the mac address
        setcolor  :
        getcolor  :
        setunits <value>  :
        getunits  :
        weigh  : return 2 weights
The first one is probably the weight with the tare and unit managed while the second is the raw value.
        htcmd  <command> <value>: send a raw command to the HT16C23 (lcd driver)
        scan  : Scan wifi available