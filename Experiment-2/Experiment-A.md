# Experiment 2A – CS Amplifier with Resistor Load

## Aim
To design a Common Source (CS) amplifier using an NMOS transistor with Source Degeneration and PMOS Active Load in 180nm TSMC technology in LTSpice with a supply voltage of 1.8V and power constraint less than or equal to 1mW, and to analyze its DC operating point, transient response, voltage gain, and bandwidth.

## Introduction

A Common Source (CS) amplifier is one of the most fundamental single-stage MOSFET amplifier configurations used in analog circuit design. In this configuration, the input signal is applied at the gate terminal, the output is taken from the drain, and the source terminal acts as the common reference node.

In this experiment, the CS amplifier is implemented using:

- An NMOS transistor as the amplifying device  
- A PMOS transistor as an active load  
- A source resistor $R_S$ for source degeneration  

##

### PMOS Active Load

Instead of using a passive resistor as the drain load, a PMOS transistor is used as an active load. An active load provides a higher output resistance $r_o$ compared to a physical resistor, which increases the voltage gain of the amplifier.

Since voltage gain of a CS amplifier is approximately:

$$
A_v \approx - g_m R_{out}
$$

Increasing $R_{out}$ results in higher gain.

##

### Source Degeneration

The source resistor $R_S$ introduces negative feedback in the circuit. This technique is called **source degeneration**.

With source degeneration, the voltage gain becomes:

$$
A_v \approx \frac{-g_m r_o}{1 + g_m R_S}
$$

Effects of source degeneration:

- Improves linearity  
- Stabilizes the operating point  
- Reduces sensitivity to device variations  
- Increases input dynamic range  

However, the gain is reduced due to the term $(1 + g_m R_S)$ in the denominator.

##

### What the Circuit Does

The CS amplifier with source degeneration and PMOS active load:

- Amplifies small input voltage signals  
- Produces an inverted output signal (180° phase shift)  
- Operates with the transistor in saturation region  
- Provides improved bias stability and linear performance  

This configuration is widely used in analog integrated circuits where moderate gain, better linearity, and stable biasing are required.

---

## Working Principle

The NMOS transistor $M_1$ operates in the saturation region and acts as the amplifying device. A small variation in the input voltage $v_{in}$ produces a change in gate-to-source voltage $V_{GS}$, which in turn changes the drain current according to:

$$
i_d = g_m v_{gs}
$$

This change in drain current flows through the PMOS active load, creating a voltage variation at the output node:

$$
v_{out} = - i_d R_{out}
$$

The negative sign indicates a 180° phase inversion between input and output.

The source resistor $R_S$ introduces negative feedback. As drain current increases, the source voltage rises, reducing $V_{GS}$ and stabilizing the operating point. This improves linearity but reduces the gain:

$$
A_v \approx \frac{-g_m r_o}{1 + g_m R_S}
$$

Thus, the circuit provides controlled voltage amplification with improved stability and linearity.
