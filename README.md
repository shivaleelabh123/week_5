# week_5
set_4


EXPERIMENT - 5
BASIC OPERATIONAL AMPLIFIER CIRCUITS

------------------------------------------------------------
CIRCUIT - (d)
NON-INVERTING AMPLIFIER
------------------------------------------------------------

Aim
To design and analyze a non-inverting amplifier using an operational amplifier and study its frequency response.

![Image description](PASTE_FILENAME_HERE)

Specifications
Supply Voltage: ±VCC = ±15 V
Input Signal: Vin(pp) = 12 Vpp
Frequency: f = 2 kHz
Desired Gain: Av = +5 V/V

Introduction
An operational amplifier (Op-Amp) is a high-gain differential amplifier widely used in analog circuits. The non-inverting amplifier is one of the basic configurations where the input is applied to the non-inverting terminal.
This circuit provides amplification without phase inversion and is widely used in signal conditioning applications.

Theory
A non-inverting amplifier works on the principle of negative feedback. The input is applied to the non-inverting terminal (+), and part of the output is fed back to the inverting terminal (−).

Voltage Gain:
Av = 1 + (Rf / R1)

The output is in phase with the input (0° phase shift).

Working Principle
1. Input signal is applied to the non-inverting terminal
2. Due to high gain of op-amp: V+ ≈ V−
3. Feedback adjusts output to maintain equality
4. Output becomes amplified version of input

Design Calculation
Given:
Av = 5

5 = 1 + (Rf / R1)
Rf / R1 = 4

Choose:
R1 = 1 kΩ
Rf = 4 kΩ

Circuit Diagram
(Non-inverting amplifier using op-amp with Rf and R1)

Simulation Steps (LTspice)

Step 1: Create Circuit
Open LTspice → New Schematic
Place components:
Op-amp (uA741 or opamp2)
Resistors R1 and Rf
Voltage source (Vin)
Power supply ±15V
Ground

Step 2: Connections
Connect Vin to non-inverting terminal (+)
Connect R1 between inverting terminal and ground
Connect Rf between output and inverting terminal
Connect ±15V to op-amp supply pins

Step 3: Input Signal
Set Vin as:
SINE(0 6 2k)

Step 4: Add Commands
.op
.tran 5m
.ac dec 10 1 1G

Step 5: Run Simulation
Observe:
Vout waveform
Gain
Phase

DC Operating Point Analysis
When Vin = 0 V:
Vout ≈ 0 V

This confirms proper biasing of the circuit.
Small offset voltage may be present due to practical op-amp limitations.

Transient Analysis
Observation:
Input waveform (Vin) is sinusoidal
Output waveform (Vout) is amplified

Key Observations:
Output is in phase with input
Gain ≈ 5
Output is clipped at ±15 V

Reason:
Theoretical output = ±30 V
But op-amp supply = ±15 V
Hence output saturates (clipping occurs)

AC Analysis
Frequency Sweep:
.ac dec 10 1 1G

Observation:
Gain ≈ 13.98 dB
Gain remains constant at low frequencies
Gain decreases at high frequencies

Reason:
Internal capacitances of op-amp
Finite gain-bandwidth product

Bandwidth is limited due to op-amp characteristics.

Results, Inference and Interpretation

Results Table
Parameter        Value
Gain (Linear)    5
Gain (dB)        ≈ 13.98 dB
Phase Shift      0°
Output           Clipped at ±15 V

Inference
The non-inverting amplifier provides the required gain of +5. The output remains in phase with the input. Clipping occurs due to supply voltage limitation.

Interpretation
The circuit behaves linearly for small signals. For large input signals, the output saturates because the op-amp cannot exceed its supply voltage.

Final Conclusion
The non-inverting amplifier is successfully designed and analyzed. The required gain is achieved with correct phase relationship. The circuit demonstrates practical limitation of output saturation.

------------------------------------------------------------
CIRCUIT - (e)
VOLTAGE FOLLOWER
------------------------------------------------------------

Aim
To design and analyze a voltage follower (unity gain buffer) and study its frequency response.

Specifications
Supply Voltage: ±VCC = ±15 V
Input Signal: Vin(pp) = 12 Vpp
Frequency: f = 2 kHz
Load Resistance: RL = 2.2 kΩ

Introduction
A voltage follower is a special case of a non-inverting amplifier where the output is directly connected to the inverting terminal. It provides unity gain and is mainly used for impedance matching.

Theory
Voltage follower:

Av = 1
Vout = Vin

It provides:
Very high input impedance
Very low output impedance

Working Principle
1. Input applied to non-inverting terminal
2. Output connected to inverting terminal
3. Due to negative feedback: V+ ≈ V−
4. Output follows input exactly

Circuit Diagram
(Output directly connected to inverting terminal)

Simulation Steps (LTspice)

Step 1: Create Circuit
Open LTspice → New Schematic
Place components:
Op-amp
Voltage source
Load resistor RL
Power supply ±15V
Ground

Step 2: Connections
Connect Vin to non-inverting terminal
Connect output directly to inverting terminal
Connect RL from output to ground

Step 3: Input Signal
SINE(0 6 2k)

Step 4: Add Commands
.op
.tran 5m
.ac dec 10 1 1G

Step 5: Run Simulation
Observe:
Input and output waveform
Gain
Phase

DC Operating Point Analysis
For Vin = 0 V:
Vout ≈ 0 V

Small offset voltage may appear due to non-ideal behavior.

Transient Analysis
Observation:
Input waveform is sinusoidal
Output waveform is identical

Key Observations:
No phase shift
Amplitude same as input
Vout ≈ Vin

Effect of Load:
Even with RL = 2.2 kΩ
Output remains unchanged

This shows low output impedance.

AC Analysis
Frequency Sweep:
.ac dec 10 1 1G

Observation:
Gain ≈ 0 dB
Gain remains constant at low frequencies
Gain decreases at high frequencies

Bandwidth is very high compared to other amplifiers.

Results, Inference and Interpretation

Results Table
Parameter        Value
Gain (Linear)    1
Gain (dB)        0 dB
Phase Shift      0°
Output           Same as input

Inference
The voltage follower maintains unity gain and accurately reproduces the input signal.

Interpretation
The circuit acts as an ideal buffer at low frequencies. At higher frequencies, performance is limited by op-amp bandwidth.

Final Conclusion
The voltage follower is successfully designed and analyzed. It provides unity gain, no phase shift, and excellent buffering capability. The circuit is suitable for impedance matching and signal isolation.
