# LinuxCNC signal adapter for a parallel port operating in X-mode.
**Version 153-01C**

Many PC printer port cards can be operated in 'X' mode in **LinuxCNC**.
In X-mode the card provides 9 input ports (Pin 1, Pin 10-17) and 8 output ports (Pin 2 - Pin 9). This is usually sufficient for a small CNC. I do not know if other software than LinuxCNC can set a Printer port card in X-mode.

I do not know a commercial version of an X-mode LPT breakout board, but they are easy to build using a commercially produced dual layer PCB. This is the X-mode adapter design that I use for my CNC's running LinuxCNC.
The hardware is designed in Eagle; the .sch and .brd files are included, as well
as the Gerber files for manufacturing. The board size is kept to 10 x 10 cm to keep the manufacturing costs low (with Far-East PCB services).
The **CERN-OHL-P V2** license applies, which means that you are free to copy the design, modify it and
sell the result.

**Design features:**

  * The breakout board Input and Output ports are electrically separated from the PC using fast optical couplers. The PC side of the circuit is powered via a small 5V DC/DC converter.
  * The board can be directly plugged into a PC printer port, or connected via a standard 26 wire ribbon cable with a printer port connector on the other end. The 26 pin connector can also be used to plug in a signal monitor.
  * The Inputs for Pins 10 through 17 support a wide range of input signals (<u>+</u> 30V). The Pin 1 Input is fully isolated from the whole adapter, and can handle up to 300V AC or DC, for instance to check presence of the mains or driver voltage.



**Inputs:**

**Pin 1** requires one or two series resistors (for DC) or capacitors (for AC) so that the effctive current through the bipolar optocoupler (PC814) is 4 - 6 mA:

* For standard 5V signals use 680 Ohm series resistance. For voltages over 100V use two components in series.
* For DC voltages make sure the power dissipation in the resistor(s) does not exceed their rating.
* For mains voltage use 2 x xxxnF for 127V and 2 x xxxnF for 230V. Each capacitor should preferably be rated for 400V.
* The P1 LED lights up when it detects the incoming signal.

**Pins 10 - 17** are set to about 0V (False) for an input between -30 and + 0.5 V, and to 5V (True) for an input between 1.5 an 30V. The input lines are filtered to suppress high frequency (~ 10 KHz) pulses. The 10 pin ribbon connector is an alternative input for Pin 10 - 17, and provides ground and 5V to supply a remote input panel.

**Outputs:**

**Pins 2 - 9 **drive 5V signals with a current up to 10 mA. The 10 pin ribbon connector is an alternative output, and provides ground and 5V to supply remote distribution panels.

**Power supply:**

The USB connector on the board should be connected to an separate 5V USB mains plug to maintain electric isolation from the PC. The 2-pin 5V connector on the board can then be used to supply other 5V hardware, as most USB plugs supply 1 -3 A current, and the board consumes only about 200 mA. If PC isolation is not needed, the board can be connected to one of the PC USB plugs,and the DC/DC converter can be replaced by two wires.

**Software:** XPtest-0.hal and xptest-0.xml provide a display of the X-mode adapter I/O ports and check / set their status. The test assumes that the adapter sits on the first printer port that the PC discovers. For cards that are discovered further on, change the settings in both files.

**Assembly:**

The X-mode adapter 153-01C is designed with only through hole components to facilitate home assembly. The component list (BOM) gives the details.
The small capacitors (useful values between 10 and 100 nF) are required to suppress RF disturbance.
The antiparallel diode next to the power connector will prevent damage in case the 5V is connected with the wrong polarity.
