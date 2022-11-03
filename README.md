## NIXIE WATCH 2077 ##

Cyberpunk Looking Nixie Watch with CNC Milled Chassis, Not-so-robust code, a microcontroller and one lazy student :)

#WIP

# Part Selection 

## Nixie Tubes
Z5900M(or Z590) Nixie Tubes are small Indication Tubes That require 150V DC(but with a measly 1~1.5mA Power Consumption) as a Power Source. It's small footprint and relative abundance compared to some Burroughs Tubes is curtainly a plus. There are Z5900s, they are the same ones with protective orange layer.


## Microcontroller
Since the entire project revolves around Arduino IDE - an AVR Friendly IDE - I used an ATTINY. Specificially, ATTINY- []
It's an ATTINY with Watchdog, Interrupt, I2C Capability, Plenty of I/Os, and Internal Pullup, and whole nine yards.


## High Voltage Shift Register
There are many ways to control these Nixie Tubes, including Russian made BCD to Decimal Decoder, K155ID1(Known Alias : SN74741). This one uses 4 BCD Pins to decode it into 10 Pin Decimal Pins.
But it's large DIP-16 factor simply detered me, plus I would need a Optocoupler or a Second K155ID1 for a second tube, not even counting an AMPM Bulb in RHDP of Z5900M

There's where Microchip's HV5523 Comes in. It's essentially 74HC595 Shift Register - in fact we use that very library in arduino - but it has Open Drain meaning without it powered it can act be disconnected from the circuit, and ties connected pins to GND when it is. This way an Anode of Nixie Tube will be Connected to 150V Power Supply, and Cathodes will be connected to HV5523's HVOUT Pins. 

##
