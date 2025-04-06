 
 
 
 
 
 ###  **CURRENT MIRROR** 
 
 
 **What is Current Mirror?**

The current mirror is an analog circuit that senses the reference current and generates the copy or number of copies of the reference current, with the same characteristics. The replicated current is as stable as the reference current source. The replicated current could be the same as the reference current (Icopy = IREF), or it could be either multiple or fraction of the reference current. (Icopy = N*Iref or Icopy = (1/N)*IREF).

 ![Image](https://github.com/user-attachments/assets/ef2ff38e-9908-4132-8a0d-93a1d6359200)
 
                          Fig.1 Basic function of Current Mirror Circuit

**Why Current Mirrors are used?**

Current Mirrors are particularly useful in the integrated circuits, for biasing the amplifiers. The advantage of biasing the amplifiers with the current source is that it provides a high voltage gain and good biasing stability. This current source can be generated using a simple PMOS transistor or using a MOS transistor in cascode configuration.

But this type of MOS current source   is susceptible to the change in the biasing voltage and the change in temperature. Moreover, the integrated circuit may contain hundred or thousand of such amplifiers. To bias all the amplifiers with precise biasing voltage is another challenge. So, to overcome all these problems, in integrated circuits, one stable current source is fabricated within IC, and using the current mirror the multiple copies of the stable current source is generated (which can be used to bias the amplifiers).



**MOSFET- Current Mirror**

Fig.2 shows a current mirror circuit using the NMOS transistor. The reference current is converted to the voltage using diode connected transistor and the same is applied between the gate and the source of the another MOSFET.

![Image](https://github.com/user-attachments/assets/8918b1d4-319d-4457-8c8a-93b8a4dff028)

             Fig.2 Current Mirror Circuit using NMOS transistors

The relation between the ID1 and IREF can be given by the following expression.

![Image](https://github.com/user-attachments/assets/99e1561e-5671-442d-b139-6a3dda03e476)

By changing the W/L ratio of the two transistors, the current which is fraction or multiple of the reference current can be generated. The only thing which needs to be ensured is that, the MOSFET should operate in the saturation region.

**Effect of Channel Length Modulation on Current Mirror**

So far during the discussion, the effect of channel length modulation was neglected. If the channel length modulation effect is also considered, then as shown in Fig. 3, as the drain to source voltage (VDS) of the MOSFET increases, the drain current also slightly increases.

![Image](https://github.com/user-attachments/assets/b34c2e95-ca9c-449d-8064-e4e49131a92f)
                                             
          Fig.3 The effect of channel length modulation on drain current of the MOSFET

Considering the channel length modulation effect, if VDS of MOSFET M1 changes by ΔVDS then the drain current ID1 also changes to ID1 + ΔID1. The same is shown in Fig.4.

![Image](https://github.com/user-attachments/assets/52b6439d-2dd3-4749-ae22-d3de99810e4b)

       Fig.4 Effect of Channel Length Modulation on Current Mirror

The effect of channel length modulation can be reduced by increasing the length of the channel for the given W/L ratio.

**PMOS Current Mirror**

Fig.5 shows the implementation of current mirror using the PMOS transistors. In PMOS current mirror, the source terminals for both transistors are connected to Supply voltage Vdd.

![Image](https://github.com/user-attachments/assets/7d9b4646-21df-44e6-8584-15c7b20857ef)

      Fig.5 Current Mirror using PMOS transistors


The relation between the ID1 and IREF can be given by the same expression.


![Image](https://github.com/user-attachments/assets/8bba0691-6b34-439e-ba33-f8f25db2bf8c)

The only thing which needs to be ensured is that M1 should operate in the saturation region. Or in other words, VSD1 ≥ VSG – |VTP |, Where VTP is the threshold voltage of the PMOS transistor.


### **Part A**

Design a current mirror circuit which has a gain of AV = -10V/V, power supply of Vdd = 1.8V, and power of P <= 1mW. Find reference current (Iref), output current (Id), and total current (Itotal). Perform DC and AC analysis for mirror ratio 1:1, 1:2.

Circuit-1 (1:1 aspect ratio)

![Image](https://github.com/user-attachments/assets/0b1db859-a658-41a1-8bb1-67b6367b1747)



       Itotal =(P/Vdd)            Iref=Id=(Itotal/2)
             
              =(1mW/1.8V)                 =0.5mA/2
            
              =0.5mA                       =0.27m                  
 
                                         


  **Simulation Outcomes:**

  This document presents the simulation results for the current mirror circuit with different L (length) values of MOSFETs. The simulation was conducted for three cases with varying L values.

  **Case 1: L = 180 nm**

  ![Image](https://github.com/user-attachments/assets/807969b4-48b4-49f5-b919-4cbd94216184)

  Analysis:

Observation 1: W = 2.66u.

Observation 2: W/L ratio of M2 and M3 transistors are maintained same .

**Case 2: L = 500 nm**

![Image](https://github.com/user-attachments/assets/3464c221-604b-4762-a2f1-cf9f1813f6e2)

Analysis:

Observation 1: W = 12.2u

Observation 2: W/L ratio of M2 and M3 transistors are maintained same i,e 1:1 .

**Case 3: L = 1 µm**


![Image](https://github.com/user-attachments/assets/4f2acf05-58ee-4d33-b784-86e7a3ebccfb)
 
Analysis:

Observation 1: W=37.45u.

Observation 2: W/L ratio of M2 and M3 transistors are maintained same i,e 1:1 .

**Special Case: W/L Ratio of M2:M3 = 1:2**

![Image](https://github.com/user-attachments/assets/eb430aaf-ad9f-41b3-87aa-5b4a00d8db0b)

Analysis:

Observation 1: Width is kept at 180nm and length were M2:M3 = 2.66u:5.32u

Observation 2: W/L ratio of M2 and M3 transistors are maintained same i,e 1:2 .

###  **Transient analysis**

![Image](https://github.com/user-attachments/assets/7aadacac-ddf3-459b-8808-c52032c37bbd)

Observation: MaxOutSwing = 1.175Vp-p

### **Ac Analysis**

![Image](https://github.com/user-attachments/assets/e4afbb45-f7cf-49fe-98b0-1b4a08919252)

Observation: BW = 2.122GHz

### **Results:**

|Case	 |L (Length)W   |(Width)	|W/L Ratio|
|--------|--------------|-----------|---------|
|Case 1	 |180 nm     	|2.38 µm	| 1:1     |
|Case 2	 |500 nm	    |6.0649 µm	|1:1      |
|Case 3	 |1 µm	        |12.46 µm	|1:1      |
|Special |180 nm	    |4.76 µm	|1:2      |


### **Inference:**

+ Maintaining consistent W/L ratios for the MOSFETs ensures predictable operation of the current mirror.

+ As the length (L) of the MOSFETs increases, the width (W) also increases to maintain the same W/L ratio.

+ The special case with a W/L ratio of 1:2 shows that the current mirror can be adjusted for different mirroring ratios.

+ The total current (I_total) was calculated based on power supply and constraints, resulting in I_total = 0.55 mA, with I_ref and I_p each being 0.27 mA.

+ Ensuring MOSFETs operate in the saturation region (V_1 > V_th) is crucial for proper functioning of the current mirror.

## **Circuit-2**

![Image](https://github.com/user-attachments/assets/4f2e98d9-88d5-4049-8231-30e2d87e3d46)

**DC ANALYSIS**

![Image](https://github.com/user-attachments/assets/c0bfbce9-bcdc-4978-a942-5ce6cb335349)

+ Observation We can observe that current accross M6 and M3 transistors are almost double because of 1:2 W/L ratio

+ Observation We can observe that current accross M5 and M4 transistors are same because of 1:1 W/L ratio

**TRANSIENT ANALYSIS**
![Image](https://github.com/user-attachments/assets/b883f4a4-9f97-4aa9-b138-a89cd4e86fc8)

Observation: Av=Vout/Vin
             = 1.53/0.099 =15.45 v/v

**AC ANALYSIS**

![Image](https://github.com/user-attachments/assets/06e298b7-481b-4b20-8228-31fa8070fa9b)

Observation: Bw=1.94GHz

**INFERENCE**

**Current Accuracy**

+ 1:1 Ratio: Higher accuracy owing to identical transistor sizes.

+ 1:2 Ratio: Slight difference observed due to varying transistor widths.
+ Inference: The 1:1 ratio offers superior current matching.
**Transistor Sizing**
+ 1:1 Ratio: Utilizes smaller transistors, thus requiring less chip area.
+ 1:2 Ratio: Necessitates larger transistor widths, leading to increased area consumption.
+ Inference: The 1:1 ratio is more efficient in terms of chip area usage.
**Output Resistance**

+ 1:1 Ratio: Exhibits higher output resistance, as a longer channel length (L) reduces lambda, thereby increasing rout.
+ 1:2 Ratio: Shows slightly lower output resistance since larger transistor widths may introduce mismatch, slightly affecting lambda.
+ Inference: The 1:1 ratio provides better stability due to higher output resistance.
**Power Consumption**
+ 1:1 Ratio: Consumes less power due to the use of smaller transistors.
+ 1:2 Ratio: Consumes slightly more power because of the increased transistor sizes.
+ Inference: The 1:2 ratio results in higher power consumption due to larger devices.
**Design Complexity**
+ 1:1 Ratio: Easier to implement and match.
+ 1:2 Ratio: Requires precise selection of transistor width.
+ Inference: The 1:1 ratio is simpler to design and optimize.
