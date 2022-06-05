# MCP9701A
 The MCP9701A is an analog temperature sensor that converts temperature to analog voltage.

Here is the datasheet for this device: https://ww1.microchip.com/downloads/en/DeviceDoc/20001942G.pdf

This project was created to help enigneers, technicians, and hobbyist quicky get the MCP9701A low voltage temperature sensor working in their own projects.

The characteristic equation below should make it easy for you to design your own circuits around this device.


# Basic circuit used to test and gather characteristic data

![Simple Circuit](<SimpleCircuit.png>)


# Characteristic equation

**Vout = 0.010664993427881799 * TemperatureInFahrenheit + 0.003439744213177644 * VDD + 0.000021753013902669428 * RL + 0.036892333737057255**

The coefficient of determination (r-squared) for this equation is 0.9952001732812471.

**NOTE: RL must be entered into the characteristic equation in K ohms.**

So, for example, if VDD is 3.30 Vdc, the ambient temperature is 77.0 degrees Fahrenheit, and RL (your equivalent load resistance) is 100K Ohms, then you would expect Vout to be approximately: 0.872 Volts

Vout = 0.010664993427881799 * (77.0) + 0.003439744213177644 * (3.30) + 0.000021753013902669428 * (100) + 0.036892333737057255 = 0.871623284977708946

Vout ~ 0.872 Volts




# Limitations of the characteristic equation

Besides the limitations listed in the [manufacturer's datasheet](20001942G.pdf "20001942G.pdf"), below are the ranges used in my tests to derive the characteristic equation shown above.  I anticipate adding wider temperature ranges to my tests as time and ambient temperatures permit which in turn will produce tweaks to the characteristic equation. However, I expect the characteristic equation above to be good for any situation in or "near" the domain criterion listed below.

76.8 degrees Fahrenheit <= Ambient Temperature <= 91.0 degrees Fahrenheit <br />
AND <br />
3.128 Vdc <= VDD <= 5.260 Vdc <br />
AND <br />
21.51K Ohm <= RL <= 221.6K Ohm

I used 9 different MCP9701As to acquire the data. 102 different data points were used to determine the characteristic equation.

# Warning

The TMP35/TMP36/TMP37 is an unpredictable product. I recommend against ever using it.

See https://github.com/Joe0x7F/TMP36.
