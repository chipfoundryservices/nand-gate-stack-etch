# Appendix A: Thermodynamic & Material Property Data Tables

This appendix consolidates material and thermodynamic property data referenced throughout the main text, gathered here for reference and worked-problem validation. Values are representative/illustrative, drawn from general literature ranges for the materials and species discussed; actual production process characterization should rely on fab- and tool-specific measured data (per Chapter 2, Section 1.3's caution against treating generic literature values as a substitute for recipe-specific characterization).

---

## A.1 Core Stack Material Properties

| Property | SiO2 (PECVD) | Si3N4 (PECVD) | Polysilicon | Reference |
|---|---|---|---|---|
| Density (g/cm³) | 2.1-2.2 | 2.6-2.8 | 2.30-2.33 | Chapter 2, Section 2.1-2.2 |
| Refractive index (633nm) | 1.45-1.46 | 1.95-2.05 | N/A (opaque) | Chapter 2, Section 2.1 |
| Dielectric constant (k) | ~4.0-4.2 | ~6.5-7.5 | N/A (semiconductor) | Chapter 2, Section 2.1 |
| Typical intrinsic stress | -300 to +300 MPa | -1.2 GPa to +1.0 GPa | Generally lower magnitude, grain-structure dependent | Chapter 2, Section 2.1-2.2, 3.2 |
| Wet etch rate reference | Baseline (dilute HF) | ~100:1+ selective removal in hot H3PO4 vs. oxide | Distinct wet/dry etch chemistry (TMAH, halogen-based) | Chapter 2, Section 2.1-2.2; Chapter 14, Section 2.1 |

## A.2 Elemental and Compound Thermodynamic Reference Data

| Species | Property | Value | Relevance |
|---|---|---|---|
| Si | Melting point | 1414°C | Upper thermal process bound; not typically approached in channel hole etch conditions |
| SiF4 | Boiling point | -86°C (gas at RT) | Primary volatile etch byproduct; confirms removability, Chapter 3, Section 5.1 |
| CO | Boiling point | -192°C (gas at RT) | Carbon/polymer removal byproduct, Chapter 3, Section 5.1 |
| CO2 | Sublimation point | -78.5°C | Carbon/polymer removal byproduct, Chapter 3, Section 5.1 |
| COF2 | Boiling point | -83°C | Fluorocarbon oxidation byproduct, Chapter 3, Section 5.1 |
| N2 | Boiling point | -196°C (gas at RT) | Nitride etch byproduct, chemically inert, Chapter 4, Section 2.2 |
| H3PO4 | Boiling point (85% aqueous) | ~158°C | Sacrificial nitride removal chemistry operating temperature reference, Chapter 14, Section 2.1 |
| W (tungsten) | Melting point | 3422°C | Word line fill metal; thermal stability reference, Chapter 14, Section 3.2 |
| TiN | Decomposition/stability | Stable to >2900°C (decomposition, not simple melting) | Word line barrier layer thermal stability, Chapter 14, Section 3.1 |

## A.3 Fluorocarbon Gas Species Reference

| Gas | Formula | Molecular Weight (g/mol) | C:F Ratio | Primary Role |
|---|---|---|---|---|
| Carbon tetrafluoride | CF4 | 88.0 | 1:4 | Baseline fluorine source, mask-open chemistry component |
| Octafluorocyclobutane | C4F8 | 200.0 | 1:2 | Primary sidewall-passivating species |
| Hexafluorobutadiene | C4F6 | 162.0 | 2:3 | Maximum sidewall protection chemistry |
| Trifluoromethane | CHF3 | 70.0 | 1:3 (+H) | Moderate polymer-forming, hydrogen-containing |
| Sulfur hexafluoride | SF6 | 146.1 | N/A (no carbon) | Fluorine source without polymer-forming carbon |

## A.4 Elemental Properties Relevant to Ionization and Transport (Chapter 10)

| Species | Property | Value | Relevance |
|---|---|---|---|
| Ar | Atomic mass | 39.95 amu | Dilution/sputtering gas; ion mass in sheath voltage scaling, Chapter 5, Section 5.1 |
| He | Atomic mass | 4.00 amu | Thermal transport carrier gas, Chapter 3, Section 3.3 |
| F (atomic) | Atomic mass | 19.00 amu | Primary chemical etchant species |
| Electron | Mass | 9.109×10⁻³¹ kg | Electron heating/dissociation physics, Chapter 9, Part 1 |

## A.5 Physical Constants Used in This Book's Worked Examples

| Constant | Symbol | Value |
|---|---|---|
| Vacuum permittivity | $\epsilon_0$ | 8.85×10⁻¹² F/m |
| Elementary charge | $e$ | 1.602×10⁻¹⁹ C |
| Boltzmann constant | $k_B$ | 1.381×10⁻²³ J/K |
| Silicon Young's modulus (representative) | $E_s$ | ~130 GPa |
| Silicon Poisson's ratio (representative) | $\nu_s$ | ~0.28 |

---

*Note on data provenance: the values in this appendix are representative, order-of-magnitude-correct figures drawn from general materials science and semiconductor processing literature, intended to support the worked examples throughout this book. Production process development requires fab- and tool-specific characterization rather than reliance on these generic reference values, consistent with the caution raised throughout Chapters 2-3 regarding deposition-recipe-dependent material properties.*
