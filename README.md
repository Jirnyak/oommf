# 🧲 OOMMF — Landau-Lifshitz-Gilbert 3D Micromagnetic Vector Lattice

[![Live Demo](https://img.shields.io/badge/Live_Showcase-GitHub_Pages-a855f7?style=for-the-badge&logo=github)](https://jirnyak.github.io/oommf/)
[![AI Index](https://img.shields.io/badge/LLM_Search-llms.txt-38bdf8?style=for-the-badge)](https://raw.githubusercontent.com/Jirnyak/oommf/main/llms.txt)
[![C++20](https://img.shields.io/badge/C%2B%2B-20-00599C?style=for-the-badge&logo=cplusplus)](https://isocpp.org/)
[![Spintronics](https://img.shields.io/badge/Physics-Landau_Lifshitz_Gilbert-00f5a0?style=for-the-badge)](https://en.wikipedia.org/wiki/Landau%E2%80%93Lifshitz%E2%80%93Gilbert_equation)

A 3D micromagnetic vector field simulation solving the non-linear **Landau-Lifshitz-Gilbert (LLG)** differential equations across cubic discretization meshes to model skyrmion stability, magnetic domain wall dynamics, and spintronic memory devices.

---

## 🏛️ Differential Solver Pipeline

```mermaid
graph LR
    Mesh[3D Spin Vector Mesh M_i] --> Energy[Effective Field H_eff: Exchange + Anisotropy + Demag]
    Energy --> LLG[LLG Numerical Integrator: dM/dt = -γ(M × H_eff) + α(M × dM/dt)]
    LLG --> FFT[3D FFT Demagnetization Tensor Convolver]
    FFT --> State[Next Spin Orientation & Topological Charge Q]
```

---

## 🔬 Mathematical Formalism

$$\frac{\partial \mathbf{M}}{\partial t} = -\gamma \mathbf{M} \times \mathbf{H}_{\text{eff}} + \frac{\alpha}{M_s} \left( \mathbf{M} \times \frac{\partial \mathbf{M}}{\partial t} \right)$$

- $\mathbf{H}_{\text{eff}}$ encompasses Heisenberg direct exchange coupling, uniaxial magnetocrystalline anisotropy, Zeeman external field, and demagnetization dipole-dipole convolution.
- Topological skyrmion charge evaluation: $Q = \frac{1}{4\pi} \iint \mathbf{m} \cdot \left( \frac{\partial \mathbf{m}}{\partial x} \times \frac{\partial \mathbf{m}}{\partial y} \right) dx\,dy$.

---

### 👨‍💻 Engineering Syndicate & Authors
- **Жирняк (Jirnyak)** — Lead Micromagnetic Physicist & Mathematical Engine.  
  GitHub: [@Jirnyak](https://github.com/Jirnyak)
- **Адольф Петушков (Adolf Petushkov)** — High-Concurrency Systems & Simulation Architecture.  
  GitHub: [@marko1olo](https://github.com/marko1olo)
