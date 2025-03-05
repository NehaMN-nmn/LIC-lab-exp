# Experiment 2: DIFFERENTIAL AMPLIFIER

## Introduction
The differential amplifier is a crucial analog circuit that amplifies the difference between two input signals while rejecting common-mode signals, making it essential for applications requiring precise signal amplification and noise reduction; this experiment will investigate its key parameters, including differential-mode gain, common-mode gain, and CMRR, through practical measurements and analysis of a constructed circuit, thereby providing a hands-on understanding of its operational principles.

## Two different modes of differentail amplifier :
### 1.Common mode :
Common modes signal : (V1 + V2)/2
### 2.Diferential mode :
The difference between two given inputs : V1 - V2 

## Objective:
To design a differential amplifier for the following specifications.

VDD=2V,   P<=1mW,    Vicm=1V,    Vocm=1.1V,   Vp=0.4V

### Procedure :

1.Launch LTSpice: Open the LTSpice software and create a new schematic file.


2.Import library: Import the "tsmc018.lib" library file containing the NMOS transistor models.


3.Place components: From the component library, place two NMOS transistors(M1 and M2), three resistors(R1, R2, RSS) and three voltage sources(VDD, V2, V3).


4.Set component values: Set VDD to 2V. For DC analysis, set V2 and V3 to 0V. Assign the resistor values as per your diagram (R1 = R2 = 3.6kΩ, RSS = 0.8kΩ).


5.Connect components: Wire the components according to your differential amplifier diagram, ensuring correct connections between drains, gates, sources, and resistors.


6.Edit simulation command: Go to "Simulate" > "Edit Simulation Cmd" and choose the "DC op pnt" tab.

7.Enable DC operating point analysis: Check the box for "Calculate DC operating point" in the simulation command settings.


8.Run simulation: Click the "Run" button to initiate the simulation and calculate the DC operating point.


9.View results: Use the voltage and current probes to measure values at specific nodes in the circuit.


10.Access detailed results: Open the "SPICE Error Log" (View > SPICE Error Log) to view a comprehensive list of DC voltages, currents and power dissipation for all components.


## Key components used
1.M1 and M2 (CMOSN): These NMOS transistors form the heart of the amplifier, doing the actual amplification of the difference between the input signals.

2.VDD (2V): This DC power supply provides the energy for the circuit to operate and defines the voltage range the signals can swing within.

3.R1 and R2: These load resistors convert the amplified current from the transistors into the output voltage that we measure.

4.RSS: This tail resistor sets the bias current for the transistors, which is crucial for proper operation and influences the gain.

5.V2 and V3: These are the input voltage sources, providing the signals that the amplifier will take the difference of.

## Circuit diagram

![exp2 diagram1](https://github.com/user-attachments/assets/fa137ff2-20bf-46b6-b00e-ed005e0b79e5)


For the simulation, TSMC018 library file is included which is crucial for accurate MOSFET simulation in TSMC 0.18um(180nm) CMOS technology.This library is stored in the same LTspice folder or the same directory of our simulation file.

Note: NMOS transistor operates in saturation region to act as an amplifier.

MODEL : CMOSN

MOSFET length(L): 300nm

MOSFET width(W): 29.904um

Resistor(R1 and R2): 3.6k

Voltage supply(Vdd): 2V

Input AC signal: DC offset=1V  ;  Amplitude=50mV ;  Frequency=1kHz

#  DC Analysis
![image](https://github.com/user-attachments/assets/b859fd32-c689-4430-bfb4-db8cad2efdf6)

DC analysis is done to ensure whether the mosfet operates in saturation region and to calculate the DC operationg point of the transistor. This prevents signal distortion, which helps in the determination of the biasing resistors.This helps in getting a correct operating point despite the fluctuation in the other parameters.

Iss= P/Vdd = 1mW/2V =0.5mA

Rd=(Vdd-Vocm)/Id1 = (2-1.1)/0.25mA = 3.6kohm

Rss=Vp/Iss= 0.4/0.5m= 800ohm=0.8kohm

Coming to the MOSFETS M1 and M2;

Vds=0.7V

Vgs=0.6V

Vgd=-0.1V

Vth=0.47V

Vov=0.6-0.47=0.13V

Hence here Vgd<Vth

and Vds>Vov.

So, FET is in saturation region.

The theoritical value of Iss=0.5mA and Vout=1.1V, which is matching with our analysis as highlighted.

#  Transient analysis

Transient analysis in a differential amplifier investigates its dynamic behavior over time in response to varying input signals. Unlike DC analysis, which focuses on steady-state conditions, transient analysis reveals how the amplifier reacts to changes in input voltage, particularly how it amplifies or attenuates the difference between the two input signals as they change. This involves observing output waveforms for characteristics like gain, linearity, phase shift, and settling time, providing insights into the amplifier's ability to process time-varying signals accurately. By analyzing the transient response, one can assess the amplifier's performance in dynamic situations and its suitability for applications involving signals with varying frequencies and amplitudes, such as audio signals or sensor readings.

![exp2_transient both](https://github.com/user-attachments/assets/4ea133c5-72ba-4868-92cc-f369309e6a98)

We can observe 180 degree phase shift between input and output voltage.

# Output of transient analysis

![exp2_transient output](https://github.com/user-attachments/assets/5a5f8be1-2554-4edc-a763-0ca0ec0c4c31)

We know that,

Gain(Av)= Vout/Vin

hence, Av=(1.1904-1.0096)/(1.0492-0.9505)

         =1.83

Gain in dB = 20*log (1.83)

         =5.2490dB

#  DC Sweep

A DC sweep analysis of a differential amplifier involves varying the DC input voltage(s) and observing the corresponding changes in the output voltage. This technique helps to characterize the amplifier's transfer characteristics, revealing its input-output relationship and key parameters such as gain, linearity, and input/output voltage ranges. By sweeping the input DC voltage and measuring the output, one can plot the amplifier's DC transfer characteristic curve, which visually represents its behavior across different input levels.This analysis is crucial for determining the amplifier's operating point, biasing conditions, and overall performance in DC or low-frequency applications. Additionally, it can reveal any non-linearities or saturation effects, providing insights into the amplifier's limitations and dynamic range.

![exp2_dc sweep](https://github.com/user-attachments/assets/426f7738-3985-4c9f-8b50-d63387657742)

We can observe the distorted output.

From the graph Vipp=1.712-0.722

                =0.99V

Here Vicm(min)= Vth1+Vp
        =0.473+0.4
   Vicm(min) =0.873V

Also,

Vocm(max)= Vdd-(Iss*Rd)/2 +Vth

       =2-(0.5*3.6)/2 +0.473

 Vocm(max) = 1.573V

 average of   Vicm(min) and  Vocm(max) =(0.873+1.573)/2

             =1.223V

#  AC analysis   

AC analysis of a differential amplifier explores its behavior across a range of frequencies, revealing how it responds to different input signal frequencies. Unlike transient analysis, which examines the amplifier's response to time-varying signals, AC analysis focuses on its frequency-dependent characteristics, such as gain and phase shift. By sweeping the input frequency and observing the corresponding output, one can determine the amplifier's bandwidth, which is the range of frequencies over which it provides adequate gain. Additionally, AC analysis can reveal any frequency-dependent distortions or limitations in the amplifier's performance. This information is crucial for designing and optimizing differential amplifiers for specific applications, such as audio amplifiers or communication circuits, where signal frequencies vary significantly.

![image](https://github.com/user-attachments/assets/f612957a-986d-46b0-af33-4a58ebbf9c2a)

Gain in dB = 20*log (1.83)

         =5.2490dB

Here the value obtained from the analysis exactly equal to our theoritical value 5.2490dB.

#  Circuit 2

#  introduction

![exp22_circuit diagram](https://github.com/user-attachments/assets/1ae9ded4-5859-408a-9dec-96e805b737a0)

This diagram illustrates a modified differential amplifier circuit where the conventional tail resistor (RSS) has been replaced with a current source (I1). This enhancement aims to improve the circuit's performance by providing a more stable and controlled bias current for the differential pair (M1 and M2). By utilizing a current source, the circuit achieves better common-mode rejection and a more predictable operating point, leading to enhanced accuracy and stability in amplifying the difference between the input signals (V2 and V1). This configuration is particularly beneficial in applications requiring precise signal processing and immunity to common-mode noise, such as in instrumentation and sensor interfaces. The circuit retains its core functionality of amplifying the differential input while rejecting common-mode signals, but with improved performance due to the current source biasing.

Note: NMOS transistor operates in saturation region to act as an amplifier.

MODEL : CMOSN

MOSFET length(L): 300nm

MOSFET width(W): 29.904um

Resistor(R1 and R2): 3.6k

Voltage supply(Vdd): 2V

Input AC signal: DC offset=1V  ;  Amplitude=50mV ;  Frequency=1kHz

## Key components used

1. M1 and M2: These are the core NMOS transistors forming the differential pair, responsible for amplifying the difference between input signals.

2. R1 and R2: These load resistors convert the differential current signals into output voltage signals at Vout1 and Vout2.

3. V3: This is the DC power supply, providing the operating voltage for the amplifier.

4. I1: This current source sets the bias current for the differential pair, influencing its operating point and performance.

5. V2 and V1: These are the input voltage sources, providing the differential input signals to be amplified.

#  DC Analysis

![image](https://github.com/user-attachments/assets/c836ab55-81a6-4815-ba05-f5e373281442)


Iss= P/Vdd = 1mW/2V =0.5mA

Rd=(Vdd-Vocm)/Id1 = (2-1.1)/0.25mA = 3.6kohm

Here the resistor Rss is replaced by current Iss=0.5mA.

Vds=0.7V

Vgs=0.6V

Vgd=-0.1V

Vth=0.47V

Vov=0.6-0.47=0.13V

Hence here Vgd<Vth

and Vds>Vov.

So, FET is in saturation region.

We can observe that even after replacing resistor Rss into current source I1 of 0.5mA,

the output voltage Vout is perfectly matching with the theoritical value i.e, 1.1V.

#  Transient analysis

![exp22_transient analysis both](https://github.com/user-attachments/assets/3b158aa0-8885-4968-aecc-4106a494ae7c)

We can observe 180 degree phase shift between input and output voltage, as observed in the circuit 1.

# Output of transient analysis

![exp22_transient output](https://github.com/user-attachments/assets/13ac8e9b-050f-48c6-832a-df9a512ee38c)

Gain(Av)= Vout/Vin

        =9.71

 Gain in dB = 20*log (1.83)       

        19.74

#  DC Sweep




        












