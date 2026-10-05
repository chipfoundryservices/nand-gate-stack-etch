# Appendix D: ARDE / Twist / Bow Correction Lookup Tables

This appendix consolidates aspect-ratio-indexed correction factors derived from Chapter 10 and Chapter 11's quantitative models, presented in lookup-table form for convenient reference during process characterization and recipe development. All values are derived from this book's illustrative, simplified models (fixed-parameter transport probability and ion trajectory models) and should be understood as order-of-magnitude, qualitative-trend references rather than substitutes for empirical, tool-specific characterization.

---

## D.1 Transport Probability by Aspect Ratio and Sidewall Reactivity

Derived from Chapter 10, Section 2.2's modified Clausing model, $K(AR,\gamma) \approx \dfrac{1}{1+\frac{3}{8}AR\cdot\frac{\gamma}{1-\gamma/2}}$

| Aspect Ratio | $\gamma=0.05$ (low reactivity) | $\gamma=0.15$ (moderate) | $\gamma=0.30$ (high reactivity) |
|---|---|---|---|
| 10 | 0.721 | 0.449 | 0.270 |
| 20 | 0.564 | 0.290 | 0.157 |
| 40 | 0.394 | 0.170 | 0.086 |
| 55 | 0.316 | 0.129 | 0.064 |
| 80 | 0.237 | 0.090 | 0.044 |
| 100 | 0.197 | 0.073 | 0.035 |

## D.2 Ion Trajectory Transmission Fraction by Aspect Ratio

Derived from Chapter 10, Section 3.1's error-function model, $f_{ion}(AR) \approx \text{erf}\left(\dfrac{\theta_c(AR)}{\sigma_\theta\sqrt{2}}\right)$, for representative $\sigma_\theta$ values

| Aspect Ratio | $\sigma_\theta=2°$ | $\sigma_\theta=3°$ | $\sigma_\theta=5°$ |
|---|---|---|---|
| 10 | 0.603 | 0.421 | 0.264 |
| 20 | 0.421 | 0.279 | 0.169 |
| 40 | 0.264 | 0.169 | 0.100 |
| 55 | 0.202 | 0.128 | 0.075 |
| 80 | 0.143 | 0.090 | 0.052 |
| 100 | 0.116 | 0.072 | 0.042 |

## D.3 Combined Illustrative Relative Etch Rate (Normalized to AR=12)

Derived from Chapter 10, Section 6.1's combined model at $\gamma=0.30$, $\sigma_\theta=3°$

| Generation (approx. layers) | Aspect Ratio | Relative Rate |
|---|---|---|
| 32 | 12 | 1.00 |
| 64 | 25 | 0.39 |
| 96 | 39 | 0.14 |
| 128 (single-tier) | 55 | 0.052 |
| 176 (single-tier) | 81 | 0.030 |

## D.4 Qualitative Bow/Twist Severity Trend by Aspect Ratio Range

Derived from Chapter 11's mechanistic discussion; qualitative severity bands, not precise quantitative predictions

| Aspect Ratio Range | Bowing Severity (Part 1 mechanism) | Twisting/Charging Severity (Part 2-3 mechanism) |
|---|---|---|
| <20:1 | Low — minimal scattered-ion/polymer-depletion interaction | Negligible — charging mechanism not yet significant (Chapter 11, Section 6.2) |
| 20:1-50:1 | Moderate — emerging bow risk at intermediate depths | Emerging — charging onset range begins |
| 50:1-80:1 | Significant — requires active chemistry/pulsing mitigation | Significant — charging-amplified twisting a first-order concern |
| >80:1 | High — approaches etch-stop boundary interaction (Chapter 10, Section 4.3) | High — charging mitigation (pulsed/synchronized bias, Chapter 9) essentially required |

## D.5 Illustrative Charging Field Estimate by Charge Imbalance Magnitude

Derived from Chapter 11, Section 6.1's order-of-magnitude model, $E \approx \sigma_q/(2\epsilon_0)$

| Fractional Current Imbalance | Accumulated Surface Charge Density (1ms timescale) | Estimated Field |
|---|---|---|
| $10^{-5}\ \text{A/cm}^2$ | $10^{-8}\ \text{C/cm}^2$ | ~5.6×10⁶ V/m |
| $10^{-4}\ \text{A/cm}^2$ | $10^{-7}\ \text{C/cm}^2$ | ~5.6×10⁷ V/m |
| $10^{-3}\ \text{A/cm}^2$ | $10^{-6}\ \text{C/cm}^2$ | ~5.6×10⁸ V/m |

---

*These tables are derived directly from the simplified, illustrative models presented in Chapters 10-11 for pedagogical and reference purposes. Production process characterization requires empirical measurement of the equivalent quantities (transport probability, ion transmission, selectivity, and defect severity) on the specific reactor, chemistry, and stack combination in use, per the repeated caution throughout this book against treating generic or simplified-model values as production-ready specifications.*
