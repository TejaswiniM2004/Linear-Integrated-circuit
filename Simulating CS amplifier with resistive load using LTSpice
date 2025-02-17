 ## TASK1: ##
Analyse CS amplifier using LTspice with specifications 180nm, tsmc, Vdd=1.8V, Vg=0.9V, power budget=50µW and extract the parameters-DC operating point, DC analysis, gain, bandwidth, power.

**Introduction:**

**Objectives:**

Analysis of CS amplifier to extract parameters like DC operating point, gain, bandwidth etc. using LTspice.

**Explanation:**

 The common source amplifier (CSA) is a fundamental building block in electronics, valued for its ability to amplify signals effectively across a wide range of applications. In this setup, the source terminal of the transistor is common to both the input and output, serving as the reference point for both signals. The input signal is applied between the gate and the source, while the output is taken from the drain and the source.

 The common source amplifier provides significant voltage gain, making it useful for amplifying weak signals. The output signal is inverted relative to the input, which is advantageous in certain applications where phase inversion is needed. This configuration typically offers high input impedance and low output impedance, making it suitable for interfacing with various signal sources and loads. It is used in signal amplification, oscillators, analog signal processing, active filters.

**Circuit description:**

Circuit:

![Image](https://github.com/user-attachments/assets/83b1d8b8-a53b-4467-997e-d443ffa3d24d)


**Components Required:**
 TSMC 180nm NMOS transistor (CMOSN), voltage sources (v1 and v2), drain resistor (R1) and ground.


1.	Transistor (NMOS or PMOS):
   The core component of the amplifier, responsible for amplifying the input signal. In the case of an NMOS transistor: 
Gate: The input terminal where the signal is applied. It controls the flow of current between the drain and source.
Drain: The output terminal where the amplified signal is taken. The output voltage varies based on the input signal.
Source: Commonly connected to ground, providing a reference point for the input and output.

2.	Resistive Load (Rd): It creates a voltage drop when current flows through it, which is crucial for generating the output signal. The value of Rd impacts the voltage gain of the amplifier. Higher resistance generally leads to higher gain.

3.	Power Supply (VDD): Provides the necessary voltage for the amplifier to function. It is connected to the drain through the resistive load, allowing the circuit to draw power for amplification.

   **Working:**

 The input signal is applied to the gate of the transistor. This voltage controls the current flowing from the drain to the source. As the input voltage increases, the gate-source voltage (VGS) increases, leading to an increase in drain current (ID), assuming the transistor is biased correctly and remains in the saturation region. The transistor’s operation is characterized by its transconductance (gm), which determines how much the drain current changes in response to changes in VGS.

 The increase in ID causes a larger voltage drop across the resistive load (RD), resulting in a decrease in the output voltage at the drain. The output voltage is thus an inverted version of the input signal, due to the relationship between the current and the voltage drop across RD. The gain of the amplifier is determined by the transconductance of the transistor and the load resistance:

                         Av≈−gm RD                  
This negative sign indicates the inversion of the output signal.
 The amplified and inverted signal is taken from the drain terminal, which can then be further processed or fed into additional circuit stages.

**Simulation Procedure:**

We are using the TSMC model to predict the behaviour of Common Source Amplifier.
1. Open LT Spice and new schematic.
2. Place the 4 terminal NMOS on to the schematic, connect the MOSFETs source terminal   to the ground, gate terminal to 0.9V voltage source, drain terminal to 1.8V source through 1KΩ drain resistor. Connect body terminal and two voltage sources to ground. Use wires for connection.
3. Right-click on the NMOS and set length and width. Like this right click on each component to give specifications.
4. To include tsmc018.lib spice model, go to spice directive and paste the path of that library file. Name the input the output pins.
5. Use .op command to find the DC operating point. Set up an AC analysis with the .ac command and transient analysis with the .tran command. Specify   dc offset , amplitude, stop time, frequency, type of sweep all those. 
6. Run the simulation to check dc, ac and transient analysis.
 
 
 **Observations:**

1.	DC Analysis:


![Image](https://github.com/user-attachments/assets/b0bbf244-e885-47bb-ad8a-a73424c6066e)

From this plot we are getting ID=27.1755µA and VDS=1.25649V. 

2.	Transient Analysis:

![Image](https://github.com/user-attachments/assets/ea0fda5c-d3f6-4d37-8c30-76617b23cdd7)

By giving AC input to the Gate terminal We are getting this plot. From this we get input and output voltages. It is used to find the gain.

                    Av=Vout/Vin
                      =90mV/50mV
                    Av=1.8

3.	AC Analysis:


![Image](https://github.com/user-attachments/assets/46c95ad6-c335-4343-8c26-3fc98db8e406)

From the AC analysis we get the frequency response curve. From this,
Gain in dB=28.92dB


        
        
**Theoretical calculations:**


VDD=1.8V     P=50µW    W=500nm       L=487nm   RD=20KΩ


                 ID=P/VDD=50µW/1.8V=27.78µA



                VDS=VDD-IDRD=1.8V-27.78µA*20KΩ

                   =1.2444V



               Vov=VGS-VTH=0.9-0.366=0.534V

                   gm=2ID/Vov=104.04µS

                      Av=-gm*RD
                        =-104.04µS*20KΩ
                        =2.08

**Result:**

Drain Cureent (ID)=28µA

Output Voltage (VDS)=1.26V

Gain(Av)=2


**Inference:**

Drain current depends on width of the channel hence it varies when width changes whereas other parameters remains constant.

From theoretical calculation we get gain as 2.08 but in simulating LTspice we get it as 1.8 (by transient analysis).

 By dc analysis we get operating point as (1.25V, 27.17µA) and mosfet is in                saturation region. 
I observed that when I increase RD gain also increased.
