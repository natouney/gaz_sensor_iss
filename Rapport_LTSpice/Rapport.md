# Amplification Circuit for Gas Sensor with LTSpice Simulation

## Overview

The gas sensor made during the AIME internship has an extremely high resistance that varies depending on the type and presence of gas. Its resistance is approximately **1 GΩ**, resulting in an extremely low current in the **nanoampere (nA)** range flowing to the ADC. Using an Arduino with a 10-bit ADC necessitates amplifying the signal exiting the gas sensor. We designed an amplifier circuit based on an operational amplifier and simulated it using LTSpice.

Amplifying the signal allows us to avoid the need for expensive equipment like a €15,000 multimeter to measure the high resistance.

---

## Amplifying the Signal from the Sensor

### LTSpice Simulation

The amplifier uses **three different filters**, each with its own cutoff frequency. These filters are essential for shaping the signal and reducing noise. To accurately simulate the gas sensor's behavior, we created a custom sensor component in LTSpice that mimics its high resistance and response to gases.

### Circuit for Simulating the Sensor

*(Include the circuit diagram here)*

---

## Filter Design and Characterizing the Amplification

Below are the cutoff frequencies for each filter:

| Filter | Cutoff Frequency |
|--------|-------------------|
| 1      | 15 Hz            |
| 2      | 1.6 Hz           |
| 3      | 1.55 kHz         |

### Purpose of Each Filter
1. **First Filter (C1, R1, R5):**  
   Filters out noise originating from the gas sensor.
2. **Second Filter (C4, R3):**  
   Reduces the **50 Hz** noise from the power grid.
3. **Third Filter (C2, R4):**  
   Serves as an **anti-aliasing filter**, preventing signal distortion during digitization.

### LTSpice Circuit of the Amplifier

Below is the LTSpice circuit, integrating the gas sensor and filters:  
*(Include the amplifier circuit diagram here)*

---

## Formula for the Sensor Resistance

The gas sensor's resistance can be derived from the voltage measured by the ADC using the formula:

\[
R = \frac{V_{\text{ADC}}}{I_{\text{sensor}}}
\]

Where:  
- \( R \): Resistance of the gas sensor  
- \( V_{\text{ADC}} \): Voltage measured by the ADC (0 to +5V, represented by values from 0 to 1023 in the Arduino).  
- \( I_{\text{sensor}} \): Current through the sensor.

This formula ensures accurate measurements of sensor resistance, even for high resistance and low current values.

---

## Simulating Noise and Attenuation

In the LTSpice simulation, noise filtering was tested by observing changes in FFT and attenuation for specific configurations:
- At **50 Hz**, the attenuation achieved was **100 dB**, significantly reducing grid noise.
- At **7.5 kHz**, attenuation reached **30 dB**.

Adjustments to the second filter's capacitance showed its importance in mitigating **50 Hz noise**. For example:
- Reducing the capacitance increases the 50 Hz noise peak.
- A capacitance of **1000 μF** attenuates more noise but can distort the signal.

---

## Conclusion

This amplifier circuit ensures accurate measurement and analysis of gas sensor behavior, enabling the Arduino ADC to handle high resistance and low current signals. Through LTSpice simulation and optimization of filter configurations, we have effectively minimized noise and maximized signal integrity.

---
