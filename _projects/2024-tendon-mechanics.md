---
layout: project
title: "Tendon Mechanical Testing Automation for Data Analysis"
description: MATLAB Analysis
technologies: [MATLAB]
image: /assets/images/1_marked.png
---

## Tendon Mechanical Testing Automation (MATLAB)

This project involved writing a MATLAB script to automate the analysis of mechanical testing data from supraspinatus tendon samples. The script processes raw load-displacement CSV data to compute stress-strain curves, extract mechanical properties, and visualize viscoelastic behavior through relaxation and hysteresis.

![Stress-Strain Plot with Best-Fit Line](/assets/images/1_marked.png){: .inline-image-r style="width: 300px" }

---

### Key Features

- **Automated elastic modulus detection** using sliding-window regression with R² thresholding
- **Stress relaxation analysis** after a specified hold period
- **Hysteresis quantification** across five load-unload cycles
- **Clean, reproducible visualizations** for reports or presentations

---

### Highlighted Code: Elastic Modulus Detection

```matlab
% Compute modulus from best-fit line where R² ≥ 0.95
p = polyfit(strain_window, stress_window, 1);
R2 = 1 - sum((stress_window - polyval(p, strain_window)).^2) ...
         / sum((stress_window - mean(stress_window)).^2);
if R2 > 0.95
    E = p(1); % Elastic modulus in MPa
end
```

The script searches over all time windows in the pull-to-failure segment to find the linear region with the steepest slope and acceptable fit quality, representing the true elastic modulus of the sample.

---

### Stress Relaxation Example

```matlab
peak_stress = max(stress(time >= 315 & time <= 320));
stress_150s = stress(find_nearest(time, 465));
relaxation_ratio = stress_150s / peak_stress;
```

This section computes how much the tendon relaxes after being held under constant strain, quantifying its viscoelasticity by comparing stress decay over time.

---

### Hysteresis Visualization

```matlab
AUC_load = trapz(strain_load, stress_load);
AUC_unload = trapz(flip(strain_unload), flip(stress_unload));
hysteresis = AUC_load - AUC_unload;
```

For each of the last five cycles of loading and unloading, hysteresis loops are plotted and the energy dissipated (loop area) is calculated to assess tendon fatigue behavior.

---

### Future Improvements

In the future, I’d like to:
- Add batch processing for multi-sample datasets
- Incorporate time-dependent viscoelastic models 
- Integrate plotting with export-ready figures using MATLAB's `exportgraphics`
