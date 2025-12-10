---
layout: project
title: Torque Wrench FEM Analysis
description: MAE 3270 Final Project
topics: Mechanics of Materials (MAE 3270)
image: /assets/images/cadmodel.png
---

<p>
  The final project for this class involved designing a torque wrench that can not only apply a specified
  torque but also measure it using strain gauges. Starting from a steel baseline design, I evaluated
  structural performance using both hand calculations and finite element analysis (FEA). To improve
  sensitivity and reduce weight, I selected a new material using materials indices and updated the geometry
  while still meeting required safety factors for strength, fracture, and fatigue. I then verified the
  final design in ANSYS, found the strain at the gauge location, and confirmed that the electrical output is
  sufficient for accurate torque measurement. The results below summarize the design decisions and analyses
  I used to design a functional, instrumented torque wrench.
</p>

<h2>5.2.1 Results</h2>

<h3>1. Image(s) of CAD Model</h3>

<figure>
  <img src="{{ '/assets/images/caddimension.png' | relative_url }}" alt="CAD Model - Key Dimensions">
  <figcaption>CAD model of the torque wrench with key dimensions.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/images/cadthings.png' | relative_url }}" alt="Zoomed View of Drive Dimensions">
  <figcaption>Zoomed-in view of the drive and handle transition region.</figcaption>
</figure>

<p>
  The improved design uses a rectangular beam handle with dimensions
  <em>h</em> = 0.70 in (width in bending direction) and <em>b</em> = 0.35 in (thickness). The load is applied
  16.0 in from the drive, and the strain gauges are positioned 15.0 in from the drive (1.0 in inwards from
  the load). A smooth 0.1 in fillet is included at the drive–handle transition to reduce stress
  concentrations as a design improvement. Total length of the wrench is 17 in.
</p>

<h3>2. Material Used &amp; Mechanical Properties</h3>

<p>
  <strong>Material:</strong> β-Ti alloy — Ti-12Mo-6Zr-2Fe (conservative values taken from Granta)
</p>

<p>Material properties (imperial units):</p>

<table>
    <thead>
        <tr>
            <th>Property</th>
            <th style="text-align:right;">Value</th>
            <th>Units</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Young's Modulus, E</td>
            <td style="text-align:right;">13.1 × 10<sup>3</sup></td>
            <td>ksi</td>
        </tr>
        <tr>
            <td>Poisson's Ratio, ν</td>
            <td style="text-align:right;">0.33</td>
            <td>—</td>
        </tr>
        <tr>
            <td>Yield Strength, σ<sub>y</sub></td>
            <td style="text-align:right;">130</td>
            <td>ksi</td>
        </tr>
        <tr>
            <td>Fracture Toughness, K<sub>IC</sub></td>
            <td style="text-align:right;">80.1</td>
            <td>ksi·√in</td>
        </tr>
        <tr>
            <td>Fatigue Strength (10<sup>6</sup> cycles)</td>
            <td style="text-align:right;">90</td>
            <td>ksi</td>
        </tr>
    </tbody>
</table>

<p>
  This alloy was selected after plotting normalized yield strength versus normalized fracture toughness and
  choosing a material that improved weight and toughness while still meeting strength and fatigue
  requirements.
</p>

<h3>3. FEM Loads &amp; Boundary Conditions Diagram</h3>

<figure>
  <img src="{{ '/assets/images/ansysboundaryconditions.png' | relative_url }}"
       alt="Loads and Boundary Conditions in ANSYS">
  <figcaption>Loads and boundary conditions used in the FEM model.</figcaption>
</figure>

<p>
  The upper 0.4 in of the drive is fully constrained (fixed support, zero displacement), per assignment
  instructions (marked with a yellow “A” in the model). A lateral force equivalent to
  <em>T</em> = 600 in·lb is applied at the load face, directed horizontally to produce the design bending
  (marked with a red “B”).
</p>

<h3>4. Normal Strain Contours (Strain Gauge Direction)</h3>

<figure>
  <img src="{{ '/assets/images/ansysmaxnormalstress.png' | relative_url }}"
       alt="Normal Strain Contours in ANSYS">
  <figcaption>Normal strain contours in the bending direction along the handle.</figcaption>
</figure>

<p>
  The strain field is tensile on the top surface and compressive on the bottom surface, as expected for
  simple bending. Highlighted are the approximate nodes for the strain gauge location (node 2770) and the
  location of the true maximum normal strain, neglecting local stress concentrations.
</p>

<h3>5. Maximum Principal Stress Contour Plot</h3>

<figure>
  <img src="{{ '/assets/images/ansysmaxprincipalstress.png' | relative_url }}"
       alt="Maximum Principal Stress Contour">
  <figcaption>Global view of maximum principal stress along the wrench.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/images/notfffake.png' | relative_url }}"
       alt="Zoomed View of True Maximum Principal Stress">
  <figcaption>Zoomed view of the true maximum principal stress in the fillet region.</figcaption>
</figure>

<p>
  In the zoomed view, the maximum principal stress appears to reach roughly 105 ksi near the clamped
  boundary and fillet region. A more refined local mesh shows that the true maximum principal stress is in
  the 40–50 ksi range, which is the value used for safety-factor calculations.
</p>

<h3>6. FEM Results Summary</h3>

<ul>
  <li><strong>Maximum Normal Stress:</strong> 38,282 psi (at interface between clamping region and fillet)</li>
  <li><strong>Maximum Load-Point Deflection:</strong> 0.4577 in</li>
</ul>

<figure>
  <img src="{{ '/assets/images/ansysmaxdeformation.png' | relative_url }}"
       alt="Deformation Plot in ANSYS">
  <figcaption>Deformation plot showing the deflected shape at full load.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/images/ansysstrain.png' | relative_url }}"
       alt="Strain Distribution Contour">
  <figcaption>Overall strain distribution along the wrench handle.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/images/ansysstrainatgauge2.png' | relative_url }}"
       alt="Strain Gauge Location on Handle">
  <figcaption>Highlighted strain gauge location on the top surface of the handle.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/images/ansysstrainatstraingauge.png' | relative_url }}"
       alt="FEM Strain at Gauge Node">
  <figcaption>FEM-calculated strain at the gauge node.</figcaption>
</figure>

<p>
  The FEM strain at the gauge location is approximately 1502&nbsp;με (microstrain), which alings with
  the theoretical bending-strain prediction from hand calculations.
</p>

<h3>7. Torque Wrench Sensitivity (mV/V)</h3>

<p>
  For a half-bridge configuration, the bridge output is given approximately by:
</p>

<p style="margin-left:1rem;">
  ΔV / V = (GF · ε) / 2
</p>

<ul>
  <li>Gauge factor, GF = 2.0</li>
  <li>Strain at gauge, ε = 1502 × 10⁻⁶</li>
</ul>

<p>
  Substituting these values gives an output of approximately 1.5 mV/V at 600 in·lb, which exceeds the
  target sensitivity of 1.0 mV/V and indicates that the strain gauge signal is large enough for reliable
  measurement.
</p>

<h3>8. Strain Gauge Selection</h3>

<ul>
  <li><strong>Type:</strong> 350&nbsp;Ω linear foil gauge, 1-axis</li>
  <li><strong>Reference model:</strong> Omega SGD-3-350-LY13</li>
  <li><strong>Gauge grid length:</strong> ≈ 0.12 in (3 mm)</li>
  <li><strong>Grid width:</strong> ≈ 0.08–0.12 in</li>
  <li><strong>Backing / package size:</strong> ≈ 0.25 in × 0.15 in</li>
</ul>

<p>
  The wrench handle has 0.70 in of flat width, so there is ample bonding area for the gauges. The gauges
  are aligned longitudinally to measure bending strain, with one on the top surface (tension) and one on
  the bottom surface (compression), arranged in a half-bridge to increase sensitivity and provide some
  temperature compensation.
</p>
