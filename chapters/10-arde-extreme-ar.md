# Chapter 10: Aspect Ratio Dependent Etching at Extreme Aspect Ratio

## Executive Summary

Every preceding chapter in this book has anticipated this one. Chapter 4 established the surface mechanisms and the qualitative transport mechanisms (ion trajectory narrowing, Knudsen neutral transport) that cause etch rate to fall with depth. Chapter 6 connected chamber-scale gas delivery to the feature-scale transport problem. Chapter 7 showed how the effective operating point drifts with depth within the pressure-power-bias phase space. Chapter 9 introduced pulsing as a tool for addressing that drift. This chapter now derives the quantitative aspect-ratio-dependent etch (ARDE) model itself: the mathematical relationship between aspect ratio and etch rate, built from Knudsen transport theory and ion trajectory geometry, that explains why etch rate at 100:1 aspect ratio can fall to a small fraction of its low-AR value, why this falloff accelerates rather than merely continuing linearly as aspect ratio increases, and what quantitative compensation strategies the preceding chapters' tools (pressure, power, chemistry, pulsing) can and cannot achieve against it.

---

## Part 1: Defining ARDE Quantitatively

### 1.1 The Normalized ARDE Metric

Aspect ratio dependent etching is most commonly quantified as the ratio of etch rate at a given (typically high) aspect ratio to etch rate measured in a low-aspect-ratio or unconfined (blanket film) reference condition, under otherwise identical process conditions:

$$\text{ARDE}(AR) = \frac{R(AR)}{R(AR \rightarrow 0)}$$

A value of 1.0 indicates no aspect-ratio-driven rate loss; values approaching zero indicate etch rate has collapsed toward the etch-stop condition (Chapter 3, Section 5.3) at that aspect ratio. Channel hole etch characterization typically reports this metric across a measured range of test structure aspect ratios, then extrapolates or models behavior at the production target aspect ratio where direct test structures matching the full stack depth may not always be available during early process development.

### 1.2 Why a Single Universal ARDE Curve Does Not Exist

Unlike some simpler etch systems where ARDE can be reasonably approximated by a single, chemistry-independent transport model, Chapter 4's analysis established that channel hole etch rate loss with depth results from the combination of ion trajectory narrowing (geometric, chemistry-independent) and Knudsen neutral transport attenuation (chemistry-dependent, since different neutral species have different sticking/reaction probabilities per sidewall collision, Chapter 4, Section 3.3). This means the ARDE curve for a given reactor and feature geometry is not purely geometric — it depends on gas chemistry (Chapter 3), pressure (Chapter 7), and RF/pulsing strategy (Chapter 9) as well, and must be characterized (or modeled with chemistry-specific parameters) for each distinct process regime rather than assumed universal.

---

## Part 2: The Knudsen Transport Probability Model

### 2.1 Clausing's Transport Probability

The classical starting point for feature-scale neutral transport is Clausing's treatment of molecular flow through a cylindrical tube in the free-molecular (Knudsen) regime, which gives a transmission probability $K(AR)$ — the probability that a molecule entering the top of a cylindrical feature of aspect ratio $AR$ (length/diameter) successfully exits the bottom, accounting for the possibility of returning out the top after one or more sidewall collisions, rather than being lost to the sidewall along the way:

$$K(AR) \approx \frac{1}{1 + \frac{3}{8}AR} \quad (\text{for a non-reactive, perfectly reflecting tube, long-tube approximation})$$

This classical result assumes every sidewall collision is a specular or diffuse *reflection* with no loss — i.e., it models pure transport without any reaction/consumption at the sidewall. For channel hole etch, this must be modified to account for finite reaction/sticking probability at each sidewall collision (Chapter 4, Section 3.3), since a meaningful fraction of neutral radical and fluorine flux is in fact consumed (contributing to sidewall polymer formation or parasitic sidewall etching) at each collision rather than simply reflecting onward.

### 2.2 Modified Transport Probability With Sidewall Reaction Loss

Introducing a sidewall reaction/sticking probability $\gamma$ (probability of consumption per sidewall collision, $0 \le \gamma \le 1$) modifies the transport probability to decay more steeply with aspect ratio than the pure-reflection Clausing result:

$$K(AR, \gamma) \approx \frac{1}{1 + \frac{3}{8}AR \cdot \frac{\gamma}{1-\gamma/2}} \quad (\text{approximate form; exact solution requires numerical integration of the full integral transport equation for most } \gamma \text{ values})$$

**Qualitative behavior:** for small $\gamma$ (low sidewall reactivity, species that mostly reflect rather than stick/react), $K(AR,\gamma)$ approaches the pure Clausing result and falls off relatively gently with aspect ratio. For larger $\gamma$ (highly reactive species, consumed readily at each collision), $K(AR,\gamma)$ falls off much more steeply — a direct, quantitative explanation for why atomic fluorine (highly reactive, large effective $\gamma$) depletes with depth far faster than, for example, a less reactive dilution gas species (small $\gamma$) would under the same geometric conditions.

### 2.3 Worked Transport Probability Calculation

**Illustrative calculation at AR = 80:1** (representative of a single-tier 176-layer-class channel hole etch, Chapter 1, Section 5.2), comparing a highly reactive species ($\gamma = 0.3$, representative of a reasonably sticky CFx radical contributing to polymer formation) against a less reactive species ($\gamma = 0.05$, representative of a comparatively unreactive dilution or carrier gas constituent):

$$K(80, 0.3) \approx \frac{1}{1 + 0.375 \times 80 \times \frac{0.3}{0.85}} = \frac{1}{1 + 30 \times 0.353} = \frac{1}{1+10.6} \approx 0.086$$

$$K(80, 0.05) \approx \frac{1}{1 + 0.375 \times 80 \times \frac{0.05}{0.975}} = \frac{1}{1 + 30 \times 0.0513} = \frac{1}{1+1.54} \approx 0.394$$

This single worked comparison, at identical aspect ratio, shows the highly reactive species transmitting at only ~8.6% of its top-opening flux by the time it reaches the bottom of an 80:1 feature, while the less reactive species transmits at ~39.4% — nearly a 4.6x difference in transport efficiency driven entirely by sidewall reactivity, with geometry held fixed. This is the quantitative foundation for Chapter 3's chemistry-selection discussion: a chemistry's effective sidewall sticking probability, not just its gas-phase reactivity in isolation, is a first-order determinant of how well that chemistry sustains flux (and therefore etch rate) at extreme aspect ratio.

---

## Part 3: Ion Trajectory Attenuation

### 3.1 A Simplified Geometric Model

Chapter 4, Section 3.2 described ion flux depletion with depth as primarily a trajectory-filtering effect: ions with angular spread $\theta$ around vertical, if $\theta$ exceeds the critical angle $\theta_c(AR) = \arctan(1/(2 \cdot AR))$ at a given depth-to-radius ratio, strike the sidewall before reaching that depth and are removed from the population reaching the bottom (to a first approximation, assuming ions striking the sidewall are not usefully redirected toward the bottom, a reasonable approximation at the ion energies and sidewall interaction physics typical of this application, in contrast to the more forgiving neutral reflection assumption of Section 2.1).

For a Gaussian angular ion distribution with standard deviation $\sigma_\theta$ (a function of sheath physics and pressure, Chapter 7, Section 1.1), the fraction of ions reaching full depth at aspect ratio $AR$ is approximately:

$$f_{ion}(AR) \approx \text{erf}\left(\frac{\theta_c(AR)}{\sigma_\theta \sqrt{2}}\right)$$

**Illustrative comparison:** for $\sigma_\theta = 3°$ (representative of a well-designed, low-pressure ICP+bias system, Chapter 5), at $AR=20$, $\theta_c \approx \arctan(1/40) \approx 1.43°$, giving $f_{ion}(20) \approx \text{erf}(1.43/(3\sqrt{2})) \approx \text{erf}(0.337) \approx 0.365$ — already significant depletion at only 20:1. At $AR=80$, $\theta_c \approx \arctan(1/160) \approx 0.358°$, giving $f_{ion}(80) \approx \text{erf}(0.358/4.24) \approx \text{erf}(0.0844) \approx 0.0952$ — roughly 9.5% ion transmission, broadly comparable in order of magnitude to the reactive-neutral transport result of Section 2.3, though arising from an entirely different physical mechanism (angular geometry rather than collision-probability transport).

### 3.2 Why Ion and Neutral Attenuation Curves Diverge at Different Aspect Ratios

Comparing Section 2.3's neutral transport results and Section 3.1's ion trajectory results across a range of aspect ratios shows that the two attenuation mechanisms, while producing broadly similar-order-of-magnitude transmission fractions at the specific AR=80 point calculated above, do not fall off at identical rates as AR varies — ion trajectory attenuation (an error-function form, Section 3.1) and reactive neutral transport (a roughly $1/AR$ form at large $AR$, Section 2.2) have different functional shapes. This divergence is the quantitative origin of Chapter 4, Section 3.4's qualitative claim that the ion-to-neutral flux ratio realized at the feature bottom shifts with depth, and is the direct cause of the depth-dependent polymer balance shift (Chapter 3, Section 5.3; Chapter 4, Section 5.2) that pulsed bias strategies (Chapter 9, Part 3) are specifically designed to counteract.

---

## Part 4: Combining Mechanisms Into an Overall Etch Rate Model

### 4.1 A Combined Rate Expression

Using Chapter 4, Section 1.2's saturating rate framework, with ion and neutral flux now depth-dependent via Sections 2-3 of this chapter:

$$R_{etch}(AR, depth) \approx k \cdot \Gamma_{n,0} \cdot K(AR,\gamma) \cdot f\big(\Gamma_{i,0} \cdot f_{ion}(AR),\ E_i\big)$$

where $\Gamma_{n,0}$ and $\Gamma_{i,0}$ are the top-opening neutral and ion flux values set by chamber-level conditions (Chapters 6-7), and $K(AR,\gamma)$, $f_{ion}(AR)$ are the transport attenuation factors derived in Parts 2-3. This expression makes explicit that overall etch rate at depth depends multiplicatively on both the neutral transport attenuation and the (separately attenuated) ion flux's effect on the saturating ion-assisted rate function — neither attenuation mechanism alone fully determines the outcome; both must be tracked and combined.

### 4.2 Why the Combined Falloff Is Faster Than Either Mechanism Alone

Because both $K(AR,\gamma)$ and $f_{ion}(AR)$ decrease with increasing $AR$, and because the rate expression in Section 4.1 depends on both multiplicatively (through the neutral flux factor directly, and through the ion flux's effect on the saturating function $f$), the combined etch rate falls off with aspect ratio faster than either individual mechanism's attenuation curve considered in isolation. This compounding effect is the quantitative explanation for why channel hole etch rate at extreme aspect ratio (80:1-100:1+) can fall to a small fraction — often cited in process characterization work as low as 10-30% depending on specific chemistry and reactor conditions — of its low-AR reference rate, a reduction considerably more severe than a naive, single-mechanism estimate would predict.

### 4.3 The Etch-Stop Boundary in This Framework

Chapter 3, Section 5.3's etch-stop condition (net polymer accumulation, $d\delta_p/dt > 0$) can now be expressed within this chapter's quantitative framework: etch stop occurs at the aspect ratio where ion-assisted polymer removal rate (proportional to $f_{ion}(AR)$) falls below neutral-driven polymer deposition rate (proportional to $K(AR,\gamma_{dep})$ for the polymer-forming species specifically) by a margin that cannot be compensated by any available increase in bias power or source power within the process window characterized in Chapter 7. Because $f_{ion}(AR)$ generally falls faster than $K(AR,\gamma_{dep})$ at large $AR$ (Section 3.2's divergence), every channel hole etch process has, in principle, some maximum sustainable aspect ratio beyond which no combination of chamber-level settings within Chapter 7's phase space can prevent eventual etch stop — a hard physical ceiling, not merely a recipe tuning challenge, that motivates the layer-count-driven adoption of string stacking discussed in Chapter 1, Section 1.3.

---

## Part 5: Compensation Strategies and Their Quantitative Limits

### 5.1 Depth-Ramped Power (Chapter 7, Section 3.2 Revisited)

Increasing source and/or bias power as etch depth increases directly increases $\Gamma_{n,0}$ and $\Gamma_{i,0}$ in Section 4.1's expression, partially compensating for the multiplicatively worsening attenuation factors. This compensation has a hard limit, however: increasing bias power indefinitely eventually exceeds the mask erosion and selectivity boundaries established in Chapter 7, Section 2.1, meaning depth-ramping can extend the practically achievable aspect ratio but cannot evade the fundamental Section 4.2 scaling entirely.

### 5.2 Chemistry Selection for Reduced Sidewall Reactivity

Section 2.3's worked example showed that reducing effective sidewall sticking probability $\gamma$ for key reactive species substantially improves transport probability at fixed aspect ratio. This is the quantitative justification for Chapter 3's chemistry-selection discussion: choosing a fluorocarbon chemistry and pressure regime that minimizes unwanted sidewall consumption of the specific neutral species responsible for sustaining bottom-of-feature etch rate (while still maintaining adequate sidewall polymer for profile protection, Chapter 4, Section 2.3 — a tension, not a free lever) directly improves the achievable aspect ratio before Section 4.3's etch-stop ceiling is reached.

### 5.3 Pulsing-Based Compensation (Chapter 9 Revisited)

Chapter 9's pulsing strategies address Section 3.2's divergent ion/neutral attenuation specifically by time-sequencing through conditions that favor ion-assisted clearing (high-bias intervals) and sidewall-protective polymer accumulation (low-bias intervals) separately, rather than relying on a single, static balance point that this chapter's model shows cannot simultaneously satisfy both requirements at extreme aspect ratio. Pulsing does not change the fundamental transport physics derived in Parts 2-3 of this chapter, but it allows the process to extract more usable process window from that physics than static operation could achieve, by avoiding the forced simultaneous compromise a continuous-wave process requires.

### 5.4 Why All Compensation Strategies Ultimately Face the Same Ceiling

Every compensation strategy addressed in this section works by improving the practically achievable margin against Section 4.3's etch-stop boundary, not by eliminating the boundary itself, which is set by the fundamental transport physics derived in Parts 2-3. This is the quantitative, first-principles explanation for why the industry has, as layer counts climbed, adopted string stacking (Chapter 1, Section 1.3) as a structural solution — capping per-step aspect ratio directly — rather than relying indefinitely on chemistry, power, and pulsing compensation alone to chase an ever-increasing single-tier aspect ratio target.

---

## Part 6: ARDE Across the Generational Roadmap

### 6.1 Summary Table Across Representative Aspect Ratios

Combining the illustrative calculations of Sections 2.3 and 3.1 across the generational aspect ratio progression established in Chapter 1, Section 5.2:

| Generation (layers, single-tier equivalent) | Aspect Ratio | Illustrative $K(AR, \gamma=0.3)$ | Illustrative $f_{ion}(AR)$, $\sigma_\theta=3°$ | Combined Relative Rate (normalized to AR=12) |
|---|---|---|---|---|
| 32 | ~12:1 | ~0.69 | ~0.73 | 1.00 (reference) |
| 64 | ~25:1 | ~0.47 | ~0.42 | ~0.39 |
| 96 | ~39:1 | ~0.34 | ~0.21 | ~0.14 |
| 128 (single-tier) | ~55:1 | ~0.25 | ~0.106 | ~0.052 |
| 176 (single-tier) | ~81:1 | ~0.18 | ~0.088 | ~0.030 |

(Figures are derived from this chapter's simplified illustrative models at fixed $\gamma$ and $\sigma_\theta$ values for comparative purposes; actual production ARDE curves depend on chemistry- and reactor-specific parameters characterized empirically, Chapter 7, and are expected to differ from this table's simplified, fixed-parameter illustration in detail while following the same qualitative, steeply compounding trend.)

The rightmost column makes Section 4.2's "faster than either mechanism alone" claim starkly concrete: relative etch rate at illustrative 176-layer single-tier aspect ratio falls to roughly 3% of its 32-layer-generation value under this simplified fixed-parameter model — a reduction that, if left entirely uncompensated by any of Section 5's strategies, would require roughly 33 times longer etch time to clear the same stack depth, an increase in process time that would be entirely incompatible with production throughput economics (Chapter 1, Section 6.1). This table is the quantitative heart of why string stacking, chemistry refinement, and pulsing compensation (Section 5) are not optional process refinements but necessary, continuously advancing countermeasures against a trend this chapter's physics shows to be fundamentally unforgiving.

### 6.2 Worked Throughput Impact Without Compensation

**Illustrative calculation:** suppose a 32-layer-generation channel hole etch step completes in 20 minutes at its reference aspect ratio. Applying the uncompensated relative rate ratios from Section 6.1's table (treating etch time as inversely proportional to relative rate, a simplification that ignores the mask-open and overetch steps' comparatively AR-insensitive time contribution, Chapter 2, Section 5.2, but is reasonable for illustrating the bulk-etch-dominated trend):

$$t_{96L} \approx 20\ \text{min} \times \frac{1.00}{0.14} \approx 143\ \text{min} \qquad t_{176L} \approx 20\ \text{min} \times \frac{1.00}{0.030} \approx 667\ \text{min} \ (\approx 11.1\ \text{hours})$$

An uncompensated 11-hour single-wafer bulk etch step would be entirely unworkable at production volume. This is precisely the gap that Section 5's compensation strategies (depth-ramped power, chemistry selection, pulsing) and Chapter 1, Section 1.3's string-stacking architecture must collectively close, and real production 176-layer-class channel hole etch processes do, in fact, complete in a commercially viable time frame (generally cited in industry literature as on the order of tens of minutes to a small number of hours per wafer, depending on specific stack and tool) — a direct empirical demonstration that the combination of compensation strategies developed in Section 5, applied aggressively and in combination, recovers the great majority of this chapter's uncompensated throughput penalty, even though Section 5.4 shows no combination of these strategies can fully eliminate the underlying transport-driven rate loss at its physical root.

---

## Summary and Forward Look

Aspect ratio dependent etching at the extreme aspect ratios channel hole etch requires (50:1 to 100:1+) arises from two distinct, quantitatively derivable transport mechanisms — Knudsen-regime neutral transport with finite sidewall reaction probability, and ion trajectory angular filtering — which attenuate flux at different, non-identical rates as aspect ratio increases, compounding multiplicatively in their effect on overall etch rate. This compounding explains both the severity of etch rate falloff at extreme aspect ratio and the existence of a fundamental etch-stop ceiling that chemistry, power, and pulsing compensation strategies can push outward but cannot eliminate, motivating the industry's structural adoption of string stacking as aspect ratio demands continue to climb with layer count.

The next chapter builds directly on this quantitative transport foundation to address the profile defects — bowing, twisting, and necking — that arise when this chapter's attenuation mechanisms are not merely severe but also non-uniform across a feature's cross-section or population of features, including the charging effects that complicate the ion trajectory picture developed in Part 3 of this chapter.
