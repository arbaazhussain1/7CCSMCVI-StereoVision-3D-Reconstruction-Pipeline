# 7CCSMCVI StereoVision 3D Reconstruction Pipeline

This repository contains the complete implementation of a **Stereo
Vision 3D Reconstruction Pipeline** developed for the King's College
London module **7CCSMCVI -- Computer Vision**.\
The coursework guides students through constructing a full stereo system
using **projective geometry**, **camera calibration**, **disparity
estimation**, **depth recovery**, and **3D reconstruction**.

This project builds all components **from scratch** to reinforce deep
understanding of geometric vision.

------------------------------------------------------------------------

## 1. Coursework Overview

The aim of this coursework is to simulate a stereo camera setup and
recover the 3D structure of a scene by using:

-   Camera intrinsics and extrinsics\
-   Projection matrices\
-   Direct Linear Transform (DLT) for calibration\
-   Disparity estimation\
-   Depth triangulation\
-   3D reconstruction

The pipeline produces a complete end-to-end stereo vision system that
projects 3D points into 2D views and then reconstructs them back into
3D.

------------------------------------------------------------------------

## 2. Key Mathematical Formulas

### 2.1 Camera Projection Model

A 3D point in homogeneous coordinates:

\[ X_h =
```{=tex}
\begin{bmatrix}
X \\ Y \\ Z \\ 1
\end{bmatrix}
```
\]

Camera projection:

\[ x_h = P X_h \]

Where:

\[ P = K \[R `\mid `{=tex}t\] \]

Pixel coordinates:

\[ u = `\frac{x}{w}`{=tex}, `\quad `{=tex}v = `\frac{y}{w}`{=tex} \]

------------------------------------------------------------------------

### 2.2 Intrinsic Camera Matrix

\[ K =
```{=tex}
\begin{bmatrix}
f & 0 & c_x \\
0 & f & c_y \\
0 & 0 & 1
\end{bmatrix}
```
\]

------------------------------------------------------------------------

### 2.3 DLT for Projection Matrix Estimation

\[ u_i (p_3\^T X_i) = p_1\^T X_i \]

\[ v_i (p_3\^T X_i) = p_2\^T X_i \]

Stack into:

\[ A p = 0 \]

Solve via SVD.

------------------------------------------------------------------------

### 2.4 Reprojection RMSE

\[ `\text{RMSE}`{=tex} = `\sqrt{
\frac{1}{N}
\sum_i 
[(u_i - \hat{u}_i)^2 + (v_i - \hat{v}_i)^2]
}`{=tex} \]

------------------------------------------------------------------------

### 2.5 Stereo Disparity

\[ d_i = u_i\^{left} - u_i\^{right} \]

------------------------------------------------------------------------

### 2.6 Depth Recovery

\[ Z_i = `\frac{f B}{d_i}`{=tex} \]

------------------------------------------------------------------------

### 2.7 Back-Projection to 3D

\[ X = `\frac{Z}{f}`{=tex}(u - c_x), `\quad`{=tex} Y =
`\frac{Z}{f}`{=tex}(v - c_y), `\quad`{=tex} Z = Z \]

------------------------------------------------------------------------

## 3. Pipeline Steps

1.  Simulate 3D box\
2.  Define stereo cameras and project 3D → 2D\
3.  Estimate projection matrices\
4.  Validate via reprojection error\
5.  Compute disparity and depth\
6.  Visualize disparity + depth\
7.  Reconstruct 3D points\
8.  Compare to ground truth

------------------------------------------------------------------------

## 4. Repository Structure

    .
    ├── ComputerVision_CourseWork_Fall202_v2.ipynb
    ├── README.md
    └── figures/

------------------------------------------------------------------------

## 5. Running Instructions

1.  Open notebook in Jupyter or Google Colab\
2.  Run cells top-to-bottom\
3.  View disparity, depth, reprojection error, and 3D reconstruction

------------------------------------------------------------------------

## 6. Learning Outcomes

You will understand:

-   Camera projection\
-   Stereo geometry\
-   Disparity-based depth\
-   DLT calibration\
-   3D reconstruction pipeline
