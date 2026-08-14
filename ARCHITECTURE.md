# OOMMF — Micromagnetic Vector Field Architecture Specification

## 1. Landau-Lifshitz-Gilbert (LLG) Solver
Models 3D magnetic spin precession and damping on a discrete cubic lattice:

$$\frac{\partial \mathbf{M}}{\partial t} = -\gamma \mathbf{M} \times \mathbf{H}_{\text{eff}} + \frac{\alpha}{M_s} \left( \mathbf{M} \times \frac{\partial \mathbf{M}}{\partial t} \right)$$

```mermaid
graph LR
    SpinGrid[3D Vector Field M_i] --> EffField[Effective Field Calculation]
    EffField --> FFT[3D FFT Demagnetization Tensor]
    FFT --> LLG[Runge-Kutta 4th Order Integrator]
    LLG --> Skyrmion[Topological Charge Evaluation Q]
```

## 2. Dual Authorship
- **Жирняк (Jirnyak)** — Lead Micromagnetic Physicist.
- **Адольф Петушков (Adolf Petushkov)** — Systems & Numerical Architecture.
