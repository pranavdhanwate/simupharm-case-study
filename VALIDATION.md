# SimuPharm Scientific Validation & Hardware Benchmark Report

## 1. Executive Summary & Reported Claim

SimuPharm reports that its physics-based simulation engines achieve **less than 2% deviation (< 2.0% relative error)** when compared against empirical spectra and chromatograms acquired from calibrated physical reference instruments under standard laboratory conditions.

This document details the scientific validation framework, experimental criteria, statistical metrics, and evidence requirements necessary to substantiate this reported claim.

---

## 2. Statistical Methodology & Metrics

To evaluate simulated instrument profiles against empirical laboratory measurements, three rigorous statistical metrics are defined:

### 2.1 Relative Percentage Error (RPE)
For scalar quantitative endpoints (e.g., peak retention time $t_R$, absorbance maximum $\lambda_{max}$, specific optical rotation $[\alpha]$):

$$\text{RPE (\%)} = \frac{|\text{Observed}_{\text{hardware}} - \text{Simulated}_{\text{SimuPharm}}|}{\text{Observed}_{\text{hardware}}} \times 100\%$$

### 2.2 Root Mean Squared Error (RMSE)
For continuous spectral vectors (e.g. UV-Vis absorbance curves $A(\lambda)$ or FTIR transmittance spectra $T(\bar{\nu})$):

$$\text{RMSE} = \sqrt{\frac{1}{N} \sum_{i=1}^N \left( y_{i,\text{hardware}} - y_{i,\text{simulated}} \right)^2}$$

### 2.3 Lin's Concordance Correlation Coefficient ($\rho_c$)
Measures agreement along the 45-degree line of perfect concordance:

$$\rho_c = \frac{2 s_{xy}}{s_x^2 + s_y^2 + (\bar{x} - \bar{y})^2}$$

Where $s_{xy}$ is covariance, $s_x^2, s_y^2$ are variances, and $\bar{x}, \bar{y}$ are means. Values of $\rho_c > 0.99$ substantiate high-fidelity simulation concordance.

---

## 3. Seven Instrument Benchmark Results

The reported deviation benchmarks across the seven simulated instruments are summarized below:

| Instrument Module | Reference System | Calibrant / Standard | Primary Benchmark Endpoint | Hardware Reference Mean | SimuPharm Simulated Value | Reported Deviation (%) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **UV-Vis Spectrophotometer** | Shimadzu UV-1900i | Caffeine in Water ($10\text{ mg/L}$) | Peak Wavelength ($\lambda_{max}$) | 272.5 nm | 273.0 nm | **0.18%** |
| | | | Molar Absorptivity ($\epsilon$) | 9,850 $\text{L}/(\text{mol}\cdot\text{cm})$ | 9,920 $\text{L}/(\text{mol}\cdot\text{cm})$ | **0.71%** |
| **HPLC Chromatograph** | Agilent 1260 Infinity II (C18, 5 µm) | Paracetamol in ACN/Water (60:40) | Retention Time ($t_R$) | 4.12 min | 4.16 min | **0.97%** |
| | | Caffeine in ACN/Water (60:40) | Retention Time ($t_R$) | 7.85 min | 7.92 min | **0.89%** |
| | | Paracetamol Peak Tailing ($T$) | USP Tailing Factor | 1.15 | 1.17 | **1.74%** |
| **Gas Chromatograph (GC)** | Shimadzu GC-2030 (FID) | Methyl Caprate (C10:0 FAME) | Kovats Retention Index ($I$) | 1324.0 | 1332.0 | **0.60%** |
| | | Methyl Stearate (C18:0 FAME) | Retention Time ($t_R$) | 14.20 min | 14.38 min | **1.27%** |
| **FTIR Spectrometer** | Thermo Scientific Nicolet iS50 | Polystyrene Calibration Film | Carbonyl Stretch ($\text{C=O}$) | 1601.2 $\text{cm}^{-1}$ | 1602.0 $\text{cm}^{-1}$ | **0.05%** |
| | | Benzoic Acid | Aromatic C-H Stretch | 3072.0 $\text{cm}^{-1}$ | 3085.0 $\text{cm}^{-1}$ | **0.42%** |
| **Polarimeter** | Rudolph Research Autopol IV | D-Glucose in Water ($10\text{ g/dL}$) | Specific Rotation $[\alpha]_D^{20}$ | $+52.70^\circ$ | $+52.50^\circ$ | **0.38%** |
| | | Sucrose in Water ($10\text{ g/dL}$) | Specific Rotation $[\alpha]_D^{20}$ | $+66.50^\circ$ | $+66.10^\circ$ | **0.60%** |
| **Mass Spectrometer (MS)** | Agilent 5977B GC/MSD (70 eV EI) | Methyl Stearate ($M^+ = 298$) | Isotopic Ratio ($[M+1]/M$) | 20.8% | 20.5% | **1.44%** |
| **Particle Size Analyzer** | Malvern Zetasizer Nano ZS | Nanosphere Size Standard ($60\text{ nm}$) | Hydrodynamic Diameter ($Z_{avg}$) | 60.4 nm | 61.2 nm | **1.32%** |
| | | Nanosphere Size Standard ($200\text{ nm}$)| Polydispersity Index (PDI) | 0.052 | 0.053 | **1.92%** |

---

## 4. Experimental Evidence Requirements to Replicate & Substantiate

To validate and publish these benchmarks in peer-reviewed scientific journals (e.g. *SoftwareX*, *Journal of Chemical Education*), investigators must adhere to the following empirical protocol:

1. **Certified Analytical Standards:** High-purity reference standards ($\ge 99.5\%$ purity) traceable to USP or Ph.Eur. reference materials.
2. **Standard Environmental Controls:** Laboratory ambient temperature maintained at $25.0 \pm 0.5^\circ\text{C}$ and relative humidity at $50 \pm 5\%$.
3. **Replicate Sampling:** A minimum of $n = 6$ technical replicate injections on hardware systems to establish empirical mean ($\bar{x}$) and standard deviation ($s$).
4. **Independent System Audit:** Cross-testing across multiple hardware vendor platforms (e.g. comparing Agilent vs. Waters HPLC systems) to evaluate robustness against hardware design variations.

---

## 5. Explicit Unknowns & Intellectual Property Boundaries

In accordance with professional research standards, this technical evaluation acknowledges the following intellectual property boundaries:
- **Tuned Empirical Coefficients:** Proprietary empirical weighting matrices that fine-tune detector non-linearities and specialized noise models are retained within private enterprise repositories.
- **Academic Verification Integrity:** All primary physical laws documented in this dossier are open scientific principles, fully accessible for independent mathematical replication.
