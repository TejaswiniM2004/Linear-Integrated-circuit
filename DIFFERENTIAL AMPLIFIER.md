 
#  **EXPT3:    DIFFERENTIAL AMPLIFIER** 

Design and analyze the differential amplifier for the following specifications VDD=3.3v, P<=3mw,Vicm=1.65v,Vocm=1.7v,Vp=0.5v. Perform DC analysis,transient analysis,frequency response and extract the parameters.

 ### **Aim:**

     
Design and analyze the differential amplifier circuit and extract the parameters.

 

 ### **Components required:**


+ MOSFET(M1 and M2)
+ Resistors 
+ Voltage supplies
+ Ground
+ Connecting wires



### **Theory:**

 


![Image](https://github.com/user-attachments/assets/ae5c0fea-fb85-4bfc-a2b8-0f3662bb65ea)


 Differential-amplifier configuration is the most widely used building
block in analog integrated-circuit design.There are two reasons why differential amplifiers are so well suited for IC fabrication: First, as we shall shortly see, the performance of the differential pair depends critically on the matching between the two sides of
the circuit. Integrated-circuit fabrication is capable of providing matched devices whose
parameters track over wide ranges of changes in environmental conditions. Second, by
their very nature, differential amplifiers utilize more components (approaching twice as
many) than single-ended circuits.

The above figure shows the basic MOS differential-pair configuration. It consists of two matched
transistors, Q1 and Q2, whose sources are joined together and biased by a constant-current
source I. Each drain is connected to the positive supply
through a resistance RD. If the voltage supply at the gate terminal is the same, then the current through Q1 and Q2 is also the same. This configuration is called "Common-Mode Input Voltage Differential Amplifier".Gain will be zero in this configuration.  Whatever type of load is used, it is essential
that the MOSFETs not enter the triode region of operation. It should be in saturation region.


  ### **Calculations:**  Design Rd and Rss
        
      Given P<=3mw

      P=VDD*Iss

      Iss=3mW/3.3V=0.909mA

      ID1=ID2=Iss/2=0.4545mA

      RD=VDD-Vocm/Iss=3.3V-1.7V/0.45mA=3.55kΩ

      Rss=Vp/Iss=0.5V/0.909mA=0.555kΩ

  Designed values are,
                      
                      Iss=0.909mA
                      
                      ID1=ID2=0.4545mA
                      
                      RD=3.55kΩ
                      
                      Rss=0.555kΩ

### **Procedure:**
####

1.Launch the LTspice software on your computer.

2.Go to File > New Schematic to open a new schematic editor.

3.Add the necessary components for your differential amplifier circuit.Like NMOS transistor,Resistors, Voltage sources

4.To place components, click on the Component symbol (or press F2), and select the required components from the list.

5.Arrange and connect the components using wires.

6.Assign appropriate values to the components. For example, set the resistor values, voltage source values, and transistor parameters.

7.Go to edit option select spice directive and attach tsmc018.lib file
   
8.To configure the simulation, go to Simulate > Edit Simulation command and choose the type of analysis you want to perform. Set the necessary parameters for the analysis.

9.Run the Simulation and analyze the results.
  

### **Simulation:**

**Circuit 1:**

![image](https://github.com/user-attachments/assets/953bf31f-1c99-456e-a909-3c6373543d0a)

+ **Step 1:DC analysis**
  
  We know that condition for saturation is that VDS > VOV and VGD < Vth, where Vth is the threshold voltage of the MOSFET, which is obtained from the tsmc018.lib file.
  
  VGD = (1.65 – 3.33) V = -1.65V
  Vth = 0.366 V
  Since  VGD<Vth  the MOSFET is operating in saturation/active region and can act as an amplifier.
  We have determined that the MOSFET is in saturation, now we need to set ideal Q-point.


![image](https://github.com/user-attachments/assets/89818b52-afb8-4320-ae61-99175e9b33fd)
W=6.18576um  and  L=180nm

For DC analysis we have to use **.op** command. We can see that  Vout, Vp and Id is matching with our necessary requirements.  

  
+ **Step 2:** Transient analysis

Transient analysis is a  time-domain response of our circuit to various input signals. We can calculate gain of this differential amplifier. 
To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 1.65V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain. We have to use the  **.tran** directive with stop time equal to 5 ms.

###
  **CIRCUIT DIAGRAM**
![image](https://github.com/user-attachments/assets/4d4b3330-70a3-451d-a3bb-efae62137d0c)

INPUT AND OUTPUT VOLTAGES
![image](https://github.com/user-attachments/assets/30643eff-b830-4401-b44c-b68c4a0be949)

![image](https://github.com/user-attachments/assets/eb36a188-1a85-4013-9a63-80fd03306834)


  

Green waveform represents the output voltage at Vout1  and blue waveform represents the voltage at node n003. Both are sinusoidal.
 

 We can observe that there is a 180 degree phase shift between the green and blue waveforms. Analyzing the phase shift helps determine the behavior of the differential amplifier.
 The amplitude of the waveforms provides insight into the gain of the amplifier. Comparing the amplitudes of the input and output signals helps assess the amplification factor.

voltage gain,

       Av=Vout/Vin
         =103.05/-48.7
       Av=-2.116       Here - sign indicates that output is inverted.


 Output is amplifying with a gain of 2.116


+ **Step 3:** AC analysis

 AC analysis in LTspice is used to analyze the frequency response of a circuit. It helps to understand how your circuit behaves at different frequencies, which is crucial for designing filters, amplifiers, and other frequency-dependent circuits.

To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation. Use the **.ac** directive to specify the frequency range and number of points for the analysis.

**CIRCUIT DIAGRAM**

  ![image](https://github.com/user-attachments/assets/6b6ba663-fb1c-4cee-8540-ddf2f08b69e3)


**FREQUENCY RESPONSE PLOT**
   

By using formula,
  
          Gain in dB= 20log10(AV)

                     =20log10(2.116)

                      =6.51dB
                      
![image](https://github.com/user-attachments/assets/08e99337-ec4e-43a0-b7c9-7589fdb166a7)


      From the plot gain in dB=6.64dB

  From here we can see that gain in dB matches approximately with our calculated value.

      
 
Now, we will move to the  circuit 2, where we will replace the resistor R3 by Current source.
A current source provides a constant current regardless of the voltage across it, which is beneficial for maintaining a stable operating point in your differential amplifier. Current sources typically have a much higher output resistance compared to resistors. This higher output resistance increases the overall gain of the differential amplifier, leading to better amplification of the input signal. With a current source, the common-mode gain is significantly reduced, leading to an improved CMRR.


**Circuit 2: Replacing source resistor(R3) by current source**

 
   
**CIRCUIT DIAGRAM**

![image](https://github.com/user-attachments/assets/5a398ac2-f5cb-4382-910c-e2421a61d16f)


 + **Step 1:** DC analysis


![image](https://github.com/user-attachments/assets/8743e929-e709-4dfd-b2d1-b8567fa708b2)



In the operating values we got the current flowing through the common source terminal is exactly what we had derived in intial stage of the experiment.

To operate mosfet in saturation region VGD<Vt

        VGD = VG - VD
            = 1.65v – 3.3V
        VGD = -1.65V < Vt=0.366V
        
Since VGD<VT MOSFET operates in saturation region.

As we can see that VD1 = VD2 = 3.3 V, which is matching with our necessary requirements. ID1 = ID2 = 0.45 mA, ISS = 0.9mA which also matches with our requirements. Vp = 0.5V, which also agrees with our analysis.

Next, we can calculate the power and verify whether or not we are within our power budget.

P = VDD. Iss = 3.3 V x 0.9 mA = 2.97 mW, which satisfies our power budget.



+ **Step 2:** Transient analysis

  To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 1.65V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain. We have to use the  **.tran** directive with stop time equal to 5 ms.

**CIRCUIT DIAGRAM**
![image](https://github.com/user-attachments/assets/5a398ac2-f5cb-4382-910c-e2421a61d16f)


**INPUT AND OUTPUT VOLTAGES**
![image](https://github.com/user-attachments/assets/a54e470b-b2d0-4a3d-be16-5c5d417cd8c9)

![image](https://github.com/user-attachments/assets/621b4ae1-e17a-40af-a61a-951ebf45a69f)


 We can observe that there is a 180 degree phase shift between the green and blue waveforms. Analyzing the phase shift helps determine the behavior of the differential amplifier.
 The amplitude of the waveforms provides insight into the gain of the amplifier. Comparing the amplitudes of the input and output signals helps assess the amplification factor.

            voltage gain, Av=vout/vin 

                        Av= 59.676845mV/ 48.098292mV

                        Av=-1.24             Here - sign indicates that output is inverted.

  Output is amplifying with a gain of 1.24.  



+ **Step 3:** AC analysis
  
To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation. Use the **.ac** directive to specify the frequency range and number of points for the analysis.

  
![image](https://github.com/user-attachments/assets/99ff4570-efdd-45ee-9dd9-17ae34d23dc8)


         Gain in dB=20log10(Av)
                  =20log10(1.24)
                  =1.87352dB


 
     From the plot gain in dB=1.955dB

  From here we can see that gain in dB matches approximately with our calculated value.

Now, we will move to the final circuit, where we will replace the current source , with a NMOS Transistor. The reason we do this, is due to the fact that the NMOS can behave as a constant current source when operating in the saturation region, so it can act as a constant current source, when the input gate voltage VG is applied to drive the MOSFET into saturation.
      
 
**Circuit 3: Replacing current source  by NMOS transistor**


 ![image](https://github.com/user-attachments/assets/3096f108-149e-4473-b398-4fb7a93da762)


+ **Step 1:** DC analysis

We know that when  the MOSFET is operating in the saturation (active) region if VGD<=VTH

                    VG-VD<=VTH
                    VG<=VD+VTH
                    VG<=0.5V+0.366V
       Therefore,   VG<=0.866V


![image](https://github.com/user-attachments/assets/8235f73e-7b0c-49ac-9545-020b6e77209f)


 All the  voltage, current values are matching with our requirements.
 

+ **Step 2:** Transient analysis

  INPUT AND OUTPUT VOLTAGES
  
![image](https://github.com/user-attachments/assets/a73fcfad-6abe-4911-87dd-884634e9620f)

 ![image](https://github.com/user-attachments/assets/e67cf9b8-6295-4f96-819e-19c707fac381)


We can observe that there is a 180 degree phase shift between the green and blue waveforms. Analyzing the phase shift helps determine the behavior of the differential amplifier.
 The amplitude of the waveforms provides insight into the gain of the amplifier. Comparing the amplitudes of the input and output signals helps assess the amplification factor.


          voltage gain, Av=vout/vin 

                        Av= 68.430589mV/48.169746mV
  
                        Av=-1.42             Here - sign indicates that output is inverted.

  
  Output is amplifying with a gain of 1.42.




  + **Step 3:** AC analysis



    To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation. Use the **.ac** directive to specify the frequency range and number of points for the analysis.

  

        Gain in dB=20log10(Av)
                  =20log10(1.42)
                  =3.0457dB
                  


 ![image](https://github.com/user-attachments/assets/93a94d49-b810-4d34-af1d-6a5c1754d772)


      From the plot gain in dB=3.083dB

  From here we can see that gain in dB matches approximately with our calculated value.



### **Inference:**

1.DC Analysis:

+ The designed differential amplifier operates at the specified Q-point (1.7V, 0.45mA) with both MOSFETs (M1 and M2) in saturation, ensuring optimal performance.

+ The calculated resistor values (RD=3.55kΩ, Rss=0.555kΩ) and current (ID1=ID2=0.4545mA) ensure the amplifier operates within the given power constraint (P ≤ 3mW).

2.Transient Analysis:

+ The differential amplifier exhibits a voltage gain (Av) of approximately 1.4, indicating a slight signal inversion.

+ Circuit 2(with a current source) ,  shows an improved gain of 2.466, demonstrating the benefits of using a current source for better performance.

+ Circuit 3(with a MOSFET maintains),  shows a similar gain of 2.472, suggesting consistent performance with MOSFET biasing.

3.AC Analysis:

+ The gain in dB for the initial circuit is 2.656 dB, while Circuit 2 achieves a higher gain of 7.84 dB, highlighting the improved frequency response with the current source.

+ Circuit 3 shows similar performance in terms of transient gain, indicating the MOSFET biasing achieves comparable results to the current source.

### **Conclusion:**

 The differential amplifier design meets the specified requirements, demonstrating stable performance across different configurations. The use of current sources or MOSFETs for biasing enhances the amplifier's gain and frequency response. However, there are minor deviations in the expected gain for Circuit 2, suggesting the need for further optimization. Overall, the design and analysis provide valuable insights into the behavior of differential amplifiers in various configurations.
