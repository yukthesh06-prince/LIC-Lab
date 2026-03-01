# Experiment 2B – CS Amplifier with PMOS Active Load and NMOS Current Source

##  Aim

To design a Common Source (CS) amplifier using an NMOS transistor with NMOS Current Source and PMOS Active Load in 180nm TSMC technology in LTSpice with a supply voltage of 1.8V and power constraint less than or equal to 1mW, and to analyze its DC operating point, transient response, voltage gain, and bandwidth

## 📘 Introduction

The Common Source (CS) amplifier is one of the most fundamental and widely used MOSFET amplifier configurations in analog circuit design. In this experiment, a CS amplifier is implemented using:

- An NMOS transistor (M1) as the amplifying device  
- An NMOS transistor (M3) as a current source (replacing the source resistor)  
- A PMOS transistor (M2) as an active load  

## PMOS Active Load (M2)

Instead of using a passive resistor as the drain load, a **PMOS transistor (M2)** is used as an active load.

An active load provides a much higher small-signal output resistance $r_o$ compared to a physical resistor. This increases the effective output resistance of the amplifier.

Since the voltage gain of a CS amplifier is approximately:

$$
A_v \approx -g_{m1} R_{out}
$$

where:

$$
R_{out} \approx r_{o1} \parallel r_{o2}
$$

Increasing $R_{out}$ directly increases the voltage gain.

Thus, the PMOS active load helps in achieving higher gain without using large physical resistors.

## NMOS Current Source (M3)

In this experiment, the source resistor is replaced by an **NMOS current source transistor (M3)**.

M3 is biased in saturation and behaves like a constant current source.  
It provides:

- Stable bias current
- Better control over operating point
- Improved integration compatibility

However, because M3 has finite transconductance $g_{m3}$, it introduces a source degeneration effect.

## Source Degeneration Effect Using M3

Due to the small-signal behavior of M3, the effective voltage gain becomes:

$$
A_v \approx \frac{-g_{m1}(r_{o1} \parallel r_{o2})}{1 + \frac{g_{m1}}{g_{m3}}}
$$

This term:

$$
\left(1 + \frac{g_{m1}}{g_{m3}}\right)
$$

acts similarly to the classical source degeneration term:

$$
(1 + g_m R_S)
$$

##

### Effects of NMOS Current Source Degeneration

- Improves bias stability  
- Reduces dependence on resistor values  
- Improves linearity  
- Enhances output resistance  

However,

The voltage gain is reduced due to the degeneration term in the denominator.

##

## Overall Function of the Circuit

This amplifier:

- Amplifies small input signals
- Produces 180° phase inversion
- Uses transistor-based biasing instead of resistors
- Achieves moderate gain with improved bias stability
- Is fully compatible with CMOS IC fabrication

This configuration is commonly used in:

- Differential amplifier stages  
- Current mirror loaded amplifiers  
- Analog IC gain stages  
- Operational amplifier design  

In summary, this circuit demonstrates how replacing passive resistors with MOSFET-based active elements affects gain, bias stability, and overall amplifier performance.

---

## Working Principle

The NMOS transistor M1 operates in the saturation region and acts as the amplifying device. A small variation in the input voltage $v_{in}$ produces a change in gate-to-source voltage $V_{GS1}$, which changes the drain current according to:

$$
i_d = g_{m1} v_{gs1}
$$

This change in drain current flows through the PMOS active load M2, producing a voltage variation at the output node:

$$
v_{out} = - i_d R_{out}
$$

where:

$$
R_{out} \approx r_{o1} \parallel r_{o2}
$$

The negative sign indicates a 180° phase inversion between input and output.

The NMOS transistor M3 acts as a current source and introduces a degeneration effect. Due to its finite transconductance $g_{m3}$, the gain becomes:

$$
A_v \approx \frac{-g_{m1}(r_{o1} \parallel r_{o2})}{1 + \frac{g_{m1}}{g_{m3}}}
$$

Thus, the circuit provides voltage amplification with improved bias stability and linearity, though with slightly reduced gain compared to a simple CS amplifier.

---

