# Dust Extraction System Control (DES-Ctrl)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![KiCad](https://img.shields.io/badge/KiCad-EDA-blue.svg)](https://kicad.org/)

Open-source hardware and firmware solution designed to replicate and control the vacuum dust extraction interface for **LPKF ProtoMat** circuit board plotters using affordable commercial vacuum systems.

Developed as an academic project for **Laboratorio de Electrónica III** at the School of Electrical Engineering, **Universidad de Los Andes (ULA)**, Mérida, Venezuela.

---

## Project Overview

Original LPKF ProtoMat systems utilize a synchronized vacuum dust extraction unit controlled via a serial UART interface (9600 bps) linked directly from the milling machine. When original extraction units are missing or unavailable, replacing them with proprietary hardware is cost-prohibitive. 

**DES-Ctrl** solves this challenge through a two-stage hardware approach:
1. **PCB1 (Sniffer / Man-in-the-Middle):** A passive/active diagnostic interface featuring DB9 male/female connectors and test points to intercept, log, and analyze UART communication packets between an LPKF ProtoMat (S63/C30) and its original dust extraction system.
2. **PCB2 (Controller & Power Stage):** An embedded microcontroller board equipped with zero-crossing detection and triac/thyristor switching to regulate speed and power for a standard 110VAC commercial wet/dry vacuum cleaner, perfectly synchronized with LPKF G-code / machine states.

---

## Repository Structure

```text
des_ctrl/
├── hardware/
│   ├── pcb1_sniffer/          # LPKF UART Interceptor & Test Points
│   │   ├── schematics/        # KiCad schematic files (.kicad_sch)
│   │   ├── layout/            # PCB layout files (.kicad_pcb)
│   │   └── 3d_models/         # STEP / 3D rendering models
│   └── pcb2_controller/       # Microcontroller & AC Zero-Crossing Power Stage
├── firmware/                  # MCU firmware for packet decoding and motor control
├── docs/                      # Technical notes, protocol captures, and schematics
└── LICENSE                    # MIT Open Source License
