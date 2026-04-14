# Mathematical Foundations of SVD in Seismic Denoising

This document provides a deeper look into the mathematical framework used in this project to separate coherent noise from seismic signals.

## 1. Matrix Representation of Seismic Data
A seismic shot record can be represented as a matrix $\mathbf{A}$ of size $m \times n$, where $m$ is the number of time samples and $n$ is the number of traces (receivers).

## 2. Singular Value Decomposition (SVD)
The SVD theorem states that any matrix $\mathbf{A}$ can be factored as:
$$\mathbf{A} = \mathbf{U} \mathbf{\Sigma} \mathbf{V}^T$$

Where:
- $\mathbf{U}$: An $m \times m$ orthogonal matrix whose columns are the left singular vectors (representing the temporal characteristics).
- $\mathbf{\Sigma}$: An $m \times n$ diagonal matrix containing singular values $\sigma_1 \ge \sigma_2 \ge \dots \ge \sigma_r > 0$.
- $\mathbf{V}$: An $n \times n$ orthogonal matrix whose columns are the right singular vectors (representing the spatial characteristics/lateral continuity).

## 3. Eigenimage Decomposition
The matrix $\mathbf{A}$ can be rewritten as a sum of rank-1 matrices called **Eigenimages**:
$$\mathbf{A} = \sum_{i=1}^{k} \sigma_i \mathbf{u}_i \mathbf{v}_i^T$$

In seismic processing, coherent events with high energy and linear alignment (like **Air Waves**) are captured by the first few eigenimages (associated with the largest singular values $\sigma_i$).

## 4. Signal-Noise Separation Strategy
1. **Noise Modeling**: We identify that the Air Wave dominates the first eigenimage ($i=1$). 
   $$\mathbf{A}_{noise} \approx \sigma_1 \mathbf{u}_1 \mathbf{v}_1^T$$
2. **Filtering**: To obtain the denoised data ($\mathbf{A}_{signal}$), we subtract the noise model from the original data:
   $$\mathbf{A}_{signal} = \mathbf{A}_{original} - \mathbf{A}_{noise}$$
3. **Reconstruction**: The resulting matrix contains the hyperbolic reflections (primaries and multiples) which were previously masked by the linear noise.

## 5. Why SVD over f-k Filtering?
- **Non-periodic Noise**: Unlike f-k filters which assume periodicity and can create "gibbs-like" artifacts, SVD is purely data-driven.
- **Amplitude Preservation**: SVD better preserves the AVO (Amplitude Variation with Offset) characteristics of the underlying reflections because it operates on the principal components of the data energy.

---
