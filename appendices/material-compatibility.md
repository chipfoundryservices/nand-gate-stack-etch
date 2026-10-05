# Appendix B: Material Compatibility Matrix for Chamber Components

This appendix consolidates the chamber material selection guidance developed primarily in Chapter 8, organized as a lookup matrix for component-level reference.

---

## B.1 Plasma-Facing Component Material Compatibility

| Component | Recommended Material | Fluorocarbon/F Compatibility | Typical Service Life Driver | Chapter Reference |
|---|---|---|---|---|
| Chamber wall (bulk) | Anodized Al or Y2O3/Al2O3-coated Al | Good (coated); moderate (bare anodized) | Coating erosion, wall polymer accumulation | Chapter 8, Section 1.1 |
| Showerhead | Y2O3-coated Al, or Si/SiC | Good | Hole conductance drift from polymer/erosion | Chapter 8, Section 1.1; Chapter 6, Section 2.1 |
| ESC (electrostatic chuck) surface | Al2O3 or AlN ceramic | Good, but edge-exposed regions erode faster | Edge erosion, dielectric property drift | Chapter 8, Section 1.1; Chapter 5, Section 6.1 |
| Focus/edge ring | Quartz, Si, or SiC | Good; treated as consumable regardless | Direct, concentrated plasma exposure; scheduled replacement | Chapter 8, Section 1.1, 1.3 |
| ICP dielectric window | Quartz or alumina | Good | Thermal/chemical exposure from plasma side | Chapter 8, Section 1.1; Chapter 5, Part 1 |
| RF electrode (CCP) | Anodized/coated Al | Good (coated) | Sheath-driven erosion at high bias power | Chapter 7, Part 1 |

## B.2 Fluorine Resistance Ranking (Qualitative)

| Material | Relative Fluorine/Fluorocarbon Resistance | Typical Use Context |
|---|---|---|
| Y2O3 (yttria) coating | Highest among common coatings | High ion-flux-exposed surfaces (showerhead face, chamber walls near plasma core) |
| Al2O3 (alumina) ceramic/coating | High | ESC body, dielectric windows, general wall coating |
| Quartz (SiO2) | Moderate-high | Dielectric windows, focus rings (consumable by design) |
| Anodized aluminum (uncoated beyond anodization) | Moderate | Lower-exposure structural components |
| Bare aluminum | Low (not used plasma-facing without coating) | Not recommended for direct plasma exposure; used only as substrate beneath coatings |

## B.3 Secondary Electron Emission Considerations

| Material | Relative Secondary Electron Emission | Uniformity Consequence |
|---|---|---|
| Bare/anodized Al | Baseline reference | Established uniformity models typically calibrated against this baseline |
| Y2O3 coating | Measurably different from bare Al (material and coating-process dependent) | Requires process requalification per Chapter 8, Section 6.1 when changing coating formulation |
| Al2O3 coating | Measurably different from bare Al (material and coating-process dependent) | Same requalification requirement |

## B.4 Thermal Expansion Compatibility (Coating-to-Substrate)

| Coating | Substrate | Compatibility Note |
|---|---|---|
| Y2O3 | Al | Requires qualified coating process to manage CTE mismatch; validated via accelerated thermal cycling per Chapter 8, Section 6.2 |
| Al2O3 | Al | Similar CTE mismatch management requirement |
| Al2O3 | AlN (ESC body) | Generally more closely matched than Al-substrate cases |

## B.5 Component Lifetime Management Summary

| Component Category | Typical Replacement Trigger | Chapter Reference |
|---|---|---|
| Focus/edge ring | RF hours or wafer count threshold, proactive replacement before measurable uniformity impact | Chapter 8, Section 1.3 |
| Showerhead | Hole conductance drift beyond specification, or scheduled wet clean interval | Chapter 8, Section 3.3-3.4 |
| ESC surface | Dielectric property drift or visible erosion at wafer edge contact zone | Chapter 8, Section 1.3 |
| Dielectric window | Scheduled inspection interval; replacement on crack/erosion detection | Chapter 8, Part 1 |

---

*This matrix summarizes qualitative guidance developed in Chapter 8; specific material qualification, erosion rate characterization, and replacement interval setting must be performed empirically for each tool platform and process recipe combination, per Chapter 8, Section 3.4's cadence-setting discussion.*
