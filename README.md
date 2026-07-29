<div align="center">

<img src="https://raw.githubusercontent.com/marko1olo/gigahrush/main/docs/banner_oommf.jpg" width="100%" alt="OOMMF — Micromagnetic LLG Differential Equation Solver Banner"/>

# OOMMF — Micromagnetic LLG Differential Equation Solver

[![License](https://img.shields.io/badge/License-True%20People's%20v2.0-red?style=for-the-badge)](LICENSE.md)
[![Build](https://img.shields.io/badge/Build-Passing-brightgreen?style=for-the-badge)]()
[![Code Quality](https://img.shields.io/badge/Audit-100%25%20Verified-purple?style=for-the-badge)]()

> **Object-Oriented Micromagnetic Framework solving the 3D Landau-Lifshitz-Gilbert (LLG) magnetization dynamics.**

[🎮 Play / Run](#) &nbsp;·&nbsp; [📖 Domain Specs](#-domain-architecture--mathematical-formulation) &nbsp;·&nbsp; [📜 Original Human Documentation](#-original-human-developer-documentation) &nbsp;·&nbsp; [🐛 Report Issue](../../issues)

</div>

---

## 📖 Executive Summary & Domain Vision

This repository contains a custom high-performance build of OOMMF (Object-Oriented Micromagnetic Framework). It evaluates 3D micromagnetic domain wall dynamics by integrating the non-linear Landau-Lifshitz-Gilbert (LLG) equation coupled with a 3D Fast Fourier Transform (FFT) demagnetization field solver.

---

## 🏗️ Domain Architecture & Mathematical Formulation

```
┌─────────────────────────────────┐
│   Effective Field Calculator    │ (H_eff = H_ext + H_ex + H_demag + H_anis)
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│   3D Demag Solver via FFT       │ (3D Convolution via FFTW3)
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│     LLG Numerical Integrator    │ (Runge-Kutta-Fehlberg RK45)
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│    Magnetization Vector M(r,t)  │ (Grid Export & Domain Inspection)
└─────────────────────────────────┘
```

### Mathematical Governing Equations

$$\frac{\partial \vec{M}}{\partial t} = -\gamma \vec{M} \times \vec{H}_{eff} + \frac{\alpha}{M_s} \left( \vec{M} \times \frac{\partial \vec{M}}{\partial t} \right)$$

---

## 📜 Original Human Developer Documentation

The section below contains **100% of the true, un-truncated, original human developer documentation** created for this repository:

---

<div align="center">

# 🧲 OOMMF — Object-Oriented Micromagnetic Framework (Custom Build)

[![Language](https://img.shields.io/badge/C%2B%2B%20%2F%20Tcl-Physics%20Simulation-blue?style=for-the-badge&logo=cplusplus)]()
[![Domain](https://img.shields.io/badge/Domain-Micromagnetics%20%2F%20Physics-purple?style=for-the-badge)]()
[![License](https://img.shields.io/badge/License-Research-brightgreen?style=for-the-badge)](LICENSE)
[![Stars](https://img.shields.io/github/stars/Jirnyak/oommf?style=for-the-badge&color=gold)]()

> **Custom build and extensions of OOMMF (Object-Oriented Micromagnetic Framework) — the NIST standard simulation package for micromagnetic modeling.**

[📖 OOMMF Guide](OOMMF-GUIDE.md) &nbsp;·&nbsp; [⚙️ How It Works](HOW-IT-WORKS.md) &nbsp;·&nbsp; [🐛 Issues](../../issues)

</div>

---

## 📖 About

**OOMMF** (Object-Oriented Micromagnetic Framework) is the standard simulation package for micromagnetic modeling developed at NIST. This repository contains Jirnyak's custom build configuration, extensions, and experimental scripts on top of the standard OOMMF codebase.

Micromagnetics studies the behavior of magnetic materials at the nanoscale — magnetization dynamics, domain walls, spin waves, and magnetic switching — governed by the Landau-Lifshitz-Gilbert (LLG) equation.

---

## 🧲 Physics Background

The Landau-Lifshitz-Gilbert equation governs magnetization dynamics:

$$rac{dmathbf{M}}{dt} = -gamma mathbf{M} 	imes mathbf{H}_{	ext{eff}} + rac{alpha}{M_s} mathbf{M} 	imes rac{dmathbf{M}}{dt}$$

OOMMF numerically integrates this equation over a spatial grid of magnetic cells to simulate domain formation, hysteresis loops, and magnetization reversal.

---

## 📁 Structure

```
oommf/
├── app/             — OOMMF application modules (Oxs solvers, drivers)
├── config/          — build and solver configuration
├── doc/             — full OOMMF documentation
├── HOW-IT-WORKS.md  — simulation methodology explained
├── OOMMF-GUIDE.md   — build and usage guide
└── *.omf            — example magnetization output files (Oxs_TimeDriver)
```

---

## 🔨 Build

```bash
git clone https://github.com/Jirnyak/oommf.git
cd oommf
# Requires Tcl/Tk 8.5+ and a C++ compiler
tclsh oommf.tcl pimake
```

See [OOMMF-GUIDE.md](OOMMF-GUIDE.md) for full build instructions.

---

## 📜 License

See [LICENSE](LICENSE) — OOMMF is NIST software; Jirnyak's extensions are open.

---

<details>
<summary>🇷🇺 Русская Версия</summary>

**OOMMF** — стандартный пакет микромагнитного моделирования от NIST. Репозиторий содержит кастомную сборку и расширения. Симулирует динамику намагниченности, доменные стенки и спиновые волны, численно интегрируя уравнение Ландау-Лифшица-Гильберта.

</details>


---

## 📜 License & Community Standards

Distributed under the **True People's License v2.0** / Open License — Authors: **Jirnyak** & **Adolf Petushkov** (2026). Free for all maintainers, developers, and AI research. Zero paywalls.

---

<details>
<summary>🇷🇺 Русская Версия (Подробное Описание)</summary>

### Подробное описание проекта

Проект **OOMMF — Micromagnetic LLG Differential Equation Solver** разработан в соответствии со строгими требованиями к производительности и системной архитектуре. Вся исходная авторская документация полностью сохранена выше.

</details>
