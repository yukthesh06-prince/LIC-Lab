# Experiment 2 – Common Source Amplifier Variations

# Comparison of Experiment 2 Configurations (A, B, C)

| Parameter | Experiment A | Experiment B | Experiment C |
|------------|--------------|--------------|--------------|
| Source Element | Source Resistor (Rs) | NMOS Current Source | Diode-Connected NMOS |
| Active Load | PMOS | PMOS | PMOS |
| Drain Current ($I_D$) | 200 µA | 200 µA | 200 µA |
| Power Dissipation | 0.36 mW | 0.36 mW | 0.36 mW |
| Theoretical Gain (V/V) | 15.38 | 0.99 | 40 |
| Simulated Gain (V/V) | 24.53 | 2.45 | 25.05 |
| Simulated Gain (dB) | 27.79 dB | 7.78 dB | 27.97 dB |
| Bandwidth | 39.954 MHz | 42.59 MHz | 83.21 MHz |
| Unity Gain Bandwidth | 1.516 GHz | 104.35 MHz | 2.08 GHz |
| Degeneration Strength | Moderate | Strong | Reduced |

---

# Final Combined Conclusion – Experiment 2

In Experiment 2, three different Common Source amplifier configurations were analyzed using 180nm TSMC technology while satisfying the constraints:

- $V_{DD} = 1.8V$
- Power ≤ 1mW
- $C_L = 10pF$
- $I_D = 200\mu A$

All three circuits maintained power dissipation at 0.36mW and ensured that all transistors operated in the saturation region.

### Key Observations

**Experiment A (Source Resistor):**  
Provided moderate gain with stable biasing. The resistor introduced controlled degeneration, balancing gain and linearity.

**Experiment B (NMOS Current Source):**  
Showed the lowest gain due to strong source degeneration caused by the finite output resistance of the current source transistor. Although bias stability improved, gain reduced significantly.

**Experiment C (Diode-Connected NMOS):**  
Achieved higher gain compared to Experiment B because degeneration was reduced. The diode-connected transistor provided bias control while allowing better voltage amplification.

### Gain Trend

Gain relationship observed:

$$
A_v(C) > A_v(A) > A_v(B)
$$

Experiment C delivered the highest practical gain among the three configurations.

### Frequency Behavior

- Experiment C achieved the highest bandwidth and unity gain bandwidth.
- The dominant pole in all configurations was mainly due to load capacitance ($C_L$) and intrinsic MOSFET parasitic capacitances.
- Multi-pole behavior explains the difference between calculated UGB and 0 dB frequency.

### Deviation Between Theoretical and Simulated Results

In all three experiments, theoretical gain values differed from simulated results due to:

- Finite output resistances
- Channel length modulation
- Mobility degradation
- Short-channel effects
- Parasitic capacitances included in practical MOSFET models

First-order analytical expressions provide approximate gain, while simulation reflects realistic device behavior.

---

## Overall Conclusion

Experiment 2 demonstrates how different source implementations affect amplifier performance:

- Source resistors provide predictable degeneration.
- NMOS current sources improve bias stability but significantly reduce gain.
- Diode-connected NMOS offers a balance between bias control and gain improvement.

Thus, transistor-based active elements significantly influence voltage gain, bandwidth, and overall amplifier behavior in CMOS analog design.
