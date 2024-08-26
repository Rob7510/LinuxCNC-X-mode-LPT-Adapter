# LinuxCNC signal adapter for a parallel port operating in X-mode.
**Version 153-01C**

Many PC printer port option boards can be operated in 'X' mode in **LinuxCNC**, by setting this mode in the 'loadrt hal_parport' command.
In X-mode the 25-pin I/O connector provides 9 input ports (Pin 1, Pin 10-17) and 8 output ports (Pin 2 - Pin 9). This is usually sufficient for a small CNC. (I do not know if other software than LinuxCNC can set a Printer port card in X-mode).

The signal breakout for an X-mode adapter can be home built with a low cost dual layer PCB, with full electric isolation from the connected PC. This document provides the Eagle design and the Gerber manufacturing files for such a Breakout Board (BoB). The board size is kept to 10 x 10 cm to keep the manufacturing costs low (with Far-East PCB services). The **CERN-OHL-P V2** OpenHardware license applies, hence you are free to copy the design, modify it and sell/use the result.

**Design:**

  * The BoB input and output ports are electrically separated from the PC using optical couplers. The PC side of the circuit is powered via a small 5V isolated DC/DC converter. Te board uses approximately 150 mA, and can be powered with an old USB-A power adapter.
  * The board can be directly plugged into a 25 pin PC printer port, or connected via a standard 26 wire ribbon cable with a printer port connector on the other end. The 26 pin connector can also be used to plug in a signal monitor.
  * The Inputs for Pins 10 through 17 support a wide range of input signals (<u>+</u> 30V). The Pin 1 Input is fully isolated from the whole board, and can handle up to 300V AC or DC signals, for instance to check presence of the mains voltage or Power supply output.


**Inputs:**

**Pin 1** requires one or two series resistors (for DC) or capacitors (for AC) so that the current through the bipolar optocoupler (PC814) is in the range of 4 - 10 mA:
* For standard 5V signals use a 680 Ohm resistor. For voltages over 100V use two components in series.
* For DC voltages make sure the power dissipation in the resistor(s) does not exceed their rating.
* For 230V mains voltage use 2 x 150nF (400V). To keep high voltages away from the board, mount the capacitors or resistors at the source, and fill the two onboard slots with jumpers.
* The P1 LED lights up when it detects a valid signal.

**Pins 10 - 17** are set to about 0V (False) for an input between -30 and + 0.5 V, and to 5V (True) for an input between 1.5 an 30V. These inputs suppress high frequency (>5KHz) pulses. The 10 pin ribbon connector connects Pin 10 - 17, as well as GND and 5V to a remote input panel.

**Outputs:**

**Pins 2 - 9 ** drive 5V signals with a current up to 35 mA. The fast optical couplers (6N137) can handle pulses as short as 2 microseconds. The 10 pin ribbon connector is for connection to a remote breakout panel. All outputs (typically used for stepper signals) can be collectively turned off with a logic input signal.

**Power supply:**

The USB connector on the BoB should be connected to an separate 5V USB power supply to maintain electric isolation from the PC. The onboard 2-pin 5V connector can be used to supply other 5V hardware like relay boards. If PC isolation is not needed, the BoB can be connected to one of the PC USB plugs, and the DC/DC converter can be replaced by two wires.

**Software:** XPtest-0.hal and xptest-0.xml provide a display of the X-mode adapter I/O ports and check / set their status. The test assumes that the BoB connects to the first printer port that the PC discovers.

**Assembly:**

The X-mode adapter 153-01C uses through-hole components to facilitate home assembly. The component list (BOM) has the details.
The small capacitors (useful values between 10 and 100 nF) are required to suppress RF disturbance.
The antiparallel diode next to the power connector will prevent damage in case the 5V is connected with the wrong polarity (I hate replacing dead chips).
