# 3D NAND Flash Memory Stack Etch — Chapter Index

## Navigation & Quick Reference

---

## Front Matter

| Section | Status | Overview |
|---------|--------|----------|
| [README.md](README.md) | ✓ | Book overview, audience, scope, and file organization |
| [PREFACE.md](PREFACE.md) | ✓ | Why 3D NAND etch differs from prior etch processes, discipline breadth, intellectual framework |

---

## Part I: 3D NAND Fundamentals

### Foundational Architecture, Materials, and Chemistry

| Chapter | File | Status | Key Topics |
|---------|------|--------|-----------|
| **1** | [01-3d-nand-architecture.md](chapters/01-3d-nand-architecture.md) | ✓ | 3D NAND device architecture, why vertical scaling replaced planar scaling, charge-trap vs. floating-gate cells, string/block/plane organization, industrial context and roadmap |
| **2** | [02-charge-trap-stack-materials.md](chapters/02-charge-trap-stack-materials.md) | ✓ | ONO (oxide-nitride-oxide) charge-trap stack, OPOP (oxide-polysilicon) replacement-gate stack, film deposition properties, stress and composition effects on etch |
| **3** | [03-fluorocarbon-chemistry.md](chapters/03-fluorocarbon-chemistry.md) | ✓ | CF4/C4F8/C4F6/CHF3 plasma chemistry, SF6 and O2 co-reactants, polymer passivation formation, byproduct volatility |
| **4** | [04-plasma-dielectric-reactions.md](chapters/04-plasma-dielectric-reactions.md) | ✓ | Ion-assisted dielectric etch mechanisms, fluorocarbon polymer layer dynamics, surface reaction pathways unique to ultra-high-AR features |

---

## Part II: Chamber Design for 3D NAND Etch

### Engineering Architecture for Extreme Aspect Ratio

| Chapter | File | Status | Key Topics |
|---------|------|--------|-----------|
| **5** | [05-reactor-architecture.md](chapters/05-reactor-architecture.md) | ✓ | ICP and CCP source architectures for high-AR etch, dual-frequency designs, pulsed-plasma reactor requirements |
| **6** | [06-gas-distribution.md](chapters/06-gas-distribution.md) | ✓ | Gas injection geometry, residence time control, Knudsen-regime transport into deep features, byproduct removal |
| **7** | [07-pressure-power-bias.md](chapters/07-pressure-power-bias.md) | ✓ | Pressure-power-bias phase space mapping, process windows for channel hole etch, stability regions |
| **8** | [08-chamber-materials-passivation.md](chapters/08-chamber-materials-passivation.md) | ✓ | Chamber wall materials, polymer passivation and conditioning, seasoning effects, chamber-to-chamber matching |
| **9** | [09-rf-pulsing-systems.md](chapters/09-rf-pulsing-systems.md) | ✓ | Multi-frequency RF systems, pulsed source/bias power, independent ion energy and flux control |

---

## Part III: Process Phenomena & Control

### Physics of Extreme Aspect Ratio Etch

| Chapter | File | Status | Key Topics |
|---------|------|--------|-----------|
| **10** | [10-arde-extreme-ar.md](chapters/10-arde-extreme-ar.md) | ✓ | ARDE at 50:1-100:1+ aspect ratio, transport-limited vs. reaction-limited regimes, Knudsen transport models |
| **11** | [11-ion-transport-sidewall.md](chapters/11-ion-transport-sidewall.md) | ✓ | Ion trajectory evolution with depth, sidewall passivation balance, bowing/twisting/necking mechanisms, charging effects |
| **12** | [12-selectivity-engineering.md](chapters/12-selectivity-engineering.md) | ✓ | Oxide/nitride/polysilicon selectivity in alternating stacks, averaged selectivity targets, stop-layer behavior |
| **13** | [13-staircase-contact-etch.md](chapters/13-staircase-contact-etch.md) | ✓ | Staircase formation via trim-etch cycling, step height control, multi-step CD budget |
| **14** | [14-word-line-replacement.md](chapters/14-word-line-replacement.md) | ✓ | Slit etch, sacrificial nitride removal, gate-last metal fill interface, mechanical stability during replacement |

---

## Part IV: Production Scale & Integration

### Manufacturing Implementation at High Layer Count

| Chapter | File | Status | Key Topics |
|---------|------|--------|-----------|
| **15** | [15-cluster-integration-yield.md](chapters/15-cluster-integration-yield.md) | ✓ | Cluster tool architecture, metrology feedback loops, run-to-run control, yield management at 128+ layers |

---

## Back Matter

| Appendix | File | Status | Content |
|----------|------|--------|---------|
| **Glossary** | [appendices/glossary.md](appendices/glossary.md) | ✓ | 3D NAND etch-specific terminology and acronyms |
| **Appendix A** | [appendices/thermodynamic-data.md](appendices/thermodynamic-data.md) | ✓ | Thermodynamic and material property data tables (SiO2, Si3N4, polysilicon, fluorocarbon species) |
| **Appendix B** | [appendices/material-compatibility.md](appendices/material-compatibility.md) | ✓ | Material compatibility matrix for chamber components under fluorocarbon chemistry |
| **Appendix C** | [appendices/standard-procedures.md](appendices/standard-procedures.md) | ✓ | Standard operating procedures for channel hole, staircase, and slit etch |
| **Appendix D** | [appendices/correction-tables.md](appendices/correction-tables.md) | ✓ | ARDE / twist / bow correction lookup tables, aspect-ratio indexed |
| **Appendix E** | [appendices/thermal-charging-calculations.md](appendices/thermal-charging-calculations.md) | ✓ | Thermal and differential charging calculations with worked examples |
| **Appendix F** | [appendices/endpoint-detection.md](appendices/endpoint-detection.md) | 🚩 | Endpoint detection calibration for multi-layer stack etch |

---

## Status Legend

| Symbol | Meaning |
|--------|---------|
| ✓ | Complete and published |
| 🔨 | In development |
| 📋 | Outline ready, writing in progress |
| 🚩 | Not yet started |

---

## Reading Recommendations

### For Process Engineers
**Optimal path:** Preface → Part I (Ch 1-4) → Part III (Ch 10-14) → Appendices D-F

This path emphasizes recipe development and process control without deep chamber engineering.

### For Equipment Engineers
**Optimal path:** Preface → Part II (Ch 5-9) → Part III (Ch 10-11) → Appendices A-C

This path emphasizes chamber design and material compatibility.

### For Integration Engineers
**Optimal path:** Part I (Ch 1-2) → Part III (Ch 12-14) → Part IV (Ch 15) → Appendix C

This path emphasizes process flow integration across channel hole, staircase, and word line replacement steps.

### For Equipment Investors & Analysts
**Optimal path:** Part I (Ch 1) → Part II (Ch 5) → Part III (Ch 10-11) → Part IV (Ch 15)

This path emphasizes technology differentiation and production economics without heavy derivation.

### Complete Reading (Recommended for Deep Understanding)
**Front to back:** Read in order, Part I → Part II → Part III → Part IV → Appendices.

This provides the most rigorous foundation and cross-disciplinary integration.

---

## How to Use This Index

1. **Start here** if you're new to the book—pick your reading path based on your role
2. **Reference this** while reading chapters to understand where each chapter fits in the larger narrative
3. **Quick lookup** when you need specific topics (use the Key Topics column)
4. **Status tracking** to see which chapters are ready for reading vs. in development

---

**Development Phase:** Manuscript Development (Front matter published, Chapters 1-15 and appendices in progress)
