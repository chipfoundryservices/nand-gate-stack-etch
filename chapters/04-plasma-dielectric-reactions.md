# Chapter 4: Plasma-Dielectric Surface Reactions in Ultra-High-AR Features

## Executive Summary

Chapter 3 established the gas-phase chemistry of channel hole etch. This chapter moves from the gas phase to the surface: the specific, sequential molecular mechanisms by which ions and neutrals delivered to an oxide or nitride surface actually remove material, how the ion-assisted and polymer-mediated steps interact kinetically, and — the focus unique to this chapter — how these surface mechanisms change character once they occur at the bottom of a feature tens of microns deep and only 100-150nm wide, rather than on an open, unconfined surface. This chapter builds the surface-kinetics foundation that Chapter 10's quantitative aspect-ratio-dependent etch model rests on, and that Chapter 11's profile-defect analysis (bowing, twisting, necking) draws on directly.

---

## Part 1: The Ion-Assisted Etch Mechanism

### 1.1 Why Chemical Etching Alone Is Insufficient

Atomic fluorine reacts spontaneously with SiO2 and Si3N4 even without ion bombardment, but this spontaneous chemical etch rate is generally slow and, critically, isotropic — it proceeds in all directions with no preference for the direction normal to the ion-exposed bottom of a feature. If spontaneous chemical etching were the dominant mechanism, channel hole etch could not achieve the vertical, anisotropic profiles required (Chapter 1, Section 4.3's acceptance criteria).

Ion bombardment transforms this picture through several concurrent, physically distinct mechanisms:

**Damage-enhanced chemical etching.** Energetic ion impact breaks Si-O and Si-N bonds at and near the surface, creating a damaged, chemically activated surface layer that reacts with fluorine far more readily than the undamaged bulk material. This is often the dominant contribution to ion-assisted etch rate in the energy ranges typical of channel hole etch (hundreds of eV, Chapter 9).

**Direct physical sputtering.** At sufficient ion energy, momentum transfer directly ejects surface atoms regardless of chemical reactivity. This contributes a smaller fraction of total etch rate in fluorine-rich chemistries (where chemical pathways dominate) but becomes proportionally more significant in fluorine-starved or heavily polymer-covered conditions, and is the primary mechanism by which ion bombardment clears polymer from the feature bottom (Chapter 3, Section 5.3).

**Polymer layer removal, enabling continued chemical access.** As developed in Chapter 3, ion bombardment continuously sputters/thins the polymer layer at ion-exposed surfaces, which does not itself remove the underlying oxide/nitride but is a necessary precondition for continued fluorine access to the surface beneath.

### 1.2 A Simplified Rate Expression

A widely used simplified framework (the "ion-assisted" or combined flux model) expresses net etch rate as approximately proportional to the product of neutral (chemical) flux and a function of ion flux and energy, rather than a simple additive sum of independent chemical and physical rates:

$$R_{\text{etch}} \approx k \cdot \Gamma_n \cdot f(\Gamma_i, E_i)$$

where $\Gamma_n$ is neutral reactant flux (primarily F and CFx species reaching the surface), $\Gamma_i$ is ion flux, $E_i$ is ion energy, and $f(\Gamma_i, E_i)$ is a saturating function — etch rate increases with ion flux/energy up to a point, beyond which further increases provide diminishing additional etch rate because the surface reaction becomes neutral-flux-limited rather than ion-flux-limited. This saturating character is why, as developed fully in Chapter 10, increasing ion energy alone cannot indefinitely compensate for reduced ion or neutral flux reaching the bottom of an extreme-AR feature — at some point the system is limited by whichever flux (ion or neutral) is scarcer, and extreme-AR transport (Section 3 below) determines which that is.

### 1.3 Why the Reaction Is Surface-Limited, Not Bulk-Limited

A key simplifying assumption underlying essentially all of this chapter's analysis: etch reactions occur at the exposed surface, within a thin (sub-nanometer to few-nanometer) reaction/damage layer, not throughout the bulk film. This is why etch rate depends on *flux* (particles reaching the surface per unit time per unit area) rather than, e.g., total gas-phase concentration integrated over feature volume. This surface-limited character is precisely what makes the transport problem in Part 3 of this chapter so consequential: if the reaction were somehow bulk-limited, feature geometry would matter far less, because material deep inside the feature could react with reactants already present in the gas filling the feature rather than depending on continuous resupply from the feature opening.

---

## Part 2: Material-Specific Surface Reaction Pathways

### 2.1 SiO2 Surface Reaction Sequence

1. Fluorine-containing species (F, CFx+) adsorb onto or impact the SiO2 surface
2. Ion bombardment creates a damaged, fluorinated surface layer (often described as a SiOxFy reaction layer, a few atomic layers thick)
3. Within this reaction layer, Si-F bond formation proceeds preferentially at damaged/strained Si-O bond sites
4. Sufficient fluorination of a given surface silicon atom (typically requiring multiple F atoms per Si, consistent with SiF4's stoichiometry) permits desorption as volatile SiF4, along with associated oxygen as CO/CO2 (from reaction with carbon supplied by the fluorocarbon chemistry itself, Chapter 3, Section 1.1) or, under oxygen-poor conditions, potentially as other volatile Si-O-F species

### 2.2 Si3N4 Surface Reaction Sequence

The nitride reaction sequence is mechanistically similar in its ion-assisted/fluorination structure but differs in two consequential ways:

**Nitrogen byproduct pathway.** Rather than forming CO/CO2 as the "non-silicon" byproduct (as oxide does), nitride releases nitrogen primarily as N2 (highly stable, chemically inert, readily pumped) or as CN-containing species when carbon from the fluorocarbon chemistry participates. N2's chemical inertness means, unlike oxide's byproducts, there is minimal possibility of nitrogen byproducts re-entering and influencing the ongoing surface chemistry — a comparatively "clean" byproduct pathway relative to oxide's.

**Bond strength and reaction layer differences.** Si-N bonds are, on average, somewhat weaker than Si-O bonds (consistent with nitride's generally higher spontaneous and ion-assisted etch rate relative to oxide under comparable fluorine-rich conditions, absent deliberate selectivity engineering — Chapter 12). This intrinsic reactivity difference is the starting point for essentially all oxide/nitride selectivity control discussed in Chapter 12: achieving a desired etch rate ratio (rather than nitride's naturally faster rate) requires deliberately suppressing nitride's intrinsic reactivity advantage, typically through polymer-mediated or ion-energy-mediated means, not through finding a chemistry that is naturally oxide-selective from first principles.

### 2.3 Polymer Layer as a Diffusion Barrier, Not Just a Physical Shield

Section 1.1's description of polymer as sidewall "protection" is accurate but incomplete without specifying the mechanism: the polymer layer protects not primarily by being mechanically impermeable, but by acting as a **diffusion barrier** that fluorine must cross before reaching the underlying oxide/nitride surface. A thicker, more cross-linked polymer layer presents a longer diffusion path and therefore a lower effective fluorine flux reaching the actual oxide/nitride interface beneath it, reducing but not instantaneously zeroing sidewall etch rate.

This diffusion-barrier framing matters because it explains why sidewall protection is a matter of *degree*, continuously tunable by polymer thickness and composition (which are themselves set by the chemistry choices in Chapter 3 and the ion energy/flux conditions in Chapter 9), rather than a binary protected/unprotected state. It also explains why polymer composition (cross-link density, carbon content) affects sidewall protection quality independent of polymer thickness alone — a thin, highly cross-linked polymer can outperform a thicker, poorly cross-linked one, a subtlety recipe development must account for when tuning chemistry for profile control (Chapter 11).

---

## Part 3: How These Mechanisms Change Inside Ultra-High-AR Features

### 3.1 The Transport Prerequisite

Every mechanism described in Parts 1 and 2 requires that ions and neutral reactive species actually reach the surface in question. On an open, unconfined wafer surface, this is essentially guaranteed by the bulk plasma's ion and neutral flux arriving directly from above. Inside a feature with aspect ratio exceeding roughly 10:1 — and especially at the 50:1-100:1+ aspect ratios of channel hole etch — this guarantee breaks down, and transport into the feature becomes a rate-limiting step in its own right, logically and temporally prior to the surface reactions this chapter has described.

This chapter does not derive the full quantitative transport model (reserved for Chapter 10), but establishes the qualitative mechanisms that transport must account for, since they directly determine which of this chapter's surface reaction steps becomes rate-limiting at depth.

### 3.2 Ion Trajectory Narrowing

Ions arriving at the top of a feature typically have a narrow but non-zero angular spread around the vertical (normal to the wafer) direction, originating from the ion sheath's finite temperature and from the specific sheath/presheath structure the reactor's RF design produces (Chapter 9). On an open surface, this angular spread is largely inconsequential. Inside a deep, narrow feature, however, any ion arriving at even a small angle off-vertical will, at sufficient depth, strike the sidewall rather than continuing to the bottom — a simple geometric consequence of the feature's narrow diameter relative to its depth.

The practical result: the angular distribution of ions successfully reaching the *bottom* of a feature narrows progressively with depth, as larger-angle trajectories are progressively "filtered out" by sidewall collision at shallower depths, leaving only the most nearly-vertical trajectories to reach the greatest depths. This filtering is a purely geometric/trajectory effect, distinct from (though it interacts with) the charging effects discussed in Chapter 11, and is one of the two primary mechanisms (alongside Section 3.3's neutral transport) responsible for the ion flux depletion with depth that drives Chapter 10's ARDE model and Chapter 3, Section 5.3's etch-stop discussion.

### 3.3 Neutral Species Transport in the Knudsen Regime

Neutral reactive species (F, CFx radicals) transport into the feature through gas-phase diffusion rather than directed, sheath-accelerated trajectories. At the pressures typical of channel hole etch (commonly a few mTorr to tens of mTorr) and the sub-150nm feature diameters involved, the mean free path of gas molecules is frequently comparable to or larger than the feature diameter itself — the defining condition of the **Knudsen transport regime**, in which molecules travel from one sidewall collision directly to another (or to the bottom) without intervening gas-phase collisions, rather than diffusing via the continuum (Fickian) diffusion more familiar from larger-scale or higher-pressure transport problems.

In this regime, each time a neutral molecule strikes the sidewall, it has some probability of being consumed (reacting with or sticking to the surface, contributing to polymer formation or direct chemical etching) rather than reflecting onward toward the bottom. This per-collision consumption probability, combined with the large number of sidewall collisions a molecule must statistically undergo to traverse a deep, narrow feature, produces a transport efficiency that falls off with aspect ratio — more steeply than simple geometric line-of-sight arguments alone would predict, because every sidewall collision is a chance for the molecule to be lost from the population reaching the bottom. Chapter 10 develops this Knudsen transport efficiency quantitatively (via a transport probability model closely related to Clausing's classical treatment of molecular flow through tubes); this chapter establishes why the regime applies and what physically happens at each sidewall encounter.

### 3.4 Why Neutrals and Ions Deplete at Different Rates With Depth

Sections 3.2 and 3.3 describe two distinct depletion mechanisms with different functional dependence on depth and feature geometry: ion depletion is primarily a trajectory-filtering (angular) effect, while neutral depletion is primarily a Knudsen-transport (collision-probability) effect. Because these mechanisms do not necessarily attenuate ion and neutral flux at the same rate as aspect ratio increases, the *ratio* of ion flux to neutral flux reaching the bottom of a feature can shift substantially with depth, even if that ratio was deliberately tuned to a desired value at the feature's top opening.

This shifting ion-to-neutral ratio with depth is the direct mechanistic link between this chapter's surface chemistry and Chapter 3, Section 5.3's polymer accumulation/etch-stop analysis: if ion-assisted polymer removal (Section 1.1) depletes faster with depth than neutral-driven polymer deposition does, the bottom-of-feature polymer balance shifts toward net accumulation specifically because of this differential transport, not because of any change in the gas-phase chemistry supplied at the feature's top. Recipe and chemistry choices made using Chapter 3's framework must therefore be understood as setting conditions at the feature's *top opening*; this chapter and Chapter 10 together explain why the conditions actually realized at the feature's *bottom* can differ substantially, and in a depth-dependent way, from those top-opening conditions.

---

## Part 4: Reaction Layer Thickness and Its Interaction With Film Transitions

### 4.1 Reaction Layer Persistence Across an Oxide-Nitride Interface

Because the reaction/damage layer described in Part 2 is a few atomic layers thick and forms dynamically under ongoing ion bombardment, it does not instantaneously reset to a "clean" state the moment the etch front crosses from an oxide layer into the adjacent nitride layer (or vice versa) in the alternating stack (Chapter 2). There is a brief transition interval, on the scale of the reaction layer's own formation timescale, during which the surface reaction layer carries some compositional memory of the previously etched material.

In practice, for the film thicknesses involved (tens of nanometers per layer, Chapter 2, Section 1.1) relative to the sub-nanometer reaction layer scale, this transition interval represents a small fraction of the total time spent etching through any single layer, and is generally not a first-order concern for bulk etch rate. It is noted here because it becomes relevant at the margins — particularly for endpoint detection signal interpretation at layer transitions (Appendix F) and for understanding why etch rate measured immediately after a layer transition can show brief, small transients distinct from the steady-state rate within that layer.

### 4.2 Why Averaged Selectivity, Not Instantaneous Selectivity, Governs Practical Recipe Design

Because the etch front spends the overwhelming majority of its time within the steady-state regime of whichever single film it is currently etching (Section 4.1), and because a full channel hole etch transits dozens to hundreds of such film layers sequentially, the practically relevant selectivity metric for recipe design is the **time-averaged or depth-averaged** oxide:nitride etch rate ratio across the many layer transitions the etch will experience — not the instantaneous selectivity at any single, momentary point in the etch. This averaged-selectivity framing, grounded in this chapter's surface mechanism discussion, is developed into a full quantitative treatment in Chapter 12.

---

## Part 5: Quantifying Mechanism Contributions

### 5.1 Relative Contribution of Etch Mechanisms by Condition

The three mechanisms introduced in Part 1 (damage-enhanced chemical etching, direct physical sputtering, polymer removal enabling continued access) do not contribute equally across all process conditions. The following table summarizes their relative importance across the regimes most relevant to channel hole etch:

| Condition | Dominant Mechanism | Secondary Mechanism | Practical Implication |
|---|---|---|---|
| Fluorine-rich, moderate ion energy (typical bulk etch step) | Damage-enhanced chemical etching | Polymer removal (minimal polymer present) | Etch rate scales with both neutral flux and ion flux/energy per Section 1.2's saturating model |
| Fluorine-starved or heavily polymerized surface | Polymer removal (rate-limiting prerequisite) | Damage-enhanced chemical etching (occurs only after polymer clears) | Etch rate effectively gated by ion-assisted polymer clearing rate, not by underlying film reactivity |
| High ion energy, fluorine-poor (e.g., Ar-dominant, minimal reactive gas) | Direct physical sputtering | Damage-enhanced chemical etching (minimal, little F available) | Low absolute etch rate, poor selectivity (sputtering is comparatively material-nonspecific), rarely used alone for bulk channel hole etch |
| Low ion energy, fluorine-rich (e.g., deep in a feature where ion flux has attenuated per Section 3.2) | Damage-enhanced chemical etching, but flux-starved | Polymer removal severely reduced | Approaches the etch-stop condition developed in Chapter 3, Section 5.3 and Chapter 10 |

This table makes explicit why no single mechanism can be described as "the" channel hole etch mechanism in isolation — production recipes are tuned to keep the process operating in the first row's regime for as much of the feature depth as possible, while the third and fourth rows describe failure modes the rest of this book's process control chapters (7, 9, 10) are specifically designed to avoid or delay to greater depth.

### 5.2 A Worked Reaction-Layer Kinetics Estimate

To make Section 1.1's damage-enhanced mechanism concrete, consider a simplified first-order estimate of reaction layer formation and consumption. If the ion-induced damage layer forms at a rate proportional to ion flux $\Gamma_i$ and is consumed (converted to volatile byproduct and removed) at a rate proportional to neutral flux $\Gamma_n$ reacting with that damaged layer, a steady-state damaged layer thickness $\delta_d$ emerges from the balance:

$$\delta_d \approx \frac{\alpha \Gamma_i}{\beta \Gamma_n}$$

for proportionality constants $\alpha$ (damage formation efficiency per ion) and $\beta$ (chemical consumption rate constant of damaged material per unit neutral flux). Overall etch rate under this simplified picture is then limited by whichever process — damage formation or chemical consumption — is slower, consistent with Section 1.2's saturating rate expression.

**Illustrative implication:** at the top of a channel hole, where both $\Gamma_i$ and $\Gamma_n$ are near their maximum, undepleted values, this balance is set by the bulk recipe's gas chemistry and power settings (Chapters 3, 9) and is, by design, tuned to sit in a regime where neither flux is severely limiting. As depth increases and $\Gamma_i$ depletes faster than $\Gamma_n$ (Section 3.4), the ratio $\Gamma_i/\Gamma_n$ falls, driving $\delta_d$ down — a thinner, less chemically activated damage layer forms per unit time, directly reducing the chemical consumption rate even though neutral flux (fluorine availability) may still be comparatively abundant. This is the mechanistic reason why etch rate falloff with depth is not simply a story of "running out of fluorine," a common oversimplification; it is at least as much a story of insufficient ion-induced surface activation to make the available fluorine chemically effective, a distinction with direct consequences for how Chapter 9's pulsed-bias strategies and Chapter 10's compensation approaches are designed, since those strategies target ion delivery specifically rather than simply increasing total reactive gas flow.

---

## Summary and Forward Look

Channel hole etch proceeds through ion-assisted surface reactions that combine damage-enhanced chemical etching, direct sputtering, and polymer-layer-mediated protection, acting on oxide and nitride surfaces whose differing intrinsic bond strengths and byproduct pathways (CO/CO2 for oxide, N2 for nitride) are the starting point for all subsequent selectivity engineering. Inside an ultra-high-aspect-ratio feature, however, these surface mechanisms cannot be understood in isolation from the transport problem that gets reactants to the surface in the first place: ion trajectory narrowing and Knudsen-regime neutral transport attenuate ion and neutral flux at different, depth-dependent rates, shifting the ion-to-neutral balance realized at the feature bottom away from the balance set at the feature's top opening.

This transport/surface-chemistry coupling is the physical foundation for the quantitative aspect-ratio-dependent etch (ARDE) model developed in Chapter 10, and for the bowing, twisting, and necking profile defects analyzed in Chapter 11. Before reaching those chapters, however, Part II of this book turns to the chamber and reactor engineering question: what physical reactor architecture is actually capable of delivering and controlling the ion energy, ion flux, and neutral chemistry this chapter has shown to be necessary, at the scale and precision 3D NAND channel hole etch demands.
