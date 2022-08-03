# MCP9701A
The MCP9701A is an analog temperature sensor that converts temperature to analog voltage. The MCP9700/9700A and MCP9701/9701A sensors are designed to source/sink 100 µA (max.).

Here is the datasheet for this device: https://ww1.microchip.com/downloads/en/DeviceDoc/20001942G.pdf

                MD5                             SHA-1
003a8010f2c872e9da725d6c69f76897 ee33498247825d49fb32e9772598d829319a2f86 20001942G.pdf


Main Microchip.com landing for MCP9701A: https://www.microchip.com/en-us/product/MCP9701A



This project was created to help enigneers, technicians, and hobbyist quicky get the MCP9701A low voltage temperature sensor working in their own projects.

**The characteristic equations below should make it relatively easy and quick for you to design your own circuits around this device.**


# Basic circuit used to test and gather characteristic data:

![Simple Circuit](<mcp9701a-e_to.png>)


# Characteristic equations:

**Characteristic Equation 1, FOR 0 (uA) <= Iout <= 100 (uA), MCP9701A is sourcing current:**

**Vout  = 0.011526966933808041 * Temperature_In_Fahrenheit + 0.005141759459988668 * VDD - 0.00006455409191007096 * Iout_In_uA - 0.03950709236257986**

The coefficient of determination (r-squared) for this Characteristic Equation 1 is 0.9794267220990659.


**NOTE 1: Iout_In_uA must be entered into the characteristic equations in uA (1 microAmp = 1x10^-06 Amps). See examples below.**

**NOTE 2: Regarding these characteristic equations and the schematic above, I am defining Iout to be postiive (+) when Iout is flowing out of the MCP9701A (sourcing current) , and I am defining Iout to be negative (-) when Iout is flowing into the MCP9701A (sinking current).**

**NOTE 3: From the manufacturer's datasheet, Iout must be:  -100uA <= Iout <= 100uA  for normal temperature sensing operation.**


Example 1a:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = +25uA, then

Vout  = 0.011526966933808041 * (77) + 0.005141759459988668 * (4.1) - 0.00006455409191007096 * (25) - 0.03950709236257986 = 0.8675367230288410618 Volts

Vout ~ 0.8675 Volts


Example 1b:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = 0uA, then

Vout  = 0.011526966933808041 * (77) + 0.005141759459988668 * (4.1) - 0.00006455409191007096 * (0) - 0.03950709236257986 = 0.8691505753265928358 Volts

Vout ~ 0.8692 Volts


**The following form below of Characteristic Equation 1 may be easier for you if you know the DC Thevenin equivalent of the circuit your MCP9701A will drive:**


Given this form of Characteristic Equation 1: Vout = a * Temperature_In_Fahrenheit + b * VDD + c * Iout_in_uA + e.

Let Iout_in_uA = [(Vout - VL) / RL] * 1,000,000, then an equivalent alternative form of Characteristic Equation 1 is:

Vout = [a * Temperature_In_Fahrenheit + b * VDD - ((c * 1,000,000 * VL)/RL) + e]/[1 - (c * 1,000,000/RL)]

Therefore,
Vout = (0.011526966933808041 * Temperature_In_Fahrenheit + 0.005141759459988668 * VDD - ((-0.00006455409191007096 * 1,000,000 * VL) / RL) - 0.03950709236257986)/(1 - ((-0.00006455409191007096 * 1,000,000) / RL))


Example 1c:

Note:
RL = (Vout-VL)*1,000,000/Iout_in_uA

So, if the ambient temperature is 77 degrees Fahrenheit, VDD = 4.1 Volts, Iout = +25uA, VL = 0, (from Example 1a) Vout = 0.8675367230288410618 Volts, then

RL = (Vout-VL)*1,000,000/Iout_in_uA = (0.8675367230288410618 - 0) * 1,000,000 / 25 = 34,701.468921153642472 Ohms.


Vout = (0.011526966933808041 * 77 + 0.005141759459988668 * 4.1 - ((-0.00006455409191007096 * 1,000,000 * 0) / 34,701.468921153642472) - 0.03950709236257986)/(1 - ((-0.00006455409191007096 * 1,000,000) / 34,701.468921153642472)) = 0.8675367230288410618

*Compare to result of Example 1a. They are the same.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Characteristic Equation 2, FOR -100 (uA) <= Iout <= 0 (uA), MCP9701A is sinking current:**

**Vout  = 0.011066511626424604 * Temperature_In_Fahrenheit + 0.0064653234928165855 * VDD - 0.000009774365871666986 * Iout_In_uA - 0.004720069006290857**

The coefficient of determination (r-squared) for Characteristic Equation 2 is 0.9801000691017826.


**NOTE 1: Iout_In_uA must be entered into the characteristic equations in uA (1 microAmp = 1x10^-06 Amps).  See examples below.**

**NOTE 2: Regarding these characteristic equations and the schematic above, I am defining Iout to be postiive (+) when Iout is flowing out of the MCP9701A (sourcing current) , and I am defining Iout to be negative (-) when Iout is flowing into the MCP9701A (sinking current).**

**NOTE 3: From the manufacturer's datasheet, Iout must be:  -100uA <= Iout <= 100uA  for normal temperature sensing operation.**


Example 2a:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = -25uA, then

Vout  = 0.011066511626424604 * (77) + 0.0064653234928165855 * (4.1) - 0.000009774365871666986 * (-25) - 0.004720069006290857 = 0.8741535116957433262 Volts

Vout ~ 0.8742 Volts


Example 2b:

If temperature is 77 degree Fahrenheit, VDD = 4.1, Iout = 0uA, then

Vout  = 0.011066511626424604 * (77) + 0.0064653234928165855 * (4.1) - 0.000009774365871666986 * (0) - 0.004720069006290857 = 0.87390915254895165155 Volts

Vout ~ 0.8739 Volts


**The following form below of Characteristic Equation 2 may be easier for you if you know the DC Thevenin equivalent of the circuit your MCP9701A will drive:**

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
