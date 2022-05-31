# MCP9701A
 The MCP9701A is an analog temperature sensor that converts temperature to analog voltage.

Here is the datasheet for this device: https://ww1.microchip.com/downloads/en/DeviceDoc/20001942G.pdf

This project was created to help enigneers, technicians, and hobbyist quicky get the MCP9701A low voltage temperature sensor working in their own projects.

The characteristic equation below should make it easy for you to design your own circuits around this device.


# Basic circuit used to test and gather characteristic data

![Simple Circuit](<SimpleCircuit.png>)


# Characteristic equation

Vout = 0.010794909077825357 * TemperatureInFahrenheit + 0.003601552216090184 * VDD + 0.000022013009740013396 * RL + 0.02551266767780824

The coefficient of determination (r-squared) for this equation is 0.9941778756953391.

***NOTE: RL must be in K ohms.***


So, for example, if VDD is 3.30 Vdc, the temperature is 77.0 degrees fahrenheit, RL (your equivalent load resistance) is 100K Ohms, then you would expect Vout to be 
approximately: 0.871 Volts

Vout = 0.010794909077825357 * (77.0) + 0.003601552216090184 * (3.30) + 0.000022013009740013396 * (100) + 0.02551266767780824 = 0.8708070899574596758

Vout ~ 0.871 Volts




# Limitations to the characteristic equation

Besides the limitations listed in the [datasheet](20001942G.pdf "20001942G.pdf"), below are the ranges used in my tests to derive the characteristic equation shown above.  I anticipate adding wider temperature ranges to my tests as time and ambient temperatures permit which in turn will produce tweaks to the characteristic equation. However, I expect the characteristic equation above to be good for any situations "near" the ranges listed below.

I used 9 different MCP9701As to acquire the data.

76.8 degrees Fahrenheit <= Ambient Temperature <= 89.2 degrees Fahrenheit <br />
AND <br />
3.128 Vdc <= VDD <= 5.260 Vdc <br />
AND <br />
21.51K Ohm <= RL <= 221.6K Ohm


# Warning

The TMP35/TMP36/TMP37 is an unpredictable product. I recommend against ever using it.

See https://github.com/Joe0x7F/TMP36.
