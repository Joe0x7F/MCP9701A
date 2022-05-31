# MCP9701A
 The MCP9701A is an analog temperature sensor that converts temperature to analog voltage.

This project was created to help enigneers, technicians, and hobbyist quicky get the MCP9701A low voltage temperature sensor working in their own projects.

The characteristic equation given below should make it easy for you to design your own circuits around this device.


# Basic circuit used to test and gather characteristic data

![Simple Circuit](<SimpleCircuit.png>)


# Characteristic equation

Vout = 0.010794909077825357 * TemperatureInFahrenheit + 0.003601552216090184 * VDD + 0.000022013009740013396 * RL + 0.02551266767780824

***NOTE: RL must be in K ohms.***


So, for example, if VDD is 3.30 Vdc, the temperature is 77.0 degrees fahrenheit, RL (your equivalent load resistance) is 100K Ohms, then you would expect Vout to be 
approximately: 0.871 Volts

Vout = 0.010794909077825357 * (77.0) + 0.003601552216090184 * (3.30) + 0.000022013009740013396 * (100) + 0.02551266767780824 = 0.8708070899574596758

Vout ~= 0.871 Volts



# Warning

The TMP35/TMP36/TMP37 is an unpredictable prooduct. I recommend against ever using it.

See https://github.com/Joe0x7F/TMP36.
