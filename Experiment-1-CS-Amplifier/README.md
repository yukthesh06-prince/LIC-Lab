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
