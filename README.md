# Solving the 2D Navier–Stokes Equations with a PINN

This project applies a Physics-Informed Neural Network (PINN) to the lid-driven cavity problem for an incompressible fluid. The notebooks explore three Reynolds numbers: 100, 400 and 1000.

The work was part of my Applied Mathematics studies at IIT Roorkee.

## Problem

The lid-driven cavity is a standard fluid-mechanics test case: the top wall moves at a fixed horizontal velocity while the other three walls remain stationary. The resulting flow is governed by the incompressible continuity and momentum equations.

Using velocity components (u,v), pressure (p), density (ho) and kinematic viscosity (
u):

[
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0
]

[
u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}
=-\frac{1}{\rho}\frac{\partial p}{\partial x}
+\nu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right)
]

[
u\frac{\partial v}{\partial x}+v\frac{\partial v}{\partial y}
=-\frac{1}{\rho}\frac{\partial p}{\partial y}
+\nu\left(\frac{\partial^2v}{\partial x^2}+\frac{\partial^2v}{\partial y^2}\right)
]

The PINN takes spatial coordinates as input and predicts velocity and pressure. Automatic differentiation is used to form the PDE residuals, which are combined with boundary-condition terms in the training loss.

## Experiments

| Notebook | Reynolds number |
|---|---:|
| `re_100.ipynb` | 100 |
| `re_400.ipynb` | 400 |
| `re_1000.ipynb` | 1000 |

The notebooks use TensorFlow and include training and flow-field analysis. The original experiment settings recorded in the project are:

- Optimizer: Adam
- Activation: tanh
- Collocation points: 5,000
- Boundary points: 500
- Training epochs: 50,000

These are the recorded notebook settings; they are not a guarantee that every run converges to the same result.

## Repository contents

- `re_100.ipynb`, `re_400.ipynb`, `re_1000.ipynb` — experiments at different Reynolds numbers.
- `20312032_report (1).pdf` — project report.
- `sandeep_kumar_20312032 (5).pdf` — accompanying report document.

## Run the notebooks

Use a Python environment with Jupyter, TensorFlow, NumPy and Matplotlib installed. TensorFlow installation depends on the operating system and available hardware, so choose a version compatible with your setup.

```bash
python -m venv .venv
# Windows: .venv\\Scripts\\activate
# macOS/Linux: source .venv/bin/activate
pip install numpy matplotlib jupyter tensorflow
jupyter notebook
```

Open one of the three experiment notebooks and execute the cells in order.

## References

- Raissi, M., Perdikaris, P. and Karniadakis, G. E. (2019), *Physics-informed neural networks: A deep learning framework for solving forward and inverse problems involving nonlinear partial differential equations*, Journal of Computational Physics.
- Ghia, U., Ghia, K. N. and Shin, C. T. (1982), *High-Re solutions for incompressible flow using the Navier–Stokes equations and a multigrid method*, Journal of Computational Physics.

## Author

Sandeep Kumar · [GitHub](https://github.com/Sandeep-kumar-IITR)
