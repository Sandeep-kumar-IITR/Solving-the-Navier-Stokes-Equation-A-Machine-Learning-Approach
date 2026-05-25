# Physics-Informed Neural Networks for Navier–Stokes Equation

Implementation of a Physics-Informed Neural Network (PINN) to solve the 2D incompressible Navier–Stokes equations for the lid-driven cavity flow problem.

---

## Repository Structure

```bash
├── 20312032_report (1).pdf      # Full thesis report
├── README.md                    # Project documentation
├── re_100.ipynb                 # PINN training and analysis for Re = 100
├── re_400.ipynb                 # PINN training and analysis for Re = 400
├── re_1000.ipynb                # PINN training and analysis for Re = 1000
└── sandeep_kumar_20312032 (5).pdf
```

---

# Overview

This project uses **Physics-Informed Neural Networks (PINNs)** to approximate solutions of the incompressible Navier–Stokes equations without traditional mesh-based CFD solvers.

The model is tested on the classical **lid-driven cavity flow** benchmark problem for different Reynolds numbers.

The PINN framework embeds the governing PDEs directly into the neural network loss function using automatic differentiation.

---

# Governing Equations

## Continuity Equation

\[
\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} = 0
\]

## Momentum Equations

### X-Momentum

\[
u \frac{\partial u}{\partial x}
+
v \frac{\partial u}{\partial y}
=
-\frac{\partial p}{\partial x}
+
\nu
\left(
\frac{\partial^2 u}{\partial x^2}
+
\frac{\partial^2 u}{\partial y^2}
\right)
\]

### Y-Momentum

\[
u \frac{\partial v}{\partial x}
+
v \frac{\partial v}{\partial y}
=
-\frac{\partial p}{\partial y}
+
\nu
\left(
\frac{\partial^2 v}{\partial x^2}
+
\frac{\partial^2 v}{\partial y^2}
\right)
\]

---

# Problem Description

The lid-driven cavity problem consists of:

- A square cavity filled with incompressible fluid
- Top wall moving horizontally with constant velocity
- Remaining walls fixed

The flow generates:

- Primary vortices
- Secondary vortices
- Complex streamline patterns

---

# PINN Architecture

The neural network:

- Takes spatial coordinates \((x,y)\) as input
- Predicts:
  - Horizontal velocity \(u\)
  - Vertical velocity \(v\)
  - Pressure \(p\)

The loss function combines:

- PDE residual loss
- Boundary condition loss

Automatic differentiation is used to compute required derivatives.

---

# Training Details

| Parameter | Value |
|---|---|
| Optimizer | Adam |
| Activation | tanh |
| Collocation Points | 5000 |
| Boundary Points | 500 |
| Epochs | 50000 |
| Framework | TensorFlow |

---

# Reynolds Number Experiments

## Re = 100
- Smooth laminar flow
- Accurate vortex prediction
- Strong agreement with benchmark data

## Re = 400
- Captures secondary vortices
- Increased error near cavity walls

## Re = 1000
- Complex turbulent structures
- Higher approximation difficulty

---

# Results

The model successfully predicts:

- Velocity contours
- Streamlines
- Centerline velocity profiles
- Vortex locations

Results are validated against benchmark solutions from:

> Ghia et al. (1982)

---

# Technologies Used

- Python
- TensorFlow
- NumPy
- Matplotlib
- Automatic Differentiation

---

# Running the Notebooks

Open Jupyter Notebook:

```bash
jupyter notebook
```

Run any experiment notebook:

- `re_100.ipynb`
- `re_400.ipynb`
- `re_1000.ipynb`

---

# References

1. Raissi, M. et al.  
   *Physics-Informed Neural Networks*  
   Journal of Computational Physics (2019)

2. Ghia, U. et al.  
   *High-Re Solutions for Incompressible Flow Using Navier–Stokes Equations*  
   Journal of Computational Physics (1982)

---

# Author

**Sandeep Kumar**  
Integrated M.Sc. Applied Mathematics  
Indian Institute of Technology Roorkee
