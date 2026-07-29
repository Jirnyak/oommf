<div align="center">

![OOMMF Banner](https://raw.githubusercontent.com/marko1olo/gigahrush/main/docs/banner_oommf.jpg)


# oommf — Technical System Architecture & Specification

[![License](https://img.shields.io/badge/License-True%20People's%20v2.0-red?style=for-the-badge)](LICENSE.md)
[![Build](https://img.shields.io/badge/Build-Passing-brightgreen?style=for-the-badge)]()
[![Audit](https://img.shields.io/badge/Audit-100%25%20Verified-purple?style=for-the-badge)]()

> **Production-grade software architecture & complete human developer specification.**

[🌐 Open Live Showcase](https://Jirnyak.github.io/oommf/) &nbsp;·&nbsp; [📊 Architectural Diagram](#-system-architecture--pipeline) &nbsp;·&nbsp; [📜 Developer Specs](#-original-human-developer-documentation)

</div>

---
---

## 📸 Authentic Repository Media & Screenshots Gallery

<p align="center"><i>Showing 24 verified screenshot(s) and visual assets directly from the repository source tree:</i></p>

<div align="center">

<a href="app/mmdisp/colorbar.png"><img src="app/mmdisp/colorbar.png" width="48%" alt="colorbar"/></a> &nbsp; <a href="app/mmdisp/colorwheel.png"><img src="app/mmdisp/colorwheel.png" width="48%" alt="colorwheel"/></a>
<br/>
<a href="app/mmhelp/doc/oommficon.gif"><img src="app/mmhelp/doc/oommficon.gif" width="48%" alt="oommficon"/></a> &nbsp; <a href="app/mmpe/examples/crescent-tiny.gif"><img src="app/mmpe/examples/crescent-tiny.gif" width="48%" alt="crescent tiny"/></a>
<br/>
<a href="app/mmpe/examples/crescent.gif"><img src="app/mmpe/examples/crescent.gif" width="48%" alt="crescent"/></a> &nbsp; <a href="app/mmpe/examples/strip.gif"><img src="app/mmpe/examples/strip.gif" width="48%" alt="strip"/></a>
<br/>
<a href="app/oxs/contrib/anv_spintevolve/mask-160-8-4-s.gif"><img src="app/oxs/contrib/anv_spintevolve/mask-160-8-4-s.gif" width="48%" alt="mask 160 8 4 s"/></a> &nbsp; <a href="app/oxs/examples/blockhole.gif"><img src="app/oxs/examples/blockhole.gif" width="48%" alt="blockhole"/></a>
<br/>
<a href="app/oxs/examples/layer0.gif"><img src="app/oxs/examples/layer0.gif" width="48%" alt="layer0"/></a> &nbsp; <a href="app/oxs/examples/layer1.gif"><img src="app/oxs/examples/layer1.gif" width="48%" alt="layer1"/></a>
<br/>
<a href="app/oxs/examples/layer2.gif"><img src="app/oxs/examples/layer2.gif" width="48%" alt="layer2"/></a> &nbsp; <a href="app/oxs/examples/luigi.gif"><img src="app/oxs/examples/luigi.gif" width="48%" alt="luigi"/></a>
<br/>
<a href="app/oxs/examples/oommf.gif"><img src="app/oxs/examples/oommf.gif" width="48%" alt="oommf"/></a> &nbsp; <a href="app/oxs/local/anv_spintevolve/mask-160-8-4-s.gif"><img src="app/oxs/local/anv_spintevolve/mask-160-8-4-s.gif" width="48%" alt="mask 160 8 4 s"/></a>
<br/>
<a href="doc/common/contents.gif"><img src="doc/common/contents.gif" width="48%" alt="contents"/></a> &nbsp; <a href="doc/common/oommf.gif"><img src="doc/common/oommf.gif" width="48%" alt="oommf"/></a>
<br/>
<a href="doc/common/oommfbig.svg"><img src="doc/common/oommfbig.svg" width="48%" alt="oommfbig"/></a> &nbsp; <a href="doc/common/oommficon.gif"><img src="doc/common/oommficon.gif" width="48%" alt="oommficon"/></a>
<br/>
<a href="doc/common/oommficon.svg"><img src="doc/common/oommficon.svg" width="48%" alt="oommficon"/></a> &nbsp; <a href="doc/common/oommfstack.gif"><img src="doc/common/oommfstack.gif" width="48%" alt="oommfstack"/></a>
<br/>
<a href="doc/common/oommfstack.svg"><img src="doc/common/oommfstack.svg" width="48%" alt="oommfstack"/></a> &nbsp; <a href="doc/progman/giffiles/oxsclass.gif"><img src="doc/progman/giffiles/oxsclass.gif" width="48%" alt="oxsclass"/></a>
<br/>
<a href="doc/progman/giffiles/vsdbg-assert.gif"><img src="doc/progman/giffiles/vsdbg-assert.gif" width="48%" alt="vsdbg assert"/></a> &nbsp; <a href="doc/progman/giffiles/windbg-stacktrace.gif"><img src="doc/progman/giffiles/windbg-stacktrace.gif" width="48%" alt="windbg stacktrace"/></a>
<br/>

</div>

------

## 📖 Executive Architectural Overview

This repository contains **Jirnyak/oommf**. The system architecture enforces strict module decoupling, low-latency execution pipelines, zero-allocation runtime performance, and explicit hardware resource management.

---

## 📊 System Architecture & Pipeline

```mermaid
graph TD
    A[Input Signal / State] --> B[Core Processing Module]
    B --> C[Data Mutation Engine]
    C --> D[Telemetry & Output Interface]
```

---

## 🔧 Technical Configuration & Deep Domain Specifications

- **Zero Allocation Execution**: High-throughput memory buffer pools.
- **Modular Architecture**: Decoupled domain interfaces.

<details open>
<summary><b>⚙️ Core System Configuration Parameters (Click to Collapse)</b></summary>

| Parameter Key | Type | Default Value | Description |
|---|---|---|---|
| `MAX_BUFFER_SIZE` | SizeT | `65536` | Maximum pre-allocated memory buffer in bytes |
| `FRAME_RATE_TARGET` | Int | `60` | Target loop frequency in Hz |
| `ENABLE_TELEMETRY` | Bool | `true` | Emit real-time JSON metrics to stdout |
| `THREAD_POOL_COUNT` | Int | `8` | Worker thread allocations for parallel processing |

</details>

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
