# Experiment 1 – Common Source (CS) Amplifier

## 1. Introduction

### What is a Common Source Amplifier?

A Common Source (CS) amplifier is a single-stage MOSFET amplifier configuration in which the source terminal is common to both input and output. 

- Input is applied at the gate
- Output is taken from the drain
- Source is connected to ground

It is the MOSFET equivalent of the Common Emitter amplifier in BJT.

The CS amplifier provides:
- Voltage amplification
- 180° phase inversion
- High input impedance

---

## 2. Working Principle

For amplification, the MOSFET must operate in the saturation region.

Condition for saturation:

VDS ≥ VGS − VT

When a small AC signal is applied at the gate:

- Increase in VGS → Increase in ID
- Increased ID causes larger voltage drop across RD
- Drain voltage decreases

Thus,
Input increases → Output decreases  
Input decreases → Output increases  

This results in 180° phase shift between input and output.

The small signal voltage gain is given by:

Av = − gm × RD

---

---

## Circuit Schematic

![CS Amplifier Circuit](Results/circuit.png)

## 3. Design Calculations

### 3.1 Power Constraint

Given:
VDD = 1.8V  
P ≤ 1mW  

Power:
P = VDD × ID  

1.8 × ID ≤ 1 × 10⁻³  

ID ≤ 555.5 µA  

For safe operation, choose:
ID = 200 µA  

Power dissipated:
P = 1.8 × 200µA = 0.36mW  

Since 0.36mW < 1mW, power constraint is satisfied.

---

### 3.2 Bias Point Selection

For maximum symmetrical output swing:

VDS ≈ VDD / 2  
VDS = 0.9V  

Since source is grounded:

VGS = VG − VS  
VGS = 0.9 − 0  
VGS = 0.9V  

Threshold voltage (from library):
VT = 0.36V  

Overdrive voltage:
VOV = VGS − VT  
VOV = 0.9 − 0.36  
VOV = 0.54V  

---

## DC Analysis

![DC Analysis](Results/dc.png)

DC Operating Point :

![Imabe](Results/values.png)

### 3.3 Drain Resistance (RD)

Vout = VDD − ID RD  

RD = (VDD − Vout) / ID  

RD = (1.8 − 0.9) / 200µA  
RD = 4.5kΩ  

---

### 3.4 Width Calculation (W)

Drain current equation in saturation:

ID = (µn Cox / 2) × (W/L) × (VOV)²  

From technology library:

µnCox = 2.365 × 10⁻⁴  

Substituting values:

200 × 10⁻⁶ = (2.365 × 10⁻⁴ / 2) × (W / 560 × 10⁻⁹) × (0.54)²  

Solving:

W ≈ 3.24 µm  

After simulation tuning to match ID = 200µA:

Final W = 4.09 µm  

---

### 3.5 Theoretical Voltage Gain

gm = 2ID / VOV  

gm = (2 × 200µA) / 0.54  
gm = 0.00074 S  

Voltage gain:

Av = − gm RD  

Av = − (0.00074 × 4500)  
Av ≈ −3.33 V/V  

Gain in dB:

Av(dB) = 20 log₁₀ (3.33)  
Av(dB) ≈ 10.45 dB  

---

### 3.6 Bandwidth Estimation

Dominant pole frequency:

fp = 1 / (2π RD CL)  

fp = 1 / (2π × 4.5k × 10pF)  

fp ≈ 3.53 MHz  

Simulated high frequency cutoff:
fH ≈ 3.67 MHz  

Bandwidth ≈ 3.67 MHz  

---

### Note

Channel length modulation is neglected in first-order theoretical analysis.
