# Virtual-control-and-measurement-device-with-the-use-of-a-measurement-card
Support for measurement cards with the use of dedicated drivers and functions.

Works:
- For communication with the measurement card, use libraries and subroutines provided by the manufacturer
- When using the measurement card, it is necessary to implement an electronic system that allows to determine the resistance
of the static two-terminal Rs, for this purpose the following should be used:
  - 1 DAC output: as a controlled voltage source
  - 2 ADC inputs: to measure the voltage on the tested double terminal and the DAC voltage
  - Ri resistor to determine the current flowing through the tested two-pole (connect the resistor in series with the object, use the voltage difference on the ADC inputs and the known resistance value - measure the reference resistance Ri with a multimeter and enter the obtained value into the program)
  - Use a diode and a resistor as exemplary double junctions for testing various operating modes of the program
- Determination of static resistance, manual mode (1) and automatic modes (2 and 3):
  - Mode 1: The operator sets the desired voltage source (DAC) with the knob or slider. They are presented on the panel
results for the selected DAC voltage.
  - Mode 2: The operator sets the value of the current for which he wants to determine the static resistance. The program is to determine the static resistance for the set current value by linear voltage regulation of the DAC converter with a step of 5 mV until the set current value is obtained.
  - Mode 3: The operator sets the current value for which he wants to determine the static resistance. The program has
determine the static resistance for the set current value by adjusting the voltage of the DAC converter by the method of successive approximations in 9 steps, starting from the voltage of 2.5V and in the following steps increasing or decreasing the value of the DAC voltage by half of the previous change (initial state: 2.5V, step 1: + / - 1.25V, step2: +/- 0.625V)
  - For modes 1 to 3:
    - The panel presents the current value of the static resistance and the current flowing through the object
(current value and history of changes), the current voltage on the site and the current measured voltage of the DAC
- Automatic determination of the current-voltage characteristic of the two-way point (Mode 4):
  - The device is to automatically determine the characteristic of the two-terminal by linearly increasing the voltage on
DAC output. The characteristics are to be presented on the XY Graph indicator (for convenience you can use
input builder)
  - The operator shall be able to define a maximum value for the DAC and the step of changing the DAC voltage
  - Determination of the characteristics is to stop when the set maximum DAC voltage is reached
or after reaching saturation by any ADC converter (approx. 2.4V)
  - Avoid errors in determining the starting and ending points of the characteristic
  - Enable you to save the designated characteristics to a file in CSV format (two columns separated
a semicolon containing pairs of currents and voltages - test the correctness of writing using Excel)
- Only one selected operating mode and its indicators / lamps are active
