# MCP9701A
The MCP9701A is an analog temperature sensor that converts temperature to analog voltage. The MCP9700/9700A and MCP9701/9701A sensors are designed to source/sink 100 µA (max.).

Here is the datasheet for this device: https://ww1.microchip.com/downloads/en/DeviceDoc/20001942G.pdf

                MD5                             SHA-1
003a8010f2c872e9da725d6c69f76897 ee33498247825d49fb32e9772598d829319a2f86 20001942G.pdf


Main Microchip.com landing for MCP9701A: https://www.microchip.com/en-us/product/MCP9701A



This project was created to help enigneers, technicians, and hobbyist quicky get the MCP9701A low voltage temperature sensor working in their own projects.

**The characteristic equations below should make it relatively easy and quick for you to design your own circuits around this device. (UNDER CONSTRUCTION!!!!)**


# Basic circuit used to test and gather characteristic data:

![Simple Circuit](<mcp9701a-e_to.png>)


# Characteristic equations (UNDER CONSTRUCTION!!!!):

**Characteristic Equation 1, (for 0 (uA) <= Iout <= 100 (uA)) MCP9701A is sourcing current:**

**Vout = 0.006294635769978737 * Temperature_In_Fahrenheit + 0.0030547026226642416 * VDD + 0.011635267509341334 * Iout_In_uA - 0.0021226953491044116**

The coefficient of determination (r-squared) for this Characteristic Equation 1 is 0.9999475739501221.


**NOTE 1: Iout_In_uA must be entered into the characteristic equations in uA (1 microAmp = 1x10^-06 Amps). See examples below.**

**NOTE 2: Regarding these characteristic equations and the schematic above, I am defining Iout to be postiive (+) when Iout is flowing out of the MCP9701A (sourcing current) , and I am defining Iout to be negative (-) when Iout is flowing into the MCP9701A (sinking current).**

**NOTE 3: From the manufacturer's datasheet, Iout must be:  -100uA <= Iout <= 100uA  for normal temperature sensing operation.**


Example 1a:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = +25uA, then

Vout = -0.007779402248826279 * (77) + 0.0009733172601552494 * (4.1) + 0.000028261925286710542 * (25) + 2.8933598263741938 = 2.29904300211337460309 Volts

Vout ~ 2.299 Volts

Example 1b:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = 0uA, then

Vout = -0.007779402248826279 * (77) + 0.0009733172601552494 * (4.1) + 0.000028261925286710542 * (0) + 2.8933598263741938 = 2.29833645398120683954 Volts

Vout ~ 2.298 Volts


The following form below of Characteristic Equation 1 may be easier for you if you know the DC Thevenin equivalent of the circuit your MCP9701A will drive:

Let Iout (in uA) = [(Vout - VL) / RL] * 1,000,000, then an equivalent alternative form of Characteristic Equation 1 is:

Vout = [a * Temperature_In_Fahrenheit + b * VDD - ((c * 1,000,000 * VL)/RL) + e]/[1 - (c * 1,000,000/RL)]

Vout = [-0.007779402248826279 * (Temperature_In_Fahrenheit) + 0.0009733172601552494 * (VDD) - ((0.000028261925286710542 * (1,000,000) * (VL)) / RL) + 2.8933598263741938]/[1 - (0.000028261925286710542 * (1,000,000) / RL)]


Example 1c:

If the ambient temperature is 77 degrees Fahrenheit, VDD = 4.1 Volts, Iout = +25uA, VL = 0, then

RL = ((2.29904300211337460309 - 0) / 25) * 1,000,000 = 91,961.7200845349841236 Ohms.

Vout = (-0.007779402248826279 * (77) + 0.0009733172601552494 * (4.1) - ((0.000028261925286710542 * 1,000,000*(0)) / 91,961.7200845349841236) + 2.8933598263741938) / (1 - (0.000028261925286710542 * 1,000,000 / 91,961.7200845349841236)) = 2.29904300211337460309 Volts

*Compare to result of Example 1a. They are the same.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Characteristic Equation 2, (for -100 (uA) <= Iout <= 0 (uA)) MCP9701A is sinking current:**

**Vout = -0.0075608961627175765 * Temperature_In_Fahrenheit + 0.0009416100793021476 * VDD + -0.000018778567101973768 * Iout_In_uA + 2.87419156362495**

The coefficient of determination (r-squared) for Characteristic Equation 2 is 0.990896061949286.


**NOTE 1: Iout_In_uA must be entered into the characteristic equations in uA (1 microAmp = 1x10^-06 Amps).  See examples below.**

**NOTE 2: Regarding these characteristic equations and the schematic above, I am defining Iout to be postiive (+) when Iout is flowing out of the MCP9701A (sourcing current) , and I am defining Iout to be negative (-) when Iout is flowing into the MCP9701A (sinking current).**

**NOTE 3: From the manufacturer's datasheet, Iout must be:  -100uA <= Iout <= 100uA  for normal temperature sensing operation.**


Example 2a:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = -25uA, then

Vout = -0.0075608961627175765 * (77) + 0.0009416100793021476 * (4.1) + -0.000018778567101973768 * (-25) + 2.87419156362495 = 2.29633262459838475886 Volts

Vout ~ 2.296 Volts

Example 2b:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = 0uA, then

Vout = -0.0075608961627175765 * (77) + 0.0009416100793021476 * (4.1) + -0.000018778567101973768 * (0) + 2.87419156362495 = 2.29586316042083541466 Volts

Vout ~ 2.296 Volts


The following form below of Characteristic Equation 2 may be easier for you if you know the DC Thevenin equivalent of the circuit your MCP9701A will drive:

Let Iout (in uA) = [(Vout - VL) / RL] * 1,000,000, then an equivalent alternative form of Characteristic Equation 1 is:

Vout = [a * Temperature_In_Fahrenheit + b * VDD - ((c * 1,000,000 * VL) / RL) + e] / [1 - (c * 1,000,000 / RL)]

Vout = [-0.0075608961627175765 * Temperature_In_Fahrenheit + 0.0009416100793021476 * VDD - ((-0.000018778567101973768 * 1,000,000 * VL) / RL) + 2.87419156362495] / [1 - (-0.000018778567101973768 * 1,000,000 / RL)]


Example 2c:

If the ambient temperature is 77 degrees Fahrenheit, VDD = 4.1 Volts, Iout = -25uA, VL = 4.1, then

RL = ((2.29633262459838475886 - (4.1)) / (-25)) * 1,000,000 = 72,146.6950160646096456 Ohms.

Vout = (-0.0075608961627175765 * (77) + 0.0009416100793021476 * (4.1) - ((-0.000018778567101973768 * 1,000,000 * (4.1)) / 72,146.6950160646096456) + 2.87419156362495) / (1 - (-0.000018778567101973768 * 1,000,000 / 72,146.6950160646096456)) = 2.29633262459838475886 Volts

*Compare to result of Example 2a. They are the same.


# Notes and limitations of the characteristic equations:

Besides the limitations listed in the [manufacturer's datasheet](20001942G.pdf "20001942G.pdf"), below are the ranges used in my tests to derive the characteristic equations shown above.  I anticipate adding wider temperature ranges to my tests as time and ambient temperatures permit which in turn will produce tweaks to the characteristic equations. However, I expect the characteristic equations above to be good for any situation in or "near" the domain criterion listed below.

-49.6992481203007uA <= Iout <= 47.840462905559uA

AND

75.6 degrees F <= Temperature_In_Fahrenheit <= 91.6 degrees F

AND

2.703V <= Vout <= 5.5V

I used 21 MCP9701ALPGs (TO-92S) to acquire the data. 300 different data points were used to determine the characteristic equations.


# Places to buy:

MCP9701A-E/TO from DigiKey:  https://www.digikey.com/en/products/detail/microchip-technology/MCP9701A-E-TO/1212511

MCP9701A-E/TO from Mouser:  https://www.mouser.com/ProductDetail/Microchip-Technology-Atmel/MCP9701A-E-TO?qs=RnzODY3cU8u0EUmxN333WQ%3D%3D

MCP9701A-E/TO from Arrow: https://www.arrow.com/en/products/mcp9701a-eto/microchip-technology

MCP9701A-E/TO from Newark: https://www.newark.com/microchip/mcp9701a-e-to/temperature-sensor-1c-3-to-92/dp/17M0680


# Observations:

(intentionally left blank)


# Another good analog temperature sensor:

https://github.com/Joe0x7F/LMT87

# Warning:

The TMP35/TMP36/TMP37 is an unpredictable/unstable product. I recommend against ever using it.

See https://github.com/Joe0x7F/TMP36.
