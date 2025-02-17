# LINEAR INTEGRATED CIRCUITS-EXPERIMENT1
#  DC,AC and Transient Analysis of CS Amplifier
##  Introduction
The Common Source (CS) amplifier is a fundamental building block in analog circuit design, known for its voltage amplification capabilities. It utilizes an NMOS transistor where the input signal is applied to the gate, the output is taken from the drain and the source is common to both.A key feature is its ability to provide significant voltage gain, making it suitable for amplifying weak signals. The CS amplifier inverts the input signal that is there is a 180-degree phase shift between the input and output.It offers a high input impedance, which is beneficial for minimizing loading effects on the signal source. Here the circuit is biased using a DC voltage source(1.8V) and an input of AC signal is applied to the gate. CS amplifier analysis necessitates examining its static(DC) behavior,dynamic(AC) behavior and its time-domain(transient) response.
## Objective:
Determining its DC biasing conditions,voltage gain, input impedance, output impedance and observing the phase relationship between the input and output signals and frequency response.
## Key components used
Voltage source(DC): Its inteded use is to provide a DC bias voltage to the gate of the MOSFET.

AC input: Controls drain current and enables amplification.

Resistor: The resistor acts as a pull-up resistor for the output node.
## Circuit diagram
![WhatsApp Image 2025-02-17 at 19 25 33_eae90468](https://github.com/user-attachments/assets/5be4210b-4758-43af-9c12-b00ea5f310ca)

## Component details
For the simulation, TSMC018 library file is included which is crucial for accurate MOSFET simulation in TSMC 0.18um(180nm) CMOS technology.This library is stored in the same LTspice folder or the same directory of our simulation file.The drain resistor(R1) converts the drain current to output voltage, which limits the current through the FET and also affects the small signal gain.

Note: NMOS transistor operates in saturation region to act as an amplifier.

MODEL : CMOSN

MOSFET length(L): 250nm

MOSFET width(W): 0.05um

Resistor(R1): 1k

Voltage supply(Vdd): 1.8V

Input AC signal: DC offset=0.9V  ;  Amplitude=50mV ;  Frequency=1kHz


#  DC Analysis

| Width   | Length  | Current |
|-------  |-------- |---------|
|  0.35u  |   250nm |  45.94uA|
|  0.25u  |   250nm |  37.26uA|
|  0.15u  |  250nm  |  29.22uA|
|  0.10u  |  250nm  |  26.12uA |
|  0.05u  |  250nm  |  27.77uA |


![WhatsApp Image 2025-02-15 at 13 51 49_860626ca](https://github.com/user-attachments/assets/2e2e418a-d16d-4c8e-97c3-3b56181c4e2d)

DC analysis is done to ensure whether the mosfet operates in saturation region and to calculate the DC operationg point of the transistor. This prevents signal distortion, which helps in the determination of the biasing resistors.This helps in getting a correct operating point despite the fluctuation in the other parameters.

Here, L=250nm, W=0.05um .

Vout=1.77281

Id = 27.18uA

Given, P= 50um. V=0.9V
We know that, P=VI

Therefore, I=27.77uA

Also here, Vgs= 0.9V , Vds= 1.8V  , Vov= 1.29V , Vth =  0.366V

So here, Vgs>Vth and Vds>Vov

   FET is in saturation.

#  Transient analysis

Analyzing a circuit's response to changing signals is crucial for understanding its performance. This analysis reveals how the circuit might distort the signal, introduce unwanted DC offsets between input and output, or cause timing issues like phase distortion.  Such information is vital for identifying and correcting problems within the circuit.

![WhatsApp Image 2025-02-15 at 13 52 29_f91dbb84](https://github.com/user-attachments/assets/b1f222ac-065a-4dee-9888-c801bcd24687)

We can observe 180 degree phase shift between input and output and a DC level phase shift.

#  AC analysis

This is done to determine the Gain of the amplifier circuit,which also helps to analyze the Frequency Reponse of the amplifier circuit. The gain is given by 

                                                                         Av = -gm Rd

![WhatsApp Image 2025-02-15 at 13 53 01_770e196e](https://github.com/user-attachments/assets/28396fdd-12f6-4842-bd8b-cbe2401f6245)

#  Inference

1.Current Id mainly depends on width and hence it changes when the width changes whereas the remaining parameters remains almost constant.

2.MOSFET is in saturation region and it ensures that it works as an amplifier and produces the desired negative gain as per the equation.

3.Q point stability is attained in saturation region thus helping in attaining linear amplification .

4.We can observe that the MOSFETt gain is increased in mid band frequency range.


#  CIRCUIT_2



