# Seismic Noise Attenuation using SVD
# seismic-svd-denoising

This repository contains a Python implementation for simulating a seismic shot record and attenuating linear noise (Air Waves) using **Singular Value Decomposition (SVD)**.

##  Project Overview
The goal of this project is to model a synthetic seismic dataset based on a specific earth model and then apply signal processing arrival techniques to separate signal from noise.

### Earth Model Specifications:
- **Structure:** One layer over a half-space.
- **Layer Thickness:** 500 m.
- **P-wave Velocities:** $V_{p1} = 2000$ m/s, $V_{p2} = 3500$ m/s.
- **Densities:** $\rho_1 = 2.2$ g/cm³, $\rho_2 = 2.6$ g/cm³.
- **Source:** Ricker Wavelet (Peak Frequency: 60 Hz).

### Survey Geometry:
- **Type:** Split-spread survey.
- **Stations:** 100 receivers.
- **Station Interval:** 50 m.
- **Near Offset:** 150 m.
- **Sampling Interval:** 4 ms.

##  Features
1. **Forward Modeling:** - Generation of Primary reflections.
   - Simulation of 1st, 2nd, and 3rd order surface multiples.
   - Addition of **Air Wave** ($V \approx 340$ m/s) as coherent linear noise.
2. **SVD Filtering:** - Decomposing the seismic section into singular values.
   - Identifying and removing the dominant components associated with the high-energy linear noise.
3. **Multi-Domain Analysis:**
   - Visualization in **T-X (Time-Space)** domain.
   - Visualization in **F-K (Frequency-Wavenumber)** domain to observe velocity-based separation.

##  Results
The code generates several plots, including:
- The raw shot record with air waves.
- The isolated noise component.
- The denoised seismic section.
- Singular value spectrum for filter threshold selection.

## How to Run
Ensure you have the following libraries installed:
```bash
pip install numpy matplotlib scipy