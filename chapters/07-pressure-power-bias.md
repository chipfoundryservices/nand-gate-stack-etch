# Chapter 7: Pressure-Power-Bias Phase Space for Channel Hole Etch

## Executive Summary

Chapters 5 and 6 established the reactor architecture and gas distribution systems channel hole etch depends on. This chapter integrates those pieces into a unified process window: the three-dimensional space of chamber pressure, source power, and bias power (and, for CCP architectures, the equivalent total/split power variables) within which an acceptable channel hole etch process can actually run. We map the stability boundaries of this space, show how the competing requirements developed in Chapters 3-6 translate into concrete regions of acceptable and unacceptable operation, and establish the phase-space framework that Chapter 9's RF/pulsing discussion and Chapter 10's quantitative ARDE treatment both build directly upon.

---

## Part 1: The Three Primary Process Variables

### 1.1 Pressure

Chamber pressure (typically a few mTorr to several tens of mTorr for channel hole etch) simultaneously affects:
- **Mean free path and Knudsen transport regime** (Chapter 4, Section 3.3; Chapter 6, Part 3): lower pressure generally favors longer mean free path, improving neutral transport efficiency into deep features, up to the point where pressure becomes so low that insufficient neutral density remains to sustain adequate absolute reactive flux
- **Ion energy distribution width**: higher pressure generally increases collisional broadening of the ion energy distribution as ions cross the sheath, reducing the degree to which ion energy can be sharply, narrowly controlled — a consideration that interacts directly with Chapter 5's flux/energy decoupling discussion, since a broadened energy distribution partially undermines the benefit of precise bias power control if the sheath itself scrambles that precision through collisions
- **Plasma density achievable at a given input power** (Chapter 5, Section 2.2): generally higher at higher pressure, up to a point, before density growth saturates or reverses as excessive collisional losses begin to dominate

### 1.2 Source Power

Source power (ICP coil power, or the higher-frequency component in dual-frequency CCP, Chapter 5) primarily sets plasma density and therefore both ion and neutral generation rate. Within the phase space, source power is the primary lever for addressing Chapter 6's "sufficient absolute flux at the feature's top opening" requirement, independent of (though not completely decoupled from, per Chapter 5, Section 5.2's discussion of imperfect frequency orthogonality) the ion energy set by bias power.

### 1.3 Bias Power

Bias power (wafer electrode RF power, Chapter 5, Section 1.2/5.2) primarily sets ion energy at the wafer surface via sheath voltage. Within the phase space, bias power is the primary lever for the chemical activation (damage-enhanced etching, Chapter 4, Part 1) and polymer-clearing (Chapter 3, Section 3.2; Chapter 4, Section 5.2) functions that depend specifically on ion energy, as distinct from ion flux.

---

## Part 2: Mapping the Stability Region

### 2.1 Why Not All Combinations of Pressure, Source Power, and Bias Power Are Usable

A given combination of these three variables can fail to produce an acceptable channel hole etch process for several distinct reasons, each corresponding to a different boundary of the usable phase-space region:

**Insufficient ion energy boundary.** Below a minimum bias power (and therefore minimum sheath voltage/ion energy) for a given pressure and source power, ion-assisted damage-enhanced etching (Chapter 4, Part 1) becomes too slow to proceed at a commercially useful rate, and/or insufficient ion energy fails to adequately clear polymer at the feature bottom even at moderate aspect ratio, risking early etch stop (Chapter 3, Section 5.3).

**Excessive ion energy boundary.** Above a maximum bias power, mask erosion (Chapter 2, Section 5.2) accelerates beyond the available mask thickness budget for the required total etch time, and/or oxide/nitride selectivity (Chapter 12) degrades as ion-energy-dominated physical sputtering becomes less material-selective than the ion-assisted chemical mechanisms that dominate at more moderate energy.

**Insufficient source power / plasma density boundary.** Below a minimum source power for a given pressure, absolute ion and neutral flux delivered to the feature's top opening (Chapter 6) becomes too low to sustain adequate etch rate even before accounting for aspect-ratio-driven attenuation, resulting in unacceptably long total etch time or outright failure to clear the stack within any practical time budget.

**Excessive pressure boundary.** Above a maximum pressure for a given power configuration, Knudsen transport efficiency into deep features degrades (Chapter 4, Section 3.3; shorter mean free path means more sidewall collisions per unit depth, each with some probability of consuming the neutral species before it reaches greater depth) faster than the increased plasma density from higher pressure can compensate, net-reducing effective reactive flux reaching the feature bottom despite higher nominal flux at the top opening.

**Insufficient pressure boundary.** Below a minimum pressure for a given power configuration, absolute neutral density becomes too low to sustain adequate reaction rate even where ion flux and energy are otherwise favorable, and plasma stability itself can become marginal (very low pressure operation can approach the lower pressure limit at which the specific reactor architecture can sustain a stable discharge at all, a hard physical boundary distinct from the softer, etch-performance-driven boundaries above).

### 2.2 The Resulting Phase Space Picture

| Boundary | Variable Primarily Implicated | Underlying Chapter Reference | Consequence of Crossing |
|---|---|---|---|
| Insufficient ion energy | Bias power (low) | Chapter 4, Part 1; Chapter 3, Section 5.3 | Slow etch, early etch stop risk |
| Excessive ion energy | Bias power (high) | Chapter 2, Section 5.2; Chapter 12 | Mask exhaustion, degraded selectivity |
| Insufficient source power | Source power (low) | Chapter 6, Part 1 | Inadequate absolute flux, long/failed etch |
| Excessive pressure | Pressure (high) | Chapter 4, Section 3.3 | Degraded Knudsen transport, net flux loss at depth |
| Insufficient pressure | Pressure (low) | Plasma stability, absolute neutral density | Marginal discharge stability, inadequate reaction rate |

The usable process window is the region of pressure-source power-bias power space lying inside all five of these boundaries simultaneously — generally a comparatively narrow, specifically shaped region rather than a broad, forgiving one, which is a direct, quantitative expression of why channel hole etch process development requires careful, deliberate phase-space mapping rather than ad hoc parameter adjustment.

---

## Part 3: Depth-Dependent Shifting of the Effective Operating Point

### 3.1 Why a Fixed Recipe Setting Does Not Correspond to a Fixed Position in This Phase Space Throughout the Etch

Sections 1-2 describe the phase space in terms of the commanded, chamber-level pressure/source power/bias power settings. However, Chapter 4's transport analysis established that the conditions actually realized at the feature bottom (effective local ion energy distribution after collisional/trajectory effects, effective local neutral and ion flux after Knudsen/trajectory attenuation) diverge increasingly from the chamber-level commanded conditions as etch depth increases. This means a single, fixed commanded recipe setting corresponds to a *moving* effective operating point, in a feature-bottom-conditions sense, as the etch proceeds deeper into the stack — even though the chamber-level pressure, source power, and bias power settings may remain nominally constant throughout a given etch step.

### 3.2 Practical Consequence: Depth-Compensated Recipes

This depth-dependent drift is the direct motivation for depth-compensated (or "ramped") recipes, in which commanded source power, bias power, or gas chemistry (Chapter 3, Section 4.2) are deliberately increased or adjusted as the etch step progresses, specifically to counteract the known, characterizable drift in effective feature-bottom conditions and keep the *effective* operating point closer to a desired, stable position within the phase space mapped in Part 2, even as the *commanded* chamber-level settings change over time to achieve this. Chapter 10 develops the quantitative aspect-ratio-dependent model that such ramped recipes are tuned against, and Chapter 9 develops how pulsed bias/source power schemes provide additional, finer-grained tools for implementing this compensation beyond simple continuous ramping alone.

---

## Part 4: Temperature as an Implicit Fourth Variable

### 4.1 Why Temperature Is Not Independent of Pressure, Power, and Bias

Although this chapter's primary phase space is framed around pressure, source power, and bias power, wafer and chamber wall temperature are not independently settable in the same direct sense — they emerge as a consequence of the plasma conditions set by these three primary variables (via plasma heating of the wafer and chamber surfaces) combined with the chuck/chamber active cooling capacity (Chapter 5, Section 6.1; Chapter 8). Because etch rate, polymer deposition rate (Chapter 3), and byproduct volatility (Chapter 3, Section 5.1) are all temperature-sensitive, the achievable chuck cooling capacity effectively constrains how far into the high-power regions of the pressure/source power/bias power phase space a given reactor can operate while still holding wafer temperature within its own required process window.

### 4.2 Temperature-Driven Phase Space Contraction at High Power

In practice, this means the usable phase space region mapped in Part 2 is itself contingent on adequate thermal management: a reactor with superior chuck cooling capacity (Chapter 8) can access higher source and bias power combinations (useful for addressing the insufficient-flux and insufficient-ion-energy boundaries of Section 2.1) without violating wafer temperature limits, effectively enlarging its usable phase space relative to a thermally-limited reactor of otherwise identical plasma source design. This is a concrete, quantitative reason thermal management capability (addressed fully in Chapter 8) is treated throughout this book as a first-order chamber design consideration rather than a secondary engineering detail, since it directly determines how much of the plasma-physics-defined phase space from Parts 1-3 of this chapter a given piece of hardware can actually access in practice.

---

## Part 5: Representative Process Window Summary

### 5.1 Illustrative Operating Ranges

| Variable | Representative Range for Channel Hole Bulk Etch | Representative Range for Hard Mask Open Step (Chapter 2, Section 5.2) |
|---|---|---|
| Pressure | 5-30 mTorr | 10-50 mTorr (generally less transport-constrained, lower AR) |
| Source power (ICP) | 1500-4000 W | 500-2000 W |
| Bias power | 2000-6000 W (often pulsed, Chapter 9) | 200-1000 W |
| Wafer temperature | 10-60°C (chuck-controlled) | Comparable range, less critical given lower AR |

(Figures are illustrative, representative of the general ranges reported in public literature and typical for high-density etch platforms addressing this application; specific production recipes vary by manufacturer, tool platform, and generation, and are not disclosed at the level of exact values by any manufacturer for competitive reasons.)

### 5.2 Why the Bulk Etch Window Is Narrower and Shifted Relative to the Mask Open Window

Consistent with Chapter 3, Section 4.2's discussion of why real recipes are multi-step rather than single-blend, this table's two columns illustrate the same principle in the pressure/power/bias phase space: the hard mask open step, facing comparatively low aspect ratio and prioritizing selectivity to the underlying stack rather than deep transport, can operate acceptably across a wider, more forgiving region of the phase space. The bulk channel hole etch step, by contrast, must simultaneously satisfy all five boundary conditions from Section 2.1 at the most demanding (greatest depth, highest aspect ratio) point of the entire etch, generally forcing operation within a narrower, higher-power region of the phase space, and explaining why bulk channel hole etch recipes are tuned with considerably more care and sensitivity than the comparatively more robust mask-opening step that precedes them.

---

## Part 6: A Worked Stability-Margin Estimate

### 6.1 Framing the Problem

Suppose process characterization establishes that, for a given reactor and 128-layer stack target, acceptable etch outcomes (full clearing, CD within specification, no etch-stop) require effective ion-assisted etch rate at the stack bottom to remain above a minimum threshold $R_{min}$ throughout the etch. Using the saturating rate model from Chapter 4, Section 1.2, and the depth-dependent flux attenuation discussed in Chapter 4, Section 3 and Chapter 6, Part 3, this minimum-rate requirement translates into a minimum required *top-opening* flux (both ion and neutral) sufficient that, even after full-depth attenuation, the bottom-of-feature rate stays above $R_{min}$.

### 6.2 Illustrative Margin Calculation

Suppose characterization shows that, at the chamber's current source power setting, top-opening ion flux is $\Gamma_{i,0}$, and that at full stack depth (aspect ratio ~55:1 for a 128-layer single-tier target, Chapter 1, Section 5.2) the transport-limited bottom flux is empirically found to be approximately 35% of $\Gamma_{i,0}$ (a representative illustrative figure consistent with the transport attenuation trends developed fully in Chapter 10). If process characterization separately shows that $R_{min}$ requires bottom ion flux of at least $0.30 \times \Gamma_{i,0}$ (i.e., at least 30% of the top-opening value) to sustain adequate damage-enhanced etching per Chapter 4's mechanism, the process has only a modest margin:

$$\text{Margin} = \frac{0.35 - 0.30}{0.30} \approx 17\%$$

A margin this narrow means comparatively small process drifts — a few percent reduction in source power from chamber conditioning changes (Chapter 8), a modest increase in effective aspect ratio from stack height variation (Chapter 2, Section 1.2's layer thickness drift), or minor gas distribution non-uniformity (Chapter 6, Part 2) — can push the effective bottom flux below $R_{min}$ at some wafer locations or some lots, producing exactly the kind of marginal, intermittent etch-stop or clearing failures that are notoriously difficult to debug in production, since the nominal recipe "looks correct" on average while occasionally failing at the margins. This worked example is why production process characterization (Chapter 15) typically targets considerably larger nominal margins than this illustrative 17% figure, specifically to buffer against the many small, compounding sources of real-world process variation that a purely nominal, single-point process characterization would not reveal.

### 6.3 Why Margin, Not Just Nominal Performance, Is the Correct Design Target

This worked example illustrates a broader principle this book returns to repeatedly: a channel hole etch recipe that achieves nominally acceptable performance at the exact characterization conditions is not, by itself, evidence of a robust process. The phase space mapped in this chapter has boundaries (Part 2) that are generally not sharp cliffs but regions of progressively degrading margin, and a well-designed recipe deliberately operates with comfortable margin from all five boundaries simultaneously, not merely inside the boundary that happens to be currently best characterized or most visible in a given qualification dataset.

---

## Part 7: Phase Space Shifts Across Layer-Count Generations

### 7.1 Why the Same Reactor's Usable Window Changes With Target Layer Count

As layer count increases from one generation to the next (Chapter 1, Section 5.2), target aspect ratio increases correspondingly, which — per Section 2.1's excessive-pressure and insufficient-source-power boundaries — generally shifts the usable phase space toward lower pressure (favoring Knudsen transport, Chapter 4, Section 3.3) and higher source power (compensating for the flux this lower pressure and the higher aspect ratio jointly demand). A reactor's phase space window characterized and qualified for a 96-layer generation does not automatically remain centered correctly for a 176-layer generation target; it must be re-characterized, and may require hardware upgrades (higher maximum source/bias power supply capability, improved chuck cooling per Section 4) if the new generation's requirements fall outside the original hardware's achievable range entirely, rather than merely requiring a recipe parameter shift within the same hardware's existing capability.

### 7.2 Implications for Capital Equipment Planning

This generation-to-generation phase space shift is the direct, practical reason capital equipment roadmaps for channel hole etch tools (Chapter 1, Section 6.1) must anticipate future layer-count targets rather than being specified purely against the current generation's requirements — a tool specified with headroom in maximum source power, bias power, and minimum achievable pressure (and corresponding pumping capacity) can be re-qualified for a subsequent generation through recipe development alone, whereas a tool specified at exactly the current generation's requirements may require hardware replacement rather than simple requalification once the next generation's phase space shift exceeds the original hardware's design margin.

---

## Summary and Forward Look

Channel hole etch must operate within a bounded region of pressure, source power, and bias power space, defined by competing requirements for ion energy (sufficient for chemical activation and polymer clearing, not so much as to exhaust the mask or degrade selectivity), absolute flux (sufficient plasma density to supply the feature's top opening), and transport efficiency (pressure low enough to favor Knudsen-regime neutral transport, not so low as to starve absolute reaction rate or destabilize the discharge). This phase space is further constrained by achievable thermal management, and the effective operating point actually realized at the bottom of a feature drifts within this space as etch depth increases, motivating the depth-compensated, ramped recipe structures used in production.

The next chapter turns to the chamber hardware dimension most directly responsible for sustaining this phase space over long production runs: the materials chosen for plasma-facing chamber surfaces, and the polymer passivation and conditioning behavior of those surfaces, which this chapter has so far treated as a fixed backdrop but which Chapter 8 will show to be an actively evolving system in its own right.
