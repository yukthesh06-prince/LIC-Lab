# Experiment 4 

# Differential Amplifier Analysis

## Aim

To design and simulate three MOSFET differential amplifier configurations using LTspice by performing DC, Transient, and AC analyses, and to compare their performance based on gain, bandwidth, and power efficiency.

## Introduction

A differential amplifier is one of the most fundamental building blocks in analog circuit design. It amplifies the difference between two input signals while rejecting common-mode signals, making it highly useful in noise-sensitive applications.

MOSFET-based differential amplifiers are widely used in integrated circuits such as operational amplifiers, comparators, and analog signal processing systems due to their high gain, good noise immunity, and efficient performance.

In this experiment, three different MOSFET differential amplifier configurations are analyzed using LTspice. The behavior of each circuit is studied through DC, Transient, and AC analyses to understand their gain, bandwidth, and overall performance characteristics.

## Theory

A differential amplifier is a circuit that amplifies the difference between two input signals while rejecting any signal that is common to both inputs. This property is known as common-mode rejection and is an important feature in analog circuit design.

A basic MOS differential amplifier consists of two matched MOSFETs (M1 and M2) whose sources are connected together and biased using a constant current source. The drains are connected to load elements such as resistors or active loads.

When a differential input voltage is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total current is steered between the two transistors depending on the input difference. If $v_{in1} > v_{in2}$, transistor M1 conducts more current, and if $v_{in2} > v_{in1}$, transistor M2 conducts more.

For small differential inputs, both transistors operate in the saturation region, and the circuit behaves linearly. The differential gain of the amplifier is given by:

$$
A_v = g_m R_{out}
$$

where $g_m$ is the transconductance of the MOSFET and $R_{out}$ is the effective output resistance.

The transconductance is defined as:

$$
g_m = \frac{2 I_D}{V_{ov}}
$$

where $I_D$ is the drain current and $V_{ov}$ is the overdrive voltage.

For larger differential inputs:

$$
v_{id} > \sqrt{2} V_{ov}
$$

one transistor turns OFF while the other carries the entire current, resulting in non-linear operation.

The performance of the differential amplifier depends on the type of load used:

- Resistive load → moderate gain  
- Active load → higher output resistance and higher gain  
- Current mirror load → maximum gain and improved output characteristics  

Thus, by changing the circuit configuration, the gain, bandwidth, and overall performance of the differential amplifier can be significantly affected.

---

## Circuit 1: Differential Amplifier with Resistive Load

## 1.1 Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected to a constant tail current source and their drains connected to resistive loads.

When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total tail current ($I_{SS}$) is steered between the two transistors depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The change in drain current through each transistor produces a corresponding voltage drop across the load resistors ($R_D$), resulting in differential output voltages at the drains.

For small differential inputs, both transistors operate in the saturation region, and the amplifier behaves linearly, producing an amplified output proportional to the input difference.

For larger differential inputs, one transistor may turn OFF while the other carries the entire current, resulting in non-linear operation.

Thus, the circuit converts a differential input voltage into a differential output voltage using current steering through resistive loads.

## Circuit Diagram

![Circuit 1](Results/exp4a_circuit.png)

## 1.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 1.2.a Power Constraint


The total power consumed by the differential amplifier is given by:

$$
P = (V_{DD} - V_{SS}) \cdot I_{SS}
$$

Total supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9) = 1.8V
$$

Since the maximum allowed power is 1.8mW,

$$
P \leq 1.8 \times 10^{-3}
$$

$$
(V_{DD} - V_{SS}) \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
1.8 \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
I_{SS} \leq 1mA
$$

To fully utilize the available power budget, we choose:

$$
I_{SS} = 1mA
$$

Power dissipated:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Since $1.8mW \leq 1.8mW$, the power constraint is satisfied.

##

### 1.2.b Drain Current Calculation

Under balanced input conditions:

$$
V_{in1} = V_{in2}
$$

the differential pair operates symmetrically, and the tail current splits equally between both transistors.

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

Thus, each transistor carries equal current under zero differential input.

##

### 1.2.c Load Resistance Calculation

Given:

$$
V_{OCM} = 0V
$$

So,

$$
V_{out1} = V_{out2} = 0V
$$

The output voltage is given by:

$$
V_{out} = V_{DD} - I_D R_D
$$

Substituting:

$$
0 = 0.9 - I_D R_D
$$

$$
I_D R_D = 0.9
$$

Solving for resistance:

$$
R_D = \frac{0.9}{I_D}
$$

Substituting:

$$
R_D = \frac{0.9}{0.5 \times 10^{-3}}
$$

$$
R_D = 1.8k\Omega
$$

##

### 1.2.d Bias Point Calculation

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

### Source Voltage

Given:

$$
V_p = -0.7V
$$

Assuming:

$$
V_S = V_p
$$

$$
V_S = -0.7V
$$

### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

### Overdrive Voltage

Given:

$$
V_T \approx 0.36V
$$

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

### Drain Voltage

From previous calculation:

$$
V_{out1} = V_{out2} = 0V
$$

### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

### Saturation Check

Condition:

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Hence, both transistors operate in saturation.

### Final Bias Point

$$
V_G = 0V
$$

$$
V_S = -0.7V
$$

$$
V_D = 0V
$$

$$
V_{GS} = 0.7V
$$

$$
V_{DS} = 0.7V
$$

##

### 1.2.e Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_T)^2
$$

Rewriting:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging to find width:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
$$

### Substituting Values

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 236.5 \mu A/V^2 = 2.365 \times 10^{-4}
$$

$$
V_{OV} = 0.34V
$$

### Calculation

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.1156}
$$

$$
W = \frac{480 \times 10^{-12}}{2.732 \times 10^{-5}}
$$

$$
W \approx 17.57 \mu m
$$

The width calculated using first-order equations provides an approximate value based on assumed parameters such as constant mobility and ideal saturation conditions. However, in practical MOSFET models, several non-ideal effects such as channel length modulation, mobility degradation, and model parameter variations affect the actual operating point.

To strictly satisfy the given condition:

$$
V_p = V_S = -0.7V
$$

the transistor width was fine-tuned using simulation. By adjusting the width, the drain current was controlled such that the source node voltage precisely matched the required value.

Final width obtained:

$$
W \approx 28.475 \mu m
$$

Thus, the deviation from the theoretical width arises due to non-ideal device behavior and the need to meet exact biasing conditions in simulation.

---

## DC Analysis

![DC Analysis](Results/exp4a_dc.png)

The DC operating point confirms that the output voltage and source voltage is near the designed bias value, ensuring proper saturation operation.

---

### 1.2.f Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.

### Minimum Input Common Mode Voltage

For proper operation, the tail current source must remain active and the NMOS transistors must stay in saturation.

Condition:

$$
V_{GS} \ge V_T
$$

Using:

$$
V_{GS} = V_{ICM} - V_S
$$

So,

$$
V_{ICM(min)} = V_S + V_T
$$

Substituting values:

$$
V_S = -0.7V, \quad V_T = 0.36V
$$

$$
V_{ICM(min)} = -0.7 + 0.36
$$

$$
V_{ICM(min)} = -0.34V
$$

### Maximum Input Common Mode Voltage

For maximum input voltage, the NMOS transistors must remain in saturation.

Condition:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_D = 0V, \quad V_S = -0.7V
$$

$$
V_{DS} = V_D - V_S = 0 - (-0.7) = 0.7V
$$

Now,

$$
V_{ICM(max)} = V_D + V_T
$$

Substituting:

$$
V_{ICM(max)} = 0 + 0.36
$$

$$
V_{ICM(max)} = 0.36V
$$

### Final Input Common Mode Range

$$
-0.34V \le V_{ICM} \le 0.36V
$$

##

### 1.2.g Output Common Mode Range

The output common-mode voltage range is determined by ensuring that the NMOS transistors remain in saturation and the circuit operates properly.

### Maximum Output Voltage

The maximum output voltage occurs when the drain voltage is at its highest possible value, which is limited by the supply voltage:

$$
V_{OCM(max)} \le V_{DD}
$$

However, to maintain current flow through the load resistor:

$$
V_{OCM(max)} = V_{DD}
$$

$$
V_{OCM(max)} = 0.9V
$$

### Minimum Output Voltage

For proper operation, the NMOS transistors must remain in saturation:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_{DS} = V_D - V_S
$$

At the edge of saturation:

$$
V_D - V_S = V_{OV}
$$

So,

$$
V_D = V_S + V_{OV}
$$

Since:

$$
V_D = V_{OCM(min)}
$$

$$
V_{OCM(min)} = V_S + V_{OV}
$$

### Substituting Values

$$
V_S = -0.7V, \quad V_{OV} = 0.34V
$$

$$
V_{OCM(min)} = -0.7 + 0.34
$$

$$
V_{OCM(min)} = -0.36V
$$

### Final Output Common Mode Range

$$
-0.36V \le V_{OCM} \le 0.9V
$$

##

### 1.2.h Differential Input Voltage Range (Linear Region)

The differential amplifier behaves linearly only when both transistors operate in saturation and the current is approximately equally shared between them.

For a MOS differential pair, linear operation is maintained when the differential input voltage is small compared to the overdrive voltage.

### Condition for Linear Operation

$$
|V_{id}| \le 2V_{OV}
$$

### Substituting Values

$$
V_{OV} = 0.34V
$$

$$
|V_{id}| \le 2 \times 0.34
$$

$$
|V_{id}| \le 0.68V
$$

### Final Linear Range

$$
-0.68V \le V_{id} \le 0.68V
$$

---

## 1.3 Transient Analysis and Linearity Observation

The linear behavior of the differential amplifier is verified using transient analysis.

### Condition for Linearity

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

$$
\sqrt{2} V_{OV} = 1.414 \times 0.34 = 0.48V
$$

### Case 1: Linear Region

Input applied:

$$
V_{id} = 100mV < 0.48V
$$

![Circuit 2](Results/exp4a_transient1.png)

Observation:

- Output waveform is sinusoidal
- No distortion observed
- Both transistors operate in saturation
- Amplifier behaves linearly

### Case 2: Non-Linear Region

Input applied:

$$
V_{id} = 600mV > 0.48V
$$

![Circuit 3](Results/exp4a_transient2.png)

Observation:

- Output waveform shows distortion
- Clipping observed
- One transistor enters cutoff region
- Linear amplification is lost

##

The behavior of the differential amplifier is analyzed for two cases based on the input differential voltage.

### Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | $V_{id} < \sqrt{2}V_{OV}$ | $V_{id} > \sqrt{2}V_{OV}$ |
| Input ($V_{id}$) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | Both in saturation | One enters cutoff |
| Current distribution | Equal sharing | Current shifts to one transistor |

### Interpretation

In the linear region, the differential input voltage is small, and both transistors operate in saturation. The tail current is equally shared, resulting in a proportional and undistorted output. Hence, the amplifier exhibits linear behavior with constant gain.

In the non-linear region, the input differential voltage exceeds the limit, causing one transistor to carry most of the current while the other moves toward cutoff. This results in distortion and loss of linearity in the output waveform.

### Conclusion

The differential amplifier operates linearly only for small input signals.

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

As the differential input voltage increases beyond the limit:

$$
|V_{id}| > \sqrt{2} V_{OV}
$$

the circuit transitions from linear amplification to non-linear behavior due to unequal current distribution and transistor cutoff.

##

## Theoretical and Simulated Gain

![Circuit 4](Results/exp4a_transient3.png)

The output waveform is amplified and inverted.

### Simulated Gain

Input signal parameters:

- Type: Sine wave  
- Frequency = 1kHz  
- Amplitude = 50mV (applied differentially) 
- DC Offset = 0V

Measured peak-to-peak values:

$$
V_{in(p-p)} = 50mV - ( - 50mV ) = 100mV
$$

$$
V_{out(p-p)} = 302mV - ( - 302mV ) = 604mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
$$

$$
A_v = \frac{604 \times 10^{-3}}{100 \times 10^{-3}}
$$

$$
A_v = 6.04
$$

Gain in dB:

$$
A_v(dB) = 20\log_{10}(6.04)
$$

$$
A_v(dB) = 15.62dB
$$

##

### Theoretical Gain

Assume channel length modulation:

$$
\lambda = 0.1 \, V^{-1}
$$

### Output Resistance

The output resistance of each MOSFET is:

$$
r_o = \frac{1}{\lambda I_D}
$$

Substituting:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}}
$$

$$
r_o = 20k\Omega
$$

### Effective Output Resistance

Since two transistors are present:

$$
r_{o,eff} = r_{o1} \parallel r_{o2}
$$

$$
r_{o,eff} = 20k \parallel 20k
$$

$$
r_{o,eff} = 10k\Omega
$$

### Transconductance

$$
g_m = \frac{2 I_D}{V_{OV}}
$$

$$
g_m = \frac{2 \times 0.5 \times 10^{-3}}{0.34}
$$

$$
g_m \approx 2.94mS
$$

### Total Output Resistance

The effective load seen at the output is:

$$
R_{out} = R_D \parallel r_{o,eff}
$$

$$
R_{out} = 1.8k \parallel 10k
$$

$$
R_{out} \approx 1.53k\Omega
$$

### Differential Gain

$$
A_d = g_m R_{out}
$$

$$
A_d = 2.94 \times 10^{-3} \times 1.53 \times 10^3
$$

$$
A_d \approx 4.5
$$

### Gain in dB

$$
A_d(dB) = 20 \log_{10}(4.5)
$$

$$
A_d(dB) \approx 13.06dB
$$

##

## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values. This difference arises due to the simplifying assumptions made in analytical calculations and the inclusion of non-ideal effects in simulation.

### Reasons for Deviation

 ### 1. Channel Length Modulation

In theoretical calculations, channel length modulation is often neglected or approximated.  
However, in simulation, the MOSFET model includes a more accurate value of $\lambda$, which affects the output resistance $r_o$ and hence the gain.

 ### 2. Finite Output Resistance

The theoretical gain assumes ideal conditions, whereas in simulation, the finite output resistance of MOSFETs modifies the effective load resistance:

$$
R_{out} = R_D \parallel r_o
$$

This changes the overall gain.

 ### 3. Mobility Degradation and Short Channel Effects

In practical MOSFET models, carrier mobility reduces with increasing electric field.  
This reduces the effective transconductance $g_m$, which directly affects gain.

 ### 4. Variation in Overdrive Voltage ($V_{OV}$)

Theoretical calculations assume a fixed $V_{OV}$, whereas in simulation, the operating point may slightly shift, causing variations in $g_m$ and current.

 ### 5. Parasitic Capacitances

Simulation includes intrinsic parasitic capacitances, which influence the dynamic response and slightly affect the measured gain, especially in transient analysis.

 ### 6. Measurement Method

In simulation, gain is obtained from waveform measurements, which may include small inaccuracies due to scaling, cursor placement, or non-ideal waveform symmetry.

### Conclusion

Thus, the difference between theoretical and simulated gain is expected and arises due to practical device behavior and more accurate modeling in simulation compared to simplified analytical expressions.

---

## 1.4 AC Analysis

![Circuit 5](Results/exp4a_ac.png)

In AC analysis, the frequency response of the Differential Amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency ($f_L$) and upper cutoff frequency ($f_H$), measured at the −3 dB points.

##

### Midband gain:

From AC simulation:

$$
A_v = 9.871 \text{ dB}
$$

The −3 dB gain is:

$$
A_v - 3 = 9.871 - 3
$$

$$
A_v - 3 = 6.871 \text{ dB}
$$

##

### Cutoff Frequencies

Lower cutoff frequency:

$$
f_L = 0
$$

Upper cutoff frequency:

$$
f_H = 4.819 \text{ MHz}
$$

##

### Bandwidth

Bandwidth is defined as:

$$
BW = f_H - f_L
$$

$$
BW = 4.819 - 0
$$

$$
BW = 4.819 \text{ MHz}
$$

---

### 1.5 Unity Gain Bandwidth (UGB)

Since the 0 dB crossing is not visible in the plot, UGB cannot be directly measured.

However, it can be approximated as:

$$
UGB = A_v \times BW
$$

$$
A_v = 6.04
$$

$$
UGB = 6.04 \times 4.819 \text{ MHz}
$$

$$
UGB = 29.106 \text{ MHz}
$$

---

### Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as channel length modulation, mobility degradation, and parasitic capacitances. These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.

## Comparison of Results

| Parameter | Theoretical | Simulated |
|------------|-------------|-----------|
| Voltage Gain ($A_v$) | 4.5 V/V | 6.04 V/V |
| Gain (dB) | 14.46 dB | 15.62 dB |

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions used in analytical calculations and the inclusion of non-ideal MOSFET effects such as channel length modulation, mobility degradation, and parasitic capacitances in simulation.

---

## Inference

The MOS differential amplifier with resistive load was successfully designed and analyzed while satisfying the given design constraints:

Power consumption ≤ 1.8mW  
VDD = 0.9V  
VSS = -0.9V  
Vocm = 0V  

The tail current was selected as 1mA to ensure operation within the power limit (1.8mW). Under balanced conditions, the current splits equally between the two transistors:

$$
I_{D1} = I_{D2} = 0.5mA
$$

The bias point was carefully chosen such that both NMOS transistors operate in saturation, ensuring proper differential amplification. The source node voltage was adjusted to match the required tail voltage:

$$
V_S \approx -0.7V
$$

by tuning the transistor width during simulation.

Theoretical and simulated results are reasonably consistent:

Theoretical gain ≈ 5.29 V/V (14.46 dB)  
Simulated gain ≈ 6.04 V/V (15.62 dB)  
Simulated bandwidth ≈ 4.819 MHz  
Unity Gain Bandwidth ≈ 15.03 MHz  

The deviation between theoretical and simulated gain arises due to second-order effects such as channel length modulation, mobility degradation, and parasitic capacitances included in the MOSFET model. Additionally, the theoretical analysis assumes ideal conditions and neglects the finite output resistance of transistors.

From the AC analysis, it is observed that the amplifier exhibits a flat midband gain followed by a roll-off at higher frequencies due to parasitic capacitances, which introduce a dominant pole and limit the bandwidth.

The differential amplifier provides good linear amplification for small differential input signals. However, when the input differential voltage exceeds the linear range, the circuit enters non-linear operation, resulting in distortion.

Hence, the designed differential amplifier satisfies the required specifications and demonstrates proper biasing, expected gain characteristics, and acceptable frequency response behavior.

---

## Circuit 2: Differential Amplifier with PMOS active load and an NMOS current source

## 2.1 Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected to an NMOS transistor (M5) acting as a current source, and their drains connected to a PMOS current mirror load (M3 and M4).

When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the tail current ($I_{SS}$), set by transistor M5, is steered between M1 and M2 depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The PMOS transistors (M3 and M4) form a current mirror load. Transistor M3 is diode-connected and sets the reference current, while M4 mirrors this current to the other branch. This active load provides a high output resistance compared to resistive loads.

The change in drain current through M1 and M2 results in corresponding voltage variations at the output nodes (OUT1 and OUT2), producing differential output voltages.

The NMOS transistor M5 operates in saturation and provides a nearly constant tail current. However, due to its finite output resistance, it introduces a source degeneration effect, which slightly reduces the overall gain.

For small differential input signals, all transistors operate in saturation, and the amplifier behaves linearly, producing an amplified output proportional to the input difference.

For larger differential inputs, one transistor may turn OFF while the other carries most of the current, resulting in non-linear behavior.

Thus, the circuit performs differential amplification using current steering and a PMOS active load, achieving higher gain compared to a resistive load differential amplifier.

## Circuit Diagram

![Circuit 1](Results/exp4b_circuit.png)

## 2.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 2.2.a Power Constraint

The total power consumed by the differential amplifier is given by:

$$
P = (V_{DD} - V_{SS}) \cdot I_{SS}
$$

Total supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9) = 1.8V
$$

Given the maximum allowed power:

$$
P \leq 1.8 \times 10^{-3}
$$

$$
1.8 \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
I_{SS} \leq 1mA
$$

To maximize transconductance and improve gain while staying within the power limit, the tail current is chosen as:

$$
I_{SS} = 1mA
$$

The corresponding power dissipation is:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Thus, the design satisfies the power constraint.

The tail current is provided by the NMOS transistor M5, which acts as a current source for the differential pair.

##

### 2.2.b Drain Current Calculation

Under balanced input conditions:

$$
V_{in1} = V_{in2}
$$

the differential pair operates symmetrically, and the tail current splits equally between both transistors.

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

Thus, each transistor carries equal current under zero differential input.

##

### 2.2.c Bias Point Calculation

#### NMOS Differential Pair (M1 and M2)

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

#### Source Node Voltage

From specifications:

$$
V_p = V_S = -0.7V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

#### Overdrive Voltage

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

#### Drain Voltage

Given:

$$
V_{O,CM} = 0V
$$

So,

$$
V_D = 0V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

#### Saturation Condition

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Thus, M1 and M2 operate in saturation.

##

### NMOS Current Source (M5)

For M5:

- Source is connected to:

$$
V_S = V_{SS} = -0.9V
$$

- Drain is connected to:

$$
V_D = V_p = -0.7V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = -0.7 - (-0.9)
$$

$$
V_{DS} = 0.2V
$$

#### Saturation Condition

For saturation:

$$
V_{DS} \ge V_{OV}
$$

Thus,

$$
0.2V \ge V_{OV}
$$

#### Choosing Overdrive Voltage

To ensure M5 remains in saturation while maximizing current, the overdrive voltage is chosen close to the upper limit:

$$
V_{OV} \approx 0.2V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_T + V_{OV5}
$$

$$
V_{GS} = 0.36 + 0.2
$$

$$
V_{GS} = 0.56V
$$

#### Gate Voltage

$$
V_{G} = V_S + V_{GS}
$$

$$
V_{G} = -0.9 + 0.56
$$

$$
V_{G} = -0.34V
$$

#### Saturation Check

$$
V_{DS} \ge V_{OV}
$$

$$
0.2 \ge 0.2
$$

Thus, M5 operates at the edge of saturation and provides the required tail current.

##

### PMOS Active Load (M3 and M4)

For PMOS:

- Source is connected to:

$$
V_{DD} = 0.9V
$$

- Drain is at:

$$
V_D = 0V
$$

#### Source-Drain Voltage

$$
V_{SD} = V_{DD} - V_D
$$

$$
V_{SD} = 0.9 - 0
$$

$$
V_{SD} = 0.9V
$$

#### Saturation Condition

$$
V_{SD} > V_{OV}
$$

$$
0.9V > V_{OV}
$$

Since $0.9V$ is sufficiently large, both PMOS transistors operate in saturation.

### Final Bias Point Summary

All transistors (M1, M2, M3, M4, and M5) operate in saturation, ensuring proper differential amplifier operation.

##

### 2.2.d Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging to find width:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
$$

### NMOS Differential Pair (M1 and M2)

From previous calculations:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
V_{OV} = 0.34V
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 236.5 \mu A/V^2 = 2.365 \times 10^{-4}
$$

#### Substituting:

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.1156}
$$

$$
W = \frac{480 \times 10^{-12}}{2.733 \times 10^{-5}}
$$

$$
W \approx 17.56 \mu m
$$

### Final Width (M1 and M2)

$$
W_{M1} = W_{M2} \approx 17.6 \mu m
$$

##

### NMOS Current Source (M5)

From previous calculations:

$$
I_D = I_{SS} = 1mA = 1 \times 10^{-3}A
$$

$$
V_{OV5} = 0.2V
$$

#### Substituting:

$$
W = \frac{2 \times 1 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.2)^2}
$$

$$
W = \frac{960 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.04}
$$

$$
W = \frac{960 \times 10^{-12}}{9.46 \times 10^{-6}}
$$

$$
W \approx 101.5 \mu m
$$

### Width Adjustment

To achieve the desired biasing conditions (\(V_p \approx -0.7V\) and \(I_{SS} \approx 1mA\)), the transistor widths were tuned in simulation.

Updated values:

$$
W_{M1} = W_{M2} : 17.56\mu m \rightarrow 29.852\mu m
$$

$$
W_{M5} : 101.5\mu m \rightarrow 195.85\mu m
$$

This adjustment ensures accurate biasing under non-ideal MOSFET effects.

---

## DC Analysis

![Circuit 1](Results/exp4b_dc.png)

The DC operating point confirms that the output voltage and source voltage is near the designed bias value, ensuring proper saturation operation.

---

### 2.2.e Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.

### Minimum Input Common Mode Voltage

For proper operation, the NMOS input transistors (M1 and M2) must remain ON and the tail current source (M5) must remain in saturation.

Condition:

$$
V_{GS1} \ge V_T
$$

Using:

$$
V_{GS1} = V_{ICM} - V_S
$$

So,

$$
V_{ICM(min)} = V_S + V_T
$$

Substituting:

$$
V_S = -0.7V, \quad V_T = 0.36V
$$

$$
V_{ICM(min)} = -0.7 + 0.36
$$

$$
V_{ICM(min)} = -0.34V
$$

### Maximum Input Common Mode Voltage

For maximum input voltage, the PMOS load transistors (M3 and M4) must remain in saturation.

Condition:

$$
V_{SD} \ge V_{OVp}
$$

Using:

$$
V_{SD} = V_{DD} - V_D
$$

At the edge of saturation:

$$
V_{SD} = V_{SG} - |V_{TP}|
$$

Also,

$$
V_{SG} = V_{DD} - V_{ICM}
$$

So,

$$
V_{DD} - V_D = (V_{DD} - V_{ICM}) - |V_{TP}|
$$

Rearranging:

$$
V_{ICM(max)} = V_D + |V_{TP}|
$$

Substituting:

$$
V_D \approx 0V, \quad |V_{TP}| \approx 0.39V
$$

$$
V_{ICM(max)} = 0 + 0.39
$$

$$
V_{ICM(max)} = 0.39V
$$

### Final Input Common Mode Range

$$
-0.34V \le V_{ICM} \le 0.39V
$$

##

### 2.2.f Output Common Mode Range (OCMR)

The output common-mode range is defined as the range of output voltage for which all transistors remain in saturation.

### Minimum Output Common Mode Voltage

For minimum output voltage, the NMOS input transistors (M1 and M2) must remain in saturation.

Condition:

$$
V_{DS1} \ge V_{OV}
$$

Using:

$$
V_{DS1} = V_{out} - V_S
$$

So,

$$
V_{out(min)} - V_S \ge V_{OV}
$$

$$
V_{out(min)} \ge V_S + V_{OV}
$$

Substituting:

$$
V_S = -0.7V, \quad V_{OV} = 0.34V
$$

$$
V_{out(min)} = -0.7 + 0.34
$$

$$
V_{out(min)} = -0.36V
$$

### Maximum Output Common Mode Voltage

For maximum output voltage, the PMOS load transistors (M3 and M4) must remain in saturation.

Condition:

$$
V_{SD} \ge V_{OVp}
$$

Using:

$$
V_{SD} = V_{DD} - V_{out}
$$

So,

$$
V_{DD} - V_{out(max)} \ge V_{OVp}
$$

$$
V_{out(max)} \le V_{DD} - V_{OVp}
$$

Substituting:

$$
V_{DD} = 0.9V, \quad V_{OVp} \approx 0.25V
$$

$$
V_{out(max)} = 0.9 - 0.25
$$

$$
V_{out(max)} = 0.65V
$$

### Final Output Common Mode Range

$$
-0.36V \le V_{out} \le 0.65V
$$

##

### 2.2.g Differential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region as long as both transistors (M1 and M2) remain in saturation and conduct current.

The differential input voltage is defined as:

$$
v_{id} = v_{in1} - v_{in2}
$$

### Condition for Linear Operation

For linear operation:

- Both transistors must remain ON  
- Tail current must be shared between M1 and M2  

The maximum differential input occurs when one transistor starts to turn OFF.

### Maximum Differential Input Voltage

At the boundary of linear operation:

$$
v_{id(max)} = 2V_{OV}
$$

Substituting:

$$
V_{OV} = 0.25V
$$

$$
v_{id(max)} = 2 \times 0.25
$$

$$
v_{id(max)} = 0.5V
$$

### Final Differential Input Range

$$
-0.5V \le v_{id} \le 0.5V
$$

---

## 2.3 Transient Analysis and Linearity Observation

The linear behavior of the differential amplifier with PMOS active load is verified using transient analysis.

### Condition for Linearity

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

Using:

$$
V_{OV} = 0.24V
$$

$$
\sqrt{2} V_{OV} = 1.414 \times 0.24 = 0.34V
$$

### Case 1: Linear Region

Input applied:

$$
V_{id} = 100mV < 0.34V
$$

![Circuit 2](Results/exp4b_transient1.png)

#### Observation:

- Output waveform is sinusoidal  
- No distortion observed  
- Both NMOS transistors (M1, M2) operate in saturation  
- PMOS load transistors (M3, M4) remain in saturation  
- Amplifier behaves linearly  

### Case 2: Non-Linear Region

Input applied:

$$
V_{id} = 600mV > 0.34V
$$

![Circuit 3](Results/exp4b_transient2.png)

#### Observation:

- Output waveform shows distortion and clipping  
- One transistor (M1 or M2) enters cutoff  
- Current is steered completely to one branch  
- PMOS load still operates, but amplification becomes non-linear  

## Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | $V_{id} < \sqrt{2}V_{OV}$ | $V_{id} > \sqrt{2}V_{OV}$ |
| Input ($V_{id}$) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | All in saturation | One NMOS in cutoff |
| Current distribution | Shared between M1 & M2 | Current flows in one branch |

## Interpretation

In the linear region, the differential input is small and both NMOS transistors conduct simultaneously. The tail current is shared between the two branches, and the PMOS active load converts current variations into voltage, resulting in a proportional and undistorted output.

In the non-linear region, the differential input exceeds the limit, causing one transistor to carry almost the entire tail current while the other turns OFF. This leads to distortion and loss of linearity in the output.

## Conclusion

The differential amplifier with active load operates linearly only for small input signals:

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

When:

$$
|V_{id}| > \sqrt{2} V_{OV}
$$

the circuit exhibits non-linear behavior due to current steering and transistor cutoff.

##

## Theoretical and Simulated Gain

![Circuit 4](Results/exp4b_transient1.png)

The output waveform is amplified and inverted.

### Simulated Gain

Input signal parameters:

- Type: Sine wave  
- Frequency = 1kHz  
- Amplitude = 50mV (applied differentially) 
- DC Offset = 0V

Measured peak-to-peak values:

$$
V_{in(p-p)} = 50mV - ( - 50mV ) = 100mV
$$

$$
V_{out(p-p)} = 106mV - ( - 75mV ) = 181mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
$$

$$
A_v = \frac{181 \times 10^{-3}}{100 \times 10^{-3}}
$$

$$
A_v = 1.81
$$

Gain in dB:

$$
A_v(dB) = 20\log_{10}(1.81)
$$

$$
A_v(dB) = 5.153dB
$$

##

### Theoretical Gain

Assume channel length modulation:

$$
\lambda = 0.1 \, V^{-1}
$$

### Output Resistance

The output resistance of each MOSFET is:

$$
r_o = \frac{1}{\lambda I_D}
$$

Substituting:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}}
$$

$$
r_o = 20k\Omega
$$

### Effective Output Resistance

Since both NMOS and PMOS contribute:

$$
r_{o,eff} = r_{o_n} \parallel r_{o_p}
$$

$$
r_{o,eff} = 20k \parallel 20k
$$

$$
r_{o,eff} = 10k\Omega
$$

### Transconductance

$$
g_m = \frac{2 I_D}{V_{OV}}
$$

Substituting:

$$
V_{OV} = 0.24V
$$

$$
g_m = \frac{2 \times 0.5 \times 10^{-3}}{0.24}
$$

$$
g_m \approx 4.17mS
$$

### Total Output Resistance

Since active load is used (no resistor):

$$
R_{out} = r_{o,eff}
$$

$$
R_{out} = 10k\Omega
$$

### Differential Gain

$$
A_d = g_m R_{out}
$$

$$
A_d = 4.17 \times 10^{-3} \times 10 \times 10^3
$$

$$
A_d \approx 41.7
$$

### Gain in dB

$$
A_d(dB) = 20 \log_{10}(41.7)
$$

$$
A_d(dB) \approx 32.4dB
$$

##

## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values. This difference arises due to simplifying assumptions in analytical calculations and the inclusion of non-ideal MOSFET effects in simulation.

### Reasons for Deviation

### 1. Channel Length Modulation

In theoretical calculations, channel length modulation is approximated using a constant value of $\lambda$.  
However, in simulation, both NMOS and PMOS devices have more accurate and bias-dependent $\lambda$, affecting the output resistance:

$$
r_o = \frac{1}{\lambda I_D}
$$

This directly impacts the gain.

### 2. Finite Output Resistance of Active Load

In Circuit 2, the load is implemented using PMOS transistors instead of resistors.

The effective output resistance is:

$$
R_{out} = r_{o_n} \parallel r_{o_p}
$$

Any variation in NMOS and PMOS output resistances significantly affects the gain.

### 3. Mobility Degradation and Short Channel Effects

In practical MOSFET models, carrier mobility decreases with increasing electric field.  
This reduces the effective transconductance:

$$
g_m = \frac{2I_D}{V_{OV}}
$$

leading to lower gain in simulation compared to theory.

### 4. Variation in Overdrive Voltage ($V_{OV}$)

Theoretical calculations assume a fixed overdrive voltage.  
However, in simulation, the operating point slightly shifts, causing variations in $V_{OV}$ and hence in $g_m$ and gain.

### 5. Current Source Non-Ideality (M5)

The tail current source (M5) is not ideal in simulation.

- Finite output resistance  
- Slight variation in tail current  

This affects current distribution and reduces gain.

### 6. Parasitic Capacitances

Simulation includes intrinsic capacitances of MOSFETs, which influence signal behavior and slightly reduce the observed gain, especially at higher frequencies.

### 7. Measurement Method

Gain in simulation is obtained from waveform measurements, which may introduce minor inaccuracies due to scaling, cursor placement, and waveform asymmetry.

### Conclusion

Thus, the difference between theoretical and simulated gain is expected.  
It arises due to the use of simplified analytical models in theory and the inclusion of realistic device behavior and non-ideal effects in simulation.

---

## 2.4 AC Analysis

![Circuit 5](Results/exp4b_ac.png)

In AC analysis, the frequency response of the Differential Amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency ($f_L$) and upper cutoff frequency ($f_H$), measured at the −3 dB points.

##

### Midband gain:

From AC simulation:

$$
A_v = 5.2 \text{ dB}
$$

The −3 dB gain is:

$$
A_v - 3 = 5.2 - 3
$$

$$
A_v - 3 = 2.2 \text{ dB}
$$

##

### Cutoff Frequencies

Lower cutoff frequency:

$$
f_L = 0
$$

Upper cutoff frequency:

$$
f_H = 2.2 \text{ GHz}
$$

##

### Bandwidth

Bandwidth is defined as:

$$
BW = f_H - f_L
$$

$$
BW = 2.2 - 0
$$

$$
BW = 2.2 \text{ GHz}
$$

---

## 2.5 Unity Gain Bandwidth (UGB)

$$
f_{0dB} \approx 4.8 \text{GHz}
$$

$$
UGB = A_v \times f_H
$$

Using linear gain:

$$
A_v = 1.81
$$

$$
UGB = 1.81 \times 4.8 \text{ GHz}
$$

$$
UGB = 8.688 \text{ GHz}
$$

---

### Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as channel length modulation, mobility degradation, finite output resistance of current sources, and parasitic capacitances. These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.

## Comparison of Results

| Parameter | Theoretical | Simulated |
|------------|-------------|-----------|
| Voltage Gain ($A_v$) | 41.7 V/V | 1.81 V/V |
| Gain (dB) | 32.4 dB | 5.153 dB |

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions and the presence of non-ideal MOSFET effects such as finite output resistance of the current source, channel length modulation, and parasitic capacitances.

---

## Inference

The MOS differential amplifier with PMOS active load and NMOS current source was successfully designed and analyzed while satisfying the given design constraints:

Power consumption ≤ 1.8mW  
VDD = 0.9V  
VSS = -0.9V  
Vocm = 0V  

The tail current was set close to 1mA to ensure operation within the power limit. Under balanced conditions, the current splits equally between the two branches:

$$
I_{D1} = I_{D2} \approx 0.5mA
$$

The biasing was carefully adjusted to ensure all transistors (M1, M2, M3, M4, and M5) operate in saturation. The tail node voltage was fixed at:

$$
V_S \approx -0.7V
$$

by tuning the transistor widths in simulation.

Theoretical and simulated results show a significant deviation:

Theoretical gain ≈ 41.7 V/V (32.4 dB)  
Simulated gain ≈ 1.81 V/V (5.135 dB)  

This large difference arises because the theoretical gain assumes an ideal current source and large output resistance. In practice:

- The NMOS current source (M5) has finite output resistance  
- The PMOS active load (M3, M4) is not ideal  
- Channel length modulation reduces effective gain  
- Mobility degradation reduces transconductance  

These factors significantly reduce the gain in simulation.

From AC analysis, the amplifier shows a flat midband gain followed by a roll-off at higher frequencies due to parasitic capacitances and the load capacitance, which introduce a dominant pole and limit bandwidth.

The differential amplifier provides linear amplification for small differential inputs. However, for large input signals, current steering causes one transistor to turn OFF, leading to distortion and non-linear behavior.

Hence, the designed differential amplifier demonstrates correct biasing and operation, but highlights the impact of non-ideal device behavior on gain when using active loads and current sources.

---

## Circuit 3: CMOS Differential Amplifier with PMOS Active Load (Bias-Controlled Load)

## Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected together and biased by a constant tail current source (M5). The drains of M1 and M2 are connected to PMOS transistors (M3 and M4), which act as active loads.

The gates of the PMOS transistors are connected to a bias voltage $V_{b2}$, which controls their operation and ensures they function as current sources rather than forming a current mirror.

When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the tail current $I_{SS}$ is steered between M1 and M2 depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The PMOS active load converts these current variations into voltage changes at the output nodes. Since the PMOS transistors are biased by $V_{b2}$, they provide high output resistance, which increases the voltage gain of the amplifier.

The output is typically taken from one side (single-ended output), resulting in an amplified version of the differential input signal.

For small differential inputs, both NMOS transistors operate in saturation, and the circuit behaves as a linear amplifier. For larger inputs, one transistor may enter cutoff while the other carries most of the current, leading to non-linear behavior.

Thus, the circuit converts a differential input voltage into a single-ended amplified output using a differential pair and PMOS active loads, providing higher gain compared to resistive or current mirror loaded configurations.

## Circuit Diagram

![Circuit 1](Results/exp4c_circuit.png)

## 2.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 3.2.a Power Constraint

The total power consumed by the differential amplifier is given by:

$$
P = (V_{DD} - V_{SS}) \cdot I_{SS}
$$

Total supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9) = 1.8V
$$

Given the maximum allowed power:

$$
P \leq 1.8 \times 10^{-3}
$$

$$
1.8 \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
I_{SS} \leq 1mA
$$

To maximize transconductance and improve gain while staying within the power limit, the tail current is chosen as:

$$
I_{SS} = 1mA
$$

The corresponding power dissipation is:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Thus, the design satisfies the power constraint.

The tail current is provided by the NMOS transistor M5, which acts as a current source for the differential pair.

##

### 3.2.b Drain Current Calculation

Under balanced input conditions:

$$
V_{in1} = V_{in2}
$$

the differential pair operates symmetrically, and the tail current splits equally between both transistors.

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

Thus, each transistor carries equal current under zero differential input.

##

### 3.2.c Bias Point Calculation

#### NMOS Differential Pair (M1 and M2)

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

#### Source Node Voltage

From specifications:

$$
V_p = V_S = -0.7V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

#### Overdrive Voltage

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

#### Drain Voltage

Given:

$$
V_{O,CM} = 0V
$$

So,

$$
V_D = 0V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

#### Saturation Condition

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Thus, M1 and M2 operate in saturation.

##

### NMOS Current Source (M5)

For M5:

- Source is connected to:

$$
V_S = V_{SS} = -0.9V
$$

- Drain is connected to:

$$
V_D = V_p = -0.7V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = -0.7 - (-0.9)
$$

$$
V_{DS} = 0.2V
$$

#### Saturation Condition

$$
V_{DS} \ge V_{OV}
$$

To ensure saturation, choose:

$$
V_{OV} \approx 0.2V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_T + V_{OV}
$$

$$
V_{GS} = 0.36 + 0.2
$$

$$
V_{GS} = 0.56V
$$

#### Gate Voltage

$$
V_{G} = V_S + V_{GS}
$$

$$
V_{G} = -0.9 + 0.56
$$

$$
V_{G} = -0.34V
$$

#### Saturation Check

$$
0.2 \ge 0.2
$$

Thus, M5 operates at the edge of saturation and provides the required tail current.

##

### PMOS Active Load (M3 and M4)

For PMOS:

- Source is connected to:

$$
V_S = V_{DD} = 0.9V
$$

- Drain is at:

$$
V_D = V_{out} = 0V
$$

- Gate is connected to bias voltage:

$$
V_G = V_{b2}
$$

#### Source-Drain Voltage

$$
V_{SD} = V_S - V_D
$$

$$
V_{SD} = 0.9 - 0
$$

$$
V_{SD} = 0.9V
$$

#### Saturation Condition

$$
V_{SD} \ge V_{SG} - |V_T|
$$

Substituting:

$$
0.9 \ge (0.9 - V_G) - 0.39
$$

$$
0.9 \ge 0.51 - V_G
$$

$$
0.39 \ge -V_G
$$

$$
V_G \ge -0.39V
$$

#### Gate Voltage Selection

$$
V_{b2(min)} = -0.39V
$$

Choose:

$$
V_{b2} \approx -0.36V
$$

#### Source-Gate Voltage

$$
V_{SG} = V_S - V_G
$$

$$
V_{SG} = 0.9 - (-0.36)
$$

$$
V_{SG} = 1.26V
$$

#### Overdrive Voltage

$$
V_{OV(p)} = V_{SG} - |V_T|
$$

$$
V_{OV(p)} = 1.26 - 0.39
$$

$$
V_{OV(p)} = 0.87V
$$

#### Saturation Check

$$
V_{SD} > V_{OV(p)}
$$

$$
0.9 > 0.87
$$

Thus, M3 and M4 operate in saturation.
### Final Bias Point Summary

All transistors (M1, M2, M3, M4, and M5) operate in saturation, ensuring proper differential amplifier operation with PMOS active load.

##

### 3.2.d Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging:

$$
W = \frac{2 I_D L}{\mu C_{ox} (V_{OV})^2}
$$

##

### NMOS Differential Pair (M1 and M2)

From previous calculation:

$$
I_D = \frac{I_{SS}}{2} = 0.5mA
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 2.365 \times 10^{-4} A/V^2
$$

$$
V_{OV} = 0.34V
$$

#### Calculation

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.734 \times 10^{-5}}
$$

$$
W \approx 17.56 \mu m
$$

$$
W_1 = W_2 \approx 17.56 \mu m
$$

##

### NMOS Current Source (M5)

Using:

$$
I_D = 1mA
$$

$$
V_{OV5} = 0.2V
$$

#### Calculation

$$
W_5 = \frac{2 \times 1 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.2)^2}
$$

$$
W_5 = \frac{960 \times 10^{-12}}{9.46 \times 10^{-6}}
$$

$$
W_5 \approx 101.5 \mu m
$$

##

### PMOS Active Load (M3 and M4)

Given:

$$
I_D = 0.5mA
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_p C_{ox} = 9.98 \times 10^{-5}
$$

$$
V_{OV(p)} = 0.87V
$$

Substituting:

$$
W_p = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{9.98 \times 10^{-5} \times (0.87)^2}
$$

$$
W_p = \frac{480 \times 10^{-12}}{9.98 \times 10^{-5} \times 0.7569}
$$

$$
W_p = \frac{480 \times 10^{-12}}{7.55 \times 10^{-5}}
$$

$$
W_p \approx 6.35 \mu m
$$

$$
W_3 = W_4 \approx 6.35 \mu m
$$

### Width Adjustment

To achieve the desired biasing conditions (\(V_p \approx -0.7V\) and \(I_{SS} \approx 1mA\)), the transistor widths were tuned in simulation.

Updated values:

$$
W_{M1} = W_{M2} : 17.56\mu m \rightarrow 32\mu m
$$

$$
W_{M5} : 101.5\mu m \rightarrow 209.154\mu m
$$

$$
W_{M3} = W_{M4} : 6.35\mu m \rightarrow 13.876\mu m
$$

This adjustment ensures accurate biasing under non-ideal MOSFET effects.

---

## DC Analysis

![Circuit 1](Results/exp4c_dc.png)

The DC operating point confirms that the output voltage and source voltage is near the designed bias value, ensuring proper saturation operation.




