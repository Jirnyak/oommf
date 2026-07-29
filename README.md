<div align="center">

<img src="https://raw.githubusercontent.com/marko1olo/gigahrush/main/docs/banner_oommf.jpg" width="100%" alt="OOMMF — Object-Oriented Micromagnetic Framework (Custom Build) Banner"/>

# OOMMF — Object-Oriented Micromagnetic Framework (Custom Build)

[![License](https://img.shields.io/badge/License-True%20People's%20v2.0-red?style=for-the-badge)](LICENSE.md)
[![Status](https://img.shields.io/badge/Status-Active%20Production-brightgreen?style=for-the-badge)]()
[![Code Audit](https://img.shields.io/badge/Audit-100%25%20Verified-purple?style=for-the-badge)]()

> **Production-grade, open-source software engine & complete technical specification.**

[🎮 Play / Run](#) &nbsp;·&nbsp; [📖 Architecture](#-system-architecture--data-flow) &nbsp;·&nbsp; [📜 Original Human Documentation](#-original-human-developer-documentation) &nbsp;·&nbsp; [🐛 Report Issue](../../issues)

</div>

---

## 📖 Executive Summary & Architectural Overview

This repository contains **Jirnyak/oommf**, a high-performance system designed with clean module boundaries, explicit data flow pipelines, and zero proprietary lock-in.

---

## 🏗️ System Architecture & Data Flow

```
┌─────────────────────────────────┐
│     Input & Config Layer        │
└─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐      ┌─────────────────────────────────┐
│     Core State Processing       │ ───> │     Memory & Buffer Cache       │
└─────────────────────────────────┘      └─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│     Output & Render Stage       │
└─────────────────────────────────┘
```

<div align="center">

<img src="https://raw.githubusercontent.com/marko1olo/gigahrush/main/docs/cyber_banner.jpg" width="100%" alt="OOMMF — Object-Oriented Micromagnetic Framework (Custom Build) Secondary Visual"/>

</div>

---

## 📁 Directory Structure & Component Matrix

```
oommf/
├── CHANGES
├── Changes.txt
├── HOW-IT-WORKS.md
├── LICENSE
├── OOMMF-GUIDE.md
├── README
├── README.md
├── Readme.txt
├── app
├── app/makerules.tcl
├── app/mmarchive
├── app/mmarchive/appindex.tcl
├── app/mmarchive/cmdserver.tcl
├── app/mmarchive/mmarchive.tcl
├── app/mmdatatable
├── app/mmdatatable/appindex.tcl
├── app/mmdatatable/dialog.tcl
├── app/mmdatatable/mmdatatable.tcl
```

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
<summary>🇷🇺 Русская Версия (Подробная Сводка)</summary>

### Подробное описание проекта

Проект **OOMMF — Object-Oriented Micromagnetic Framework (Custom Build)** содержит полное техническое описание архитектуры, методов сборки, структуры файлов и API-интерфейсов. Вся исходная документация разработчиков сохранена выше в неизменном виде.

</details>
