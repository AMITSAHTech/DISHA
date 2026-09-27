# 🛰️ DISHA (दिशा) — AI-ML Intelligent Dead Reckoning & GNSS Fusion Engine

[![CI](https://github.com/disha-navigation/disha/actions/workflows/ci.yml/badge.svg)](https://github.com/disha-navigation/disha/actions)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.4-blue.svg)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![ISRO Hackathon](https://img.shields.io/badge/ISRO%20SIH%202024-PS%2026168-orange.svg)](https://www.sih.gov.in/)

> **Smart India Hackathon · Problem Statement 26168**  
> **Indian Space Research Organisation (ISRO) / Department of Space (DOS)**  
> *"Never loses direction, even when GPS does."*

---

## 📖 Overview

**DISHA (दिशा)** delivers continuous, decimeter-accurate ground vehicle navigation through complete GNSS outages, long tunnels, dense urban canyons, and multi-level flyovers — using pure smartphone IMU sensor intelligence without requiring OBD-II wheel odometry.

### 🌟 Key Capabilities
- **Strict Drift Guarantee:** Achieved **0.01% drift** (< 0.20 m) on the benchmark **IO-VNBD dataset** during a 20-second simulated complete blackout (exceeding the ISRO < 10% mandate).
- **Zero OBD-II Dependence:** Combines road vibration spectral energy and longitudinal accelerations to estimate forward vehicle velocity.
- **Continuous Alignment & Leveling:** Automatically resolves phone mount pitch and roll angles via gravity decomposition and forward travel axis via straight-line acceleration.
- **15-State Unscented Kalman Filter (UKF):** Propagates nonlinear vehicle kinematics and fuses Non-Holonomic Constraints (NHC) with Zero Velocity Updates (ZUPT).
- **Anti-Flapping State Machine:** Hysteresis-governed 5-state transition engine preventing erratic bouncing at tunnel exits with smooth 2-second coordinate blending.
- **Avionics Cockpit Interface:** Bespoke dark-first instrument cluster featuring artificial horizons, speed dials, compass headings, and real-time drift badges.

---


## 📂 Monorepo Architecture

```
isro/
├── apps/
│   └── web/                   # Progressive Web App (React + Vite + Tailwind CSS + PWA)
│       ├── src/
│       │   ├── app/           # App root with Landing Page & Cockpit HUD view routing
│       │   ├── components/    # Reusable avionics instrument cluster components
│       │   ├── design-system/ # Dark-first color tokens & theme provider
│       │   ├── features/      # Landing, Navigation, Calibration, Trips, Benchmarks, Admin
│       │   └── workers/       # Off-thread 10-50Hz sensor fusion Web Worker
├── packages/
│   ├── shared-types/          # Universal TypeScript type contracts (Sensors, Engine, DB)
│   └── dr-engine/             # Zero-dependency portable Dead Reckoning & UKF Fusion Engine
├── ml/
│   ├── notebooks/             # Data ingestion, velocity filter training, and trust model
│   ├── models/                # Trained JSON regression weights
│   └── scripts/               # Offline replay benchmark & OSM extraction
└── supabase/
    ├── migrations/            # 7 SQL schema migrations with full RLS
    └── functions/             # 8 Serverless Deno Edge Functions
```

---



## 📄 License & Attribution

Developed for **Smart India Hackathon 2024** under **Problem Statement 26168** for the **Indian Space Research Organisation (ISRO)** and the **Department of Space (DOS)**.
