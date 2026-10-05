# Appendix E: Thermal & Charging Calculations

This appendix consolidates the worked thermal and charging calculation methods used throughout the main text (Chapters 2, 7, 11), presented as reusable calculation templates with worked examples, for use in process characterization and recipe development.

---

## E.1 Wafer Bow from Film Stack Stress (Stoney's Equation Application)

**Method** (Chapter 2, Section 5.1):

$$\delta \approx \frac{3\sigma_f t_f r^2(1-\nu_s)}{E_s t_s^2}$$

where $\delta$ = resulting bow (deflection), $\sigma_f$ = net residual film stress, $t_f$ = total film stack thickness, $r$ = wafer radius, $\nu_s$ = substrate Poisson's ratio, $E_s$ = substrate Young's modulus, $t_s$ = substrate thickness.

**Worked template:**

| Input | Symbol | Example Value |
|---|---|---|
| Net residual stack stress | $\sigma_f$ | 150 MPa |
| Total film thickness | $t_f$ | 6 µm |
| Wafer radius | $r$ | 150 mm |
| Substrate thickness | $t_s$ | 775 µm |
| Substrate Young's modulus | $E_s$ | 130 GPa |
| Substrate Poisson's ratio | $\nu_s$ | 0.28 |
| **Result: Bow** | $\delta$ | **~560 µm** |

To use: substitute your own characterized $\sigma_f$ and $t_f$ values; compare resulting $\delta$ against your lithography overlay specification (typically tens of microns) to assess stress compensation adequacy, per Chapter 2, Section 5.1's discussion.

## E.2 Gas Residence Time

**Method** (Chapter 6, Section 1.1):

$$\tau_{res}[\text{s}] \approx 0.078 \times \frac{P[\text{mTorr}] \times V[\text{L}]}{Q[\text{sccm}]}$$

**Worked template:**

| Input | Symbol | Example Value |
|---|---|---|
| Chamber pressure | $P$ | 20 mTorr |
| Effective process volume | $V$ | 20 L |
| Total gas flow | $Q$ | 300 sccm |
| **Result: Residence time** | $\tau_{res}$ | **~0.104 s** |

To use: substitute tool-specific volume and operating conditions; compare against feature-fill timescale estimates (Chapter 6, Section 1.2) to assess recipe step-transition stabilization requirements.

## E.3 Sheath Voltage / Ion Current Density Scaling (Child-Langmuir-like)

**Method** (Chapter 5, Section 5.1):

$$J \approx \frac{4}{9}\epsilon_0\sqrt{\frac{2e}{M}}\frac{V_s^{3/2}}{d_s^2}$$

Use to estimate the degree of flux/energy coupling in a given single-frequency CCP configuration; rearrange to solve for $V_s$ given a target $J$, or vice versa, holding $d_s$ and $M$ (ion mass) fixed for a given gas/pressure condition.

## E.4 Polymer Thickness Steady-State / Etch-Stop Margin

**Method** (Chapter 3, Section 5.3):

$$\frac{d\delta_p}{dt} = R_{dep} - R_{ion,removal} - R_{O2,removal}$$

**Worked template (illustrative etch-stop margin check):**

| Input | Symbol | Moderate AR (20:1) | High AR (80:1) |
|---|---|---|---|
| Deposition rate | $R_{dep}$ | 2.0 nm/min | 1.4 nm/min (70% of moderate-AR value) |
| Combined removal rate | $R_{removal}$ | 2.0 nm/min | 0.8 nm/min (40% of moderate-AR value) |
| **Net accumulation** | $d\delta_p/dt$ | **0 (balanced)** | **+0.6 nm/min (net accumulation — etch-stop risk)** |

To use: characterize your own process's deposition and removal rate attenuation with aspect ratio (via blanket and patterned test structure comparison), and apply this balance check at your target production aspect ratio to assess etch-stop margin before full qualification.

## E.5 Differential Charging Field Estimate

**Method** (Chapter 11, Section 6.1):

$$\sigma_q \approx J_{imbalance} \times t_{charging} \qquad E \approx \frac{\sigma_q}{2\epsilon_0}$$

**Worked template:**

| Input | Symbol | Example Value |
|---|---|---|
| Net ion/electron current density imbalance | $J_{imbalance}$ | $10^{-4}\ \text{A/cm}^2$ |
| Charging accumulation timescale | $t_{charging}$ | 1 ms |
| **Result: Accumulated surface charge density** | $\sigma_q$ | **$10^{-7}\ \text{C/cm}^2$** |
| **Result: Estimated field** | $E$ | **~5.6×10⁷ V/m** |

To use: this order-of-magnitude estimate helps assess whether a given reactor/process combination is likely operating in a charging-significant regime (per Appendix D.5's reference table); direct charging measurement generally requires specialized diagnostic techniques beyond this simplified estimate's scope.

## E.6 Staircase Compounding Error (Random Walk vs. Systematic)

**Method** (Chapter 13, Section 3.2):

$$\sigma_{cumulative}(N) \approx \sigma_{trim}\sqrt{N} \qquad \Delta_{cumulative}(N) \approx N\cdot\epsilon_{sys}$$

**Worked template:**

| Input | Symbol | Example Value |
|---|---|---|
| Number of trim-etch cycles | $N$ | 128 |
| Per-cycle random trim error (std. dev.) | $\sigma_{trim}$ | 2 nm |
| Per-cycle systematic trim bias | $\epsilon_{sys}$ | 0.5 nm |
| **Result: Cumulative random error** | $\sigma_{cumulative}$ | **~22.6 nm** |
| **Result: Cumulative systematic error** | $\Delta_{cumulative}$ | **~64 nm** |

To use: substitute your own characterized per-cycle error statistics; use the result to set landing pad design margin per Chapter 13, Section 4.1, and to prioritize systematic drift elimination (Section 3.3) over random noise reduction when the systematic term dominates, as in this example.

---

*All templates in this appendix reproduce the calculation methods developed in their referenced main-text chapters. Users should substitute characterized, tool-specific input values rather than relying on the illustrative example values shown here for actual process decisions.*
