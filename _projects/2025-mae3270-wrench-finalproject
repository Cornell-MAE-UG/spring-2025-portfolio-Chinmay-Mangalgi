---
layout: project
title: Torque Wrench FEM Analysis
description: MAE 3270 Final Project
topics: Mechanics of Materials (MAE 3270)
image: /assets/images/cadmodel.png
---

The final project for this class involved designing a torque wrench that can not only apply a specified torque but also measure it using strain gauges. Starting from a steel baseline design, I evaluated structural performance using both hand calculations and finite element analysis (FEA). To improve sensitivity and reduce weight, I selected a new material using materials indices and updated the geometry while still meeting required safety factors for strength, fracture, and fatigue. I then verified the final design in ANSYS, extracted strain at the gauge location, and confirmed that the electrical output is sufficient for accurate torque measurement. The results below summarize the design decisions and analyses used to achieve a functional, instrumented torque wrench.

## 5.2.1 Results

### 1. Image(s) of CAD Model

![CAD Model - Key Dimensions](/assets/images/caddimension.png)

![Zoomed View of Drive Dimensions](/assets/images/cadthings.png)

The improved design uses a rectangular beam handle with dimensions h = 0.70 in (width in bending direction) and b = 0.35 in (thickness). The load is applied 16.0 in from the drive, and the strain gauges are positioned 15.0 in from the drive (1.0 in inboard from the load). A smooth 0.1 in fillet is included at the drive-handle transition to reduce stress concentrations as a design improvement. Total length of the wrench is 17 in.

### 2. Material Used & Mechanical Properties

**Material:** β-Ti alloy — Ti-12Mo-6Zr-2Fe (wrought, conservative values taken from Granta)

Material properties (use SI or imperial consistently; values below are in imperial units):

| Property | Value | Units / Notes |
|---|---:|---|
| Young’s Modulus, E | 13.1e6 | psi |
| Poisson’s Ratio, ν | 0.33 | — |
| Yield Strength, σ_y | 130e3 | psi (130 ksi) |
| Fracture Toughness, K_IC | 80.1e3 | psi·√in (80.1 ksi·√in) |
| Fatigue Strength (10^6 cycles) | 90e3 | psi (90 ksi) |

This alloy was selected after plotting normalized yield strength vs normalized fracture toughness.

### 3. FEM Loads & Boundary Conditions Diagram

![Loads and Boundary Conditions](/assets/images/ansysboundaryconditions.png)

The upper 0.4 in of the drive is fully constrained (fixed support, zero-displacement), per assignment instructions (marked with a yellow "A" on the model). A lateral force equivalent to T = 600 in·lb is applied at the load face, directed horizontally to produce the design bending (marked with a red "B").

### 4. Normal Strain Contours (Strain Gauge Direction)

![Normal Strain Contours](/assets/images/ansysmaxnormalstress.png)

Tensile on top and compressive on the bottom, as expected. Highlighted are the approximate nodes for the strain gauge location (node 2770) and the location of the true maximum normal strain (assuming no local stress concentrations).

### 5. Maximum Principal Stress Contour Plot

![Principal Stress Contour](/assets/images/ansysmaxprincipalstress.png)

The maximum principal stress reaches roughly 105 ksi near the clamped boundary / fillet region in the coarse view. A more detailed local view shows the true maximum principal stress in the 40–50 ksi range:

![Highlighted True Max Principal Stress](/assets/images/notfffake.png)

### 6. FEM Results Summary

- **Maximum Normal Stress:** 38,282 psi (at interface of clamping and fillet)
- **Max (Load) Point Deflection:** 0.4577 in

**Deformation plot:**
![Deformation Graph](/assets/images/ansysmaxdeformation.png)

**Strain distribution:**
![Strain Contour Plot](/assets/images/ansysstrain.png)

Highlighted strain gauge location on the handle surface:
![Strain Gauge Location](/assets/images/ansysstrainatgauge2.png)

FEM-calculated strain at the gauge location:
![FEM Calculated Strain at Gauge](/assets/images/ansysstrainatstraingauge.png)

The FEM strain at the gauge is approximately 1502 με (microstrain), which matches the theoretical bending-strain prediction.

### 7. Torque Wrench Sensitivity (mV/V)

Using the measured FEM strain at the gauge and a half-bridge configuration:

$$\frac{\Delta V}{V} = \frac{\mathrm{GF}\cdot\epsilon}{2}$$

- Gauge factor (GF) = 2.0
- ε (FEM) = 1502 × 10⁻⁶

Calculated output ≈ 1.5 mV/V at 600 in·lb, which exceeds the target sensitivity of 1.0 mV/V.

### 8. Strain Gauge Selected

- **Type:** 350 Ω linear foil gauge, 1-axis
- **Reference model:** Omega SGD-3-350-LY13
- **Gauge grid length:** ≈ 0.12 in (3 mm)
- **Grid width:** ≈ 0.08–0.12 in
- **Backing / package size:** ≈ 0.25 in × 0.15 in

The wrench handle has 0.70 in of flat width, so there is ample bonding area. Gauges are aligned longitudinally to measure bending strain with one on the top (tension) and one on the bottom (compression), arranged in a half-bridge for increased sensitivity.

The wrench handle has 0.70 in of flat width, so there is ample bonding area. Gauges are aligned longitudinally to measure bending strain with one on the top (tension) and one on the bottom (compression), arranged in a half-bridge for increased sensitivity.