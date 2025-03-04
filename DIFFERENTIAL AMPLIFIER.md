 
#  **EXPT3:    DIFFERENTIAL AMPLIFIER** 

Design and analyze the differential amplifier for the following specifications VDD=3.3v, P<=3mw,Vicm=1.65v,Vocm=1.7v,Vp=0.5v. Perform DC analysis,transient analysis,frequency response and extract the parameters.

 ### **Aim:**

     
Design and analyze the differential amplifier circuit and extract the parameters.

 


### **Components/Parts required:**


+ MOSFETs, 
+ resistors, 
+ voltage supplies.



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


### **Procedure:**
####
+
    **Step 1:**
    DC analysis
    
    Design Rd and Rss
        
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


**Circuit 1:**

 Set L=180nm, Vdd=3.3V, Vicm=1.65v

 Vary width to get  to set Q point.

Given: Q-point(1.7V,0.45mA) for both M1 and M2

For this we have to use **.op** command
###

 ![Image](https://github.com/user-attachments/assets/62aefca4-3e5d-470b-a6ac-59c630ece556)

It shows that M1 and M2 are operating in saturation region and this operating point set at width=1.73um


+ **Step 2:** Transient analysis

Transient analysis is a  time-domain response of our circuit to various input signals. We can calculate gain of this differential amplifier. We have to use the  **.tran**   directive to specify the duration of the transient analysis.

###
 ![Image](https://github.com/user-attachments/assets/56f92aab-cf27-47d6-8175-d684fc58fe15)

voltage gain,

       Av=Vout/Vin
         =64.9/47.8
       Av=-1.357       Here - sign indicates that output is inverted.


We can observe that output is amplifying with a gain of 1.4


+ **Step 3:** AC analysis

 AC analysis in LTspice is used to analyze the frequency response of a circuit. It helps to understand how your circuit behaves at different frequencies, which is crucial for designing filters, amplifiers, and other frequency-dependent circuits.



 ![Image](https://github.com/user-attachments/assets/cf3bbd8d-6f13-48fc-87c4-6fdea87042ed)

 Use the **.ac** directive to specify the frequency range and number of points for the analysis.

          Gain in dB= 20log10(AV)

                     =20log10(1.357)

                      =2.656dB



**Like this we can do the analysis for replacing the source resistor by** 

 (1)current source and
  
  (2)the mosfet.


**Circuit 2: Replacing source resistor by current source**

 + **Step 1:** DC analysis
 
 ![image](https://github.com/user-attachments/assets/5b864773-b6d3-4cde-ad31-da40ef3eb49d)

In the operating values we got the current flowing through the common source terminal is exactly what we had derived in intial stage of the experiment.

+ **Step 2:** Transient analysis
![Image](https://github.com/user-attachments/assets/aabb9cdd-0508-48e9-9959-1cdb5e96ed0c)
 

            voltage gain, Av=vout/vin 

                        Av= 121.05187mV/49.0816mV

                        Av=-2.466             Here - sign indicates that output is inverted.

Gain is increasing compared to Circuit 1.



+ **Step 3:** AC analysis


![Image](https://github.com/user-attachments/assets/17b5fd5c-c67e-48e7-819e-b07c2c5a7248)


         Gain in dB=20log10(Av)
                  =20log10(2.466)
                  =7.84dB


 We should get gain in dB=7.84dB but actually we are getting around 4dB.

Wev have to work on it.


**Circuit 3: Replacing source resistor by mosfet**

Vary the width of M3 to set operating point. Set L=180nm

+ **Step 1:** Find VG (gate voltage for M3) and DC analysis

We know that when  the MOSFET is operating in the saturation (active) region VGD<=VTH

                    VG-VD<=VTH
                    VG<=VD+VTH
                    VG<=0.5V+0.366V
       Therefore,   VG<=0.866V



 
 ![Image](https://github.com/user-attachments/assets/4216ca2b-a82c-4795-a33d-70d7e9d13d0b)

 We get this output at w=8.6554u


+ **Step 2:** Transient analysis

![Image](https://github.com/user-attachments/assets/24a3590e-a319-4ac9-a79e-b3c972d556c9)


          voltage gain, Av=vout/vin 

                        Av= 120.37217mV/49.692077mV

                        Av=-2.472             Here - sign indicates that output is inverted.

  We get the same gain.


  + **Step 3:** AC analysis

  ![Image](https://github.com/user-attachments/assets/d825e670-8bc7-4274-be05-277b5a1a4348)





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
