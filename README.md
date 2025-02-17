# LINEAR INTEGRATED CIRCUITS-EXPERIMENT1
#  DC,AC and Transient Analysis of CS Amplifier
##  Introduction
The Common Source (CS) amplifier is a fundamental building block in analog circuit design, known for its voltage amplification capabilities. It utilizes an NMOS transistor where the input signal is applied to the gate, the output is taken from the drain and the source is common to both.A key feature is its ability to provide significant voltage gain, making it suitable for amplifying weak signals. The CS amplifier inverts the input signal that is there is a 180-degree phase shift between the input and output.It offers a high input impedance, which is beneficial for minimizing loading effects on the signal source. Here the circuit is biased using a DC voltage source(1.8V) and an input of AC signal is applied to the gate. CS amplifier analysis necessitates examining its static(DC) behavior,dynamic(AC) behavior and its time-domain(transient) response.
## Objective:
Determining its DC biasing conditions,voltage gain, input impedance, output impedance and observing the phase relationship between the input and output signals and frequency response.
## Key components used
1.Voltage source(DC): Its inteded use is to provide a DC bias voltage to the gate of the MOSFET.

2.AC input: Controls drain current and enables amplification.

3.Resistor: The resistor acts as a pull-up resistor for the output node.
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

##  Introduction

This report analyzes a Common-Source(CS) amplifier utilizing an NMOS transistor as the amplifying element and a PMOS transistor as an active load, replacing the traditional drain resistor. This configuration offers potential advantages in performance, including higher voltage gain and improved output swing compared to CS amplifiers with resistive loads. The analysis covers the DC biasing of the circuit to establish the proper operating point, followed by an AC analysis to determine key amplifier characteristics such as voltage gain, input and output impedance, and bandwidth. 

## Objective:
To analyze the performance characteristics of a Common-Source amplifier employing an NMOS transistor and a PMOS active load, including its gain, impedance, and bandwidth.

## Key components used
1.NMOS Transistor: The main amplifying device.
2.PMOS Transistor: Acts as the active load.
3.DC Voltage Sources (VDD): Provides the necessary bias voltages.
4.Output (Vout): Delivers the inverted signal based on the input applied to V1.

## Circuit diagram

![WhatsApp Image 2025-02-17 at 22 24 12_ca589ef1](https://github.com/user-attachments/assets/71a5aa5a-f3b2-44b1-ac68-2914c17bde05)

For the simulation, TSMC018 library file is included which is crucial for accurate MOSFET simulation in TSMC 0.18um(180nm) CMOS technology.This library is stored in the same LTspice folder or the same directory of our simulation file.The drain resistor(R1) converts the drain current to output voltage, which limits the current through the FET and also affects the small signal gain.

MODEL : CMOSN

MOSFET length(L): 39um

MOSFET width(W): 33um

VTH  = 0.3662473


MODEL : CMOSP

MOSFET length(L):180nm

MOSFET width(W): 15um

VTH = -0.3906012


Voltage supply(Vdd): 1.8V

Input AC signal: DC offset=0.9V  ;  Amplitude=50mV ;  Frequency=1kH

#  DC Analysis

| Width   | Length  | Current |
|-------  |-------- |---------|
| 20u  |    39um |  15.64uA|
| 37u |    39um |  28.955uA|
| 50u  |  39um  |  39.135uA|
| 45u |  39um  |  35.219uA |
|  35u  | 39um |  27.388uA |

![WhatsApp Image 2025-02-17 at 22 17 46_c9a42217](https://github.com/user-attachments/assets/1094a9e7-434d-437d-a76b-399847cfb942)

The DC analysis of this NMOS-PMOS Common-Source amplifier establishes Q-point by determining the DC voltages and currents at each node. This involves calculating the gate-source voltages and drain currents for both the NMOS and PMOS transistors, ensuring they operate in the saturation region for the NMOS and active region for the PMOS load.
The drain current obtained is given by the formula

                                                          Id = 1/2 kn Vov2 
                                                          
                                                          Vov=Vgs-Vth and 
                                                          
                                                          kn=un Cox W/L


Vout=1.79532

Id = 27.322uA

Given, P= 50um, V=1.8V
We know that, P=VI

Therefore, I=27.77uA

Vs= 1.8V , Vg=0.3V , Vsg=1.5V , Vth= -0.366V , Vsd= 1.79V.

Therefore, Vsg>|Vth| and Vsd>|Vov|

Hence, FET is in saturation region.

#  Transient analysis
Transient analysis simulates the amplifier's time-domain response to a time-varying input signal, such as a sinusoidal or square wave.  This analysis reveals the output waveform, allowing observation of distortion, clipping, and other non-linear effects.  Key parameters like voltage gain and propagation delay are determined by comparing input and output signal characteristics.  The transient response also helps assess the amplifier's ability to accurately reproduce the input signal and reveals any transient effects like overshoot or ringing.  Specifically, the switching behavior of the NMOS and PMOS transistors is examined.  Ultimately, transient analysis verifies if the amplifier meets design requirements for speed, signal fidelity, and other dynamic performance metrics.
We can observe 180 degree phase shift between input and output and a DC level phase shift.

![WhatsApp Image 2025-02-17 at 22 20 52_a0e85046](https://github.com/user-attachments/assets/e574e11a-8dc8-4f52-982d-8366a3bebe55)


#  AC analysis

This AC analysis measures how well the NMOS common-source amplifier amplifies signals across a range of frequencies. By plotting the gain, we can see how the amplification changes with frequency and identify the limits of the amplifier's useful frequency range(its bandwidth).

![WhatsApp Image 2025-02-17 at 22 23 20_2347dbb2](https://github.com/user-attachments/assets/152bd9ba-a48e-4178-af2d-f9cc4fb17e3e)

#  Inference

1.The DC operating point established by V3(0.3V) and the transistor sizes ensures both PMOS and NMOS are in the appropriate operating region for amplification that is the saturation region.

2.The AC analysis demonstrates a certain voltage gain at midband frequencies, indicating the amplifier's ability to boost the input signal.

3.The observed bandwidth indicates the range of frequencies over which the amplifier provides effective amplification before the gain significantly drops.

4.The transient analysis reveals the amplifier's time-domain response to input signals.

5.The combination of NMOS and PMOS transistors as a load offers performance advantages compared to using a simple resistive load, as evidenced by the gain and bandwidth achieved.






