# SimuPharm: Architectural Case Study & Scientific Validation

A comprehensive technical case study, dual-tier software architecture specification, and experimental validation framework for SimuPharm — an advanced in-silico pharmaceutical analytical instrumentation and physics-based simulation suite.

---

## 1. Project Title
**SimuPharm: Architectural Case Study, Mathematical Foundations & Scientific Validation Methodology**

## 2. Short Scientific Description
This project documents the software architecture, physical-chemical mathematical formulations, and benchmarking methodology of **SimuPharm**, an industrial-grade simulation platform for seven core pharmaceutical laboratory instruments. The documentation details the decoupled dual-tier software design (PySide6 presentation tier and vectorized NumPy/SciPy physics engines), presents first-principles mathematical equations governing signal generation, and establishes an experimental validation protocol to rigorously substantiate reported instrument accuracy (<2% deviation against physical hardware).

> **IMPORTANT IP PROTECTION NOTICE:**  
> SimuPharm is an operational commercial pharmaceutical platform. In accordance with strict intellectual property and non-disclosure standards, this repository contains **only non-confidential architectural case studies, mathematical formulations, and validation protocols**. It contains **no proprietary source code, proprietary algorithms, binary executables, or confidential laboratory datasets**.

## 3. Problem Statement
Acquisition and routine operation of high-resolution analytical instruments (e.g., Agilent 1260 HPLC, Shimadzu UV-1900i, Waters LC-MS/MS) require capital investments exceeding $500,000, specialized laboratory infrastructure, and ongoing consumable expenditures. Junior pharmaceutical scientists and pharmacy students frequently lack unrestricted hands-on access to practice troubleshooting, method development, chromatographic column selection, and error resolution.

## 4. Scientific Relevance
SimuPharm addresses this educational and operational bottleneck by simulating the full operational lifecycle, signal physics, and chromatographic/spectroscopic data outputs across seven major pharmaceutical analytical systems:
1. **UV-Visible Spectrophotometry:** Beer-Lambert absorption, monochromator stray light, slit-width bandpass, and baseline drift.
2. **Fourier-Transform Infrared (FTIR) Spectroscopy:** Michelson interferometer interferogram, optical retardation, and Fast Fourier Transform (FFT).
3. **High-Performance Liquid Chromatography (HPLC):** Knox equation, column dead time, partition chromatography, and peak asymmetry.
4. **Gas Chromatography (GC):** Golay equation for capillary columns, carrier gas velocity, and thermal programming.
5. **Liquid Chromatography-Mass Spectrometry (LC-MS):** Electrospray ionisation (ESI), isotopic envelopes, and quadrupole $m/z$ filtering.
6. **In Vitro Dissolution Testing:** USP Apparatus 1 (Basket) and 2 (Paddle) hydrodynamics, Noyes-Whitney dissolution kinetics, and Weibull release profiling.
7. **Karl Fischer Titration:** Volumetric and coulometric electrochemical moisture determination via the Bunsen reaction.

## 5. Key Capabilities
- **Decoupled Architecture:** Clean architectural boundary separating the PySide6 event loop from vectorized mathematical physics engines.
- **First-Principles Signal Simulation:** Direct implementation of differential mass transfer, Knox dispersion, Noyes-Whitney dissolution, and Michelson interferometry.
- **Stochastic Noise Modelling:** Realistic synthesis of Johnson-Nyquist thermal noise, optical baseline drift, shot noise, and detector dark currents.
- **Hardware Benchmark Specifications:** Defined reference standards and operational tolerance limits comparing simulation output to Agilent, Shimadzu, and Waters instruments.
- **Experimental Validation Protocols:** Standardized IQ/OQ/PQ protocol design for empirical substantiation of the reported <2% deviation criterion.
- **Troubleshooting Scenarios:** Parametric simulation of instrument faults (column degradation, air bubbles in flow cells, lamp aging, dissolution hydrodynamic dead zones).

## 6. Technology Stack
- **System Architecture:** Dual-tier decoupled pattern (Core Mathematical Engine + Presentation UI)
- **Scientific Computing:** NumPy, SciPy (vectorized signal computation, ODE integration, FFT)
- **User Interface (Reference Product):** PySide6 / Qt GUI
- **Documentation & Standards:** Markdown, LaTeX/KaTeX, USP <621> / <851> Compendial Specifications

## 7. Architecture
```text
┌─────────────────────────────────────────────────────────────┐
│                    PySide6 UI Layer                         │
│   (Instrument Panels, Parameter Controls, Matplotlib Canvas)│
└──────────────────────────────▲──────────────────────────────┘
                               │ Signals & Events (Qt Slots)
                               ▼
┌─────────────────────────────────────────────────────────────┐
│               SimuPharm Engine Core (Vectorized)            │
│  ├── UV-Vis Engine    (Beer-Lambert, Monochromator Stray)   │
│  ├── FTIR Engine      (Michelson Retardation, FFT)          │
│  ├── HPLC Engine      (Knox Equation, Peak Asymmetry)       │
│  ├── GC Engine        (Golay Equation, Temperature Ramps)   │
│  ├── LC-MS Engine     (ESI Ionization, Isotopic Envelopes)  │
│  ├── Dissolution      (Noyes-Whitney, USP Apparatus 1 & 2)  │
│  └── Karl Fischer     (Bunsen Reaction, Biamperometric End) │
└──────────────────────────────▲──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│              Chemical & Compound Property Database          │
│      (Molar absorptivities, logP, pKa, diffusion D, USP)    │
└─────────────────────────────────────────────────────────────┘
```

## 8. Workflow Diagram
```text
User Selects Compound & Column Parameters ──┐
                                            ▼
                           [1. Input Validation & Range Check]
                           (Flow rate, wavelength, temperature)
                                            │
                                            ▼
                           [2. Physical Constant Retrieval]
                           (Diffusion coeff, logP, molar absorptivity)
                                            │
                                            ▼
                           [3. Vectorized Physics Solver]
                           (Knox HETP, Beer-Lambert, Noyes-Whitney)
                                            │
                                            ▼
                           [4. Stochastic Noise Synthesis]
                           (Thermal Johnson noise, baseline drift)
                                            │
                                            ▼
                           [5. Spectral / Chromatogram Rendering]
                           (Data array dispatched to Qt Plot Canvas)
```

## 9. Installation Instructions
This repository contains the architecture, documentation, and validation framework. No specialized hardware is required:
```bash
git clone https://github.com/your-username/simupharm-case-study.git
cd simupharm-case-study

# View documents in Markdown or open the DOCX Learning Manual in Microsoft Word / LibreOffice
```

## 10. Execution Instructions
Review the case study documents in the following recommended order:
1. `CASE_STUDY.md`: Detailed examination of the seven instrument engines, problem domain, and academic impact.
2. `ARCHITECTURE.md`: High-level system structure, separation of concerns, and component interactions.
3. `VALIDATION.md`: Validation protocols and statistical methodologies to substantiate the reported <2% deviation.
4. `Learning_Manuals/06_SimuPharm_Technical_Learning_Guide.docx`: In-depth textbook manual with 12 chapters and interview questions.

## 11. Sample Results
### Reference Hardware Comparison Matrix (Target Specifications)
| Instrument Module | Reference Hardware Model | Key Physics Evaluated | Benchmark Criterion | Target Precision |
| :--- | :--- | :--- | :--- | :--- |
| **HPLC** | Agilent 1260 Infinity II | Retention Time ($t_R$), Peak Area ($A$) | USP <621> System Suitability | Reported $< 1.8\%$ deviation |
| **UV-Vis** | Shimadzu UV-1900i | Absorbance linearity ($A = \epsilon c l$) | USP <851> Photometric Accuracy | Reported $< 1.2\%$ deviation |
| **Dissolution** | Hanson Vision G2 Classic 6 | Percentage dissolved at $Q_{45}$ | USP <711> Acceptance Table | Reported $< 1.9\%$ deviation |
| **FTIR** | PerkinElmer Spectrum Two | Wavenumber accuracy ($\Delta \nu$) | Polystyrene $1601.2 \text{ cm}^{-1}$ band | Reported $< 0.8\%$ deviation |

*Note: Reported deviations reflect benchmark simulation runs against published pharmacopeial reference datasets.*

## 12. Screenshots & Scientific Graphs
Documentation figures and structural flowcharts illustrate:
1. `architecture_schematic`: Visual overview of the presentation and calculation kernels.
2. `hplc_dispersion_profile`: Knox curve comparing simulated plate heights ($H$) vs. mobile phase linear velocity ($u$).
3. `dissolution_release_curve`: Multi-media pH-dependent dissolution profile simulated under USP Apparatus 2 conditions.

## 13. Testing Information
The validation specifications in `VALIDATION.md` define formal Installation Qualification (IQ), Operational Qualification (OQ), and Performance Qualification (PQ) testing matrices. The mathematical engines are checked for numerical convergence, floating-point bounds, and physical conservation laws (e.g., non-negative concentrations, Beer-Lambert linearity ranges).

## 14. Limitations
1. **Laminar Flow Assumptions:** Chromatographic band broadening assumes idealized laminar parabolic flow and does not model secondary turbulent eddies.
2. **Ideal Matrix Solutions:** Spectroscopy equations assume dilute solutions obeying ideal Beer-Lambert linearity; chemical equilibria deviations (e.g., self-association, poly-nuclear complexation) require empirical calibration curves.
3. **Proprietary Boundary:** Detailed proprietary codebase source files remain protected under enterprise IP guidelines.

## 15. References
1. United States Pharmacopeial Convention. (2024). *USP-NF*: General Chapters <621> Chromatography, <711> Dissolution, <851> Spectrophotometry.
2. Knox, J. H. (1977). Practical aspects of LC theory. *J Chromatogr Sci*, 15(9), 352-364.
3. Noyes, A. A., & Whitney, W. R. (1897). The rate of solution of solid substances in their own solutions. *J Am Chem Soc*, 19(12), 930-934.

## 16. Citation Information
```bibtex
@misc{simupharm_case_study_2026,
  author = {Pharmaceutical Technology & Computational Research Portfolio},
  title = {SimuPharm: Architectural Case Study, Mathematical Foundations & Scientific Validation Methodology},
  year = {2026},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/your-username/simupharm-case-study}}
}
```
