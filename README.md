# PID-Controlled Infant Incubator System

> **A Closed-Loop Control System Simulation for Neonatal Thermal Regulation.**

[![Tool](https://img.shields.io/badge/Tool-MATLAB%20%7C%20Simulink-orange)]()
[![Type](https://img.shields.io/badge/Control-PI_Feedback_Loop-blue)]()

## Project Overview
Premature infants lack the ability to regulate body temperature effectively, making them prone to hypothermia. This project models and simulates an **Automatic Temperature Control System** for a neonatal incubator.

Using a **PI (Proportional-Integral) Controller**, the system regulates the heater output to maintain a stable air temperature of $37^\circ C$, ensuring the infant's body temperature remains within the safe physiological range.

## Mathematical Modeling
The system was modeled in Simulink using **First-Order Transfer Functions** to represent the thermal thermodynamics.

### 1. The Controller (PI)
* **Gains Tuned:** $K_p = 5$, $K_i = 1$.
* **Mechanism:** Feedback loop minimizes error $e(t) = r(t) - y(t)$.

### 2. Plant Dynamics (Transfer Functions)
* **Air Heating Model:** Represents the heater warming the air.
  $$G_{air}(s) = \frac{0.1}{10s + 1}$$
* **Infant Thermal Model:** Represents the baby absorbing heat from the air.
  $$G_{baby}(s) = \frac{0.2}{5s + 1}$$
* **Sensor Dynamics:** A low-pass filter simulates realistic sensor lag.
  $$F(s) = \frac{1}{0.01s + 1}$$

## Simulink Model
![System Diagram](https://github.com/YOUR-USERNAME/PID-Neonatal-Incubator-Control/blob/main/simulink_model.png?raw=true)
*Figure 1: Complete Closed-Loop Block Diagram showing the PI Controller, Sensor Feedback Filter, and Thermal Plant Models.*

## Simulation Results
The system was tested with a Unit Step Reference of $37^\circ C$ over a 50-second duration.

| Performance Metric | Air Temperature ($T_{air}$) | Baby Temperature ($T_{baby}$) |
| :--- | :--- | :--- |
| **Rise Time** | **2.55 s** (Fast Heating) | 7.68 s (Gradual Warming) |
| **Settling Time** | 15.90 s | 11.64 s |
| **Overshoot** | 18.32% | **1.72%** (Safe for Skin) |
| **Steady State** | Stable at $37^\circ C$ | Stable at $37^\circ C$ |

### Response Graph
![Results](https://github.com/YOUR-USERNAME/PID-Neonatal-Incubator-Control/blob/main/response_graph.png?raw=true)
*Figure 2: The Red line ($T_{air}$) heats up quickly to warm the environment, while the Blue line ($T_{baby}$) rises smoothly without dangerous overshoot.*

## Repository Contents
* **Project Report:** Full documentation of mathematical derivation and transfer functions.
* **Simulation File:** `.slx` source file for NI Simulink.
* **MATLAB Scripts:** Code for plotting step response metrics.

## Author
**Amna Yousuf **
*Biomedical Engineering Student, SSUET*

---
*Developed for Course BM-351L (Control Systems).*
