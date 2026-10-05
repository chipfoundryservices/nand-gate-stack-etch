# Chapter 14: Word Line Replacement (Gate-Last) Etch & Metal Fill Prep

## Executive Summary

This chapter completes Part III by addressing the final major etch-adjacent step in the 3D NAND process flow: converting the sacrificial oxide/nitride stack, now fully etched with channel holes (Chapters 10-12) and staircase contacts (Chapter 13), into the final metal-gate word line structure. This proceeds through slit etch (cutting access trenches between blocks), selective sacrificial nitride removal through those slits, and metal fill — performed on a structure that, once the nitride is removed, has lost essentially all of its mechanical support except for the array of channel hole pillars (and, where present, staircase-region dummy pillars) running through it. We develop the slit etch's own aspect-ratio and selectivity requirements, the chemistry and kinetics of selective nitride removal, and the structural mechanics of the unsupported interval between removal and fill — a mechanically distinct and, by most industry accounts, the single highest structural-risk interval in the entire 3D NAND process flow.

---

## Part 1: Slit Etch

### 1.1 Purpose and Geometry

The slit is a long, trench-shaped (rather than cylindrical) opening etched vertically through the full stack between adjacent memory blocks (Chapter 1, Section 3's block definition), serving as the access path through which sacrificial nitride removal chemistry (Part 2) and subsequent metal fill (Part 3) are delivered to every word line layer simultaneously, from the block's edge rather than from the top of the stack as the channel hole etch (Chapters 10-12) does.

### 1.2 Why Slit Etch Shares Much of Channel Hole Etch's Physics, But Not All of It

Because the slit, like the channel hole, must be etched through the same full oxide/nitride stack to full stack depth, it faces aspect-ratio-dependent etch rate falloff (Chapter 10) and profile control challenges (Chapter 11) that are mechanistically similar to the channel hole etch's. However, the slit's trench geometry (long and narrow in cross-section, rather than circular) means the Knudsen transport and ion trajectory models developed in Chapter 10 for cylindrical holes require geometric adaptation — a trench's transport probability and ion trajectory filtering behave somewhat differently than a cylindrical hole's at equivalent nominal aspect ratio, generally (though not universally across all trench width/depth combinations) exhibiting somewhat more favorable transport along the trench's long axis than a cylindrical hole of equivalent minimum-dimension aspect ratio would, since the trench geometry provides an additional transport pathway not available to a fully enclosed cylindrical hole.

### 1.3 Why Slit Etch Selectivity Requirements Differ From Channel Hole Etch

Unlike the channel hole's near-balanced oxide/nitride selectivity target (Chapter 12, Section 2.3), the slit etch's primary objective is simply to clear a straight, well-controlled trench through the full stack to the bottom stop layer — it does not need to preserve a smooth, uniform sidewall for subsequent conformal deposition the way the channel hole does, since the slit's final function (nitride removal access path and eventual isolation structure fill, Section 1.1) does not require the same sidewall quality standard as the channel hole's ONO deposition target (Chapter 2, Section 4.1). This relaxed sidewall-quality requirement allows some slit etch recipes to prioritize etch rate and stop-layer selectivity (Chapter 12, Part 4's framework, applied here) somewhat more aggressively than the channel hole bulk etch's more conservative, profile-protective balance.

---

## Part 2: Selective Sacrificial Nitride Removal

### 2.1 Wet Chemistry: Hot Phosphoric Acid

The dominant industry approach for removing sacrificial nitride through the slit access path (Chapter 2, Section 1.3) uses hot phosphoric acid (H3PO4, typically around 160°C), which etches silicon nitride at a rate far exceeding its etch rate of silicon dioxide — selectivity ratios exceeding 100:1 are commonly cited in industry literature, reflecting the strongly differential chemical attack of hot phosphoric acid on Si-N versus Si-O bonding, a far larger selectivity contrast than the plasma etch selectivity discussed in Chapter 12 for the channel hole and slit vertical etch steps.

### 2.2 Why This Removal Is a Wet, Not Dry/Plasma, Process

Unlike every etch process discussed in Chapters 3-13 of this book, sacrificial nitride removal is performed as a wet chemical process rather than a plasma etch, for several specific reasons: the removal must proceed laterally, uniformly, and completely through narrow horizontal cavities (the spaces vacated as nitride is removed layer by layer, extending potentially hundreds of microns laterally from the slit into the array) where plasma or ion-based processes (requiring line-of-sight or near-line-of-sight access, Chapter 4) simply cannot reach; wet chemistry, by contrast, can achieve this lateral, non-line-of-sight removal via liquid-phase diffusion and reaction through the already-open horizontal cavity network as nitride removal progresses inward from the slit.

### 2.3 Lateral Etch Rate and Access Length Limitations

Because the hot phosphoric acid must diffuse laterally through an increasingly narrow (as more nitride is removed and oxide layers above/below begin to approach their final, unsupported state, Part 4) horizontal cavity to reach nitride still remaining deep within the array, lateral etch rate progressively slows with increasing lateral distance from the slit — directly analogous in general character (though governed by liquid-phase diffusion/reaction kinetics rather than Chapter 10's Knudsen gas transport) to the depth-dependent etch rate falloff that has been a recurring theme throughout this book. This lateral access limitation is a primary reason block width (the lateral distance from slit to the array's center, determining the maximum lateral nitride removal distance required) cannot be increased without bound even though wider blocks would otherwise be architecturally favorable for area efficiency — nitride removal process time and completeness place a practical upper limit on block width that device architects must respect.

### 2.4 Verifying Complete Removal

Because incomplete nitride removal (residual nitride remaining at the block's interior, farthest from the slit) would prevent proper metal fill at those locations in Part 3, process qualification must verify complete removal across the full block width, typically through a combination of calculated/characterized removal-rate-versus-distance models (extending Section 2.3's framework quantitatively) and direct cross-sectional inspection of qualification wafers, since incomplete removal at the block's interior would not necessarily be detectable from slit-adjacent inspection alone.

---

## Part 3: Metal Fill

### 3.1 Fill Sequence

Following complete nitride removal (Section 2.4), each now-empty horizontal cavity is filled with the final word line metal stack, typically a thin TiN barrier/adhesion layer (deposited by ALD for the same conformality reasons discussed for the channel hole's ONO stack, Chapter 2, Section 4.2) followed by tungsten (W) fill, delivered through the same slit access path used for nitride removal.

### 3.2 Why Tungsten, and Why This Fill Faces Its Own Transport Challenge

Tungsten is favored for word line fill due to its combination of acceptable resistivity, strong chemical and thermal stability, and mature, well-characterized CVD fill processes (typically WF6-based chemistry). However, filling the same long, narrow lateral cavities that challenged nitride removal (Section 2.3) with void-free tungsten faces an analogous lateral transport problem: WF6 precursor and reaction byproducts must transport laterally through an increasingly constrained path as fill progresses inward from the slit, and incomplete or non-conformal fill can leave voids, particularly near the cavity's interior, lateral extent (the same block-width-limited region discussed in Section 2.3) — a close structural analog of the channel hole's own fill-void risk discussed in Chapter 2, Section 4.3, but occurring in the lateral rather than vertical direction.

### 3.3 Resistance Implications of Fill Quality

Because word line resistance directly affects RC delay in word line signal propagation (a device performance consideration beyond this book's etch-centered scope, but a direct downstream consequence of fill quality), incomplete or void-containing tungsten fill, particularly at the lateral extremity of a block farthest from the slit, can produce measurably higher word line resistance at those locations than at slit-adjacent locations — a performance non-uniformity across a single block's physical extent that device and process teams must jointly manage through the combination of block width limitation (Section 2.3) and fill process optimization.

---

## Part 4: Mechanical Stability During the Unsupported Interval

### 4.1 Why This Interval Is Uniquely Vulnerable

Chapter 2, Section 5.2 anticipated this chapter's central structural concern: once sacrificial nitride is fully removed (Section 2.1-2.4) but before metal fill (Section 3.1-3.2) is complete, the stack's oxide layers are mechanically supported *only* by the array of channel hole pillars (and any staircase-region dummy pillars included specifically for this purpose) passing vertically through them — the nitride, which previously provided continuous horizontal mechanical support across the full lateral extent between pillars, is entirely absent during this interval. This represents the point of minimum structural integrity across the entire 3D NAND process flow, by a substantial margin relative to any other single process step addressed in this book.

### 4.2 Failure Modes During the Unsupported Interval

Several distinct failure modes are specifically associated with this interval:

**Oxide layer sagging or collapse** between widely-spaced pillars, if pillar density (set by channel hole pitch, Chapter 1, Section 5.1, an electrically and lithographically driven parameter not generally adjustable purely for mechanical margin reasons) is insufficient to support the unsupported oxide layers' own weight and any residual process-induced stress (Chapter 2, Section 5.2) across the full process duration of this interval.

**Block tilting or shifting**, particularly if residual net stack stress (Chapter 2, Section 5.2's stress evolution discussion) is asymmetric across a block's width, producing a net lateral or rotational force on the now-poorly-supported stack that the remaining pillar array cannot fully resist.

**Wafer-level warpage interaction**, where the loss of block-level mechanical rigidity during this interval can interact with and amplify any residual wafer-level bow (Chapter 2, Section 5.1) that remains from earlier process stages, since the stack's own internal rigidity (now reduced, per this section) previously contributed to resisting wafer-level deformation to some degree.

### 4.3 Mitigation Strategies

Production process flows mitigate these risks through several complementary approaches: minimizing the time duration of the unsupported interval itself (optimizing nitride removal and metal fill process speed specifically to shorten this window, sometimes at some cost to the removal/fill quality optimizations discussed in Sections 2 and 3, requiring a deliberate tradeoff); including dedicated, electrically inactive "dummy" support pillars at strategic locations beyond the minimum required by the active channel hole array itself, specifically to provide additional mechanical support during this interval without serving any electrical function in the finished device; and careful control of residual stack stress entering this interval (Chapter 2, Section 5.2) to minimize the asymmetric forces that Section 4.2's block-tilting failure mode depends on.

### 4.4 Why This Interval Receives Disproportionate Process Engineering Attention

Given Section 4.1's characterization of this interval as the point of minimum structural integrity in the entire process flow, and given that a structural failure during this interval (unlike many of the dimensional or electrical defects discussed in earlier chapters) can produce catastrophic, often unrecoverable damage affecting an entire block or larger region of the wafer rather than a single string or contact, process engineering investment in nitride removal and metal fill process speed, dummy pillar placement optimization, and stress management entering this interval is disproportionately high relative to the comparatively modest total process time this interval represents within the full 3D NAND flow — a direct reflection of the asymmetric cost of failure during this specific window relative to most other individual process steps this book addresses.

---

## Part 5: A Worked Lateral Removal Time Estimate

### 5.1 Simplified Diffusion-Limited Removal Model

Section 2.3's lateral etch rate falloff can be approximated, for illustrative purposes, using a simplified diffusion-limited model in which lateral nitride removal distance $x(t)$ grows with the square root of time, characteristic of a diffusion-controlled reactive front (a reasonable first approximation when fresh reactant must continuously diffuse inward through an already-cleared, increasingly long cavity to reach the reaction front):

$$x(t) \approx \sqrt{2 D_{eff} \cdot t}$$

where $D_{eff}$ is an effective diffusion coefficient for the phosphoric acid reactant species through the narrow, nitride-cavity geometry (a lumped parameter capturing both true molecular diffusion and the geometric constriction effects of the narrow cavity, empirically characterized rather than predicted from first principles alone for any specific stack design).

### 5.2 Illustrative Calculation

**Illustrative time to clear a representative block half-width of 3 µm**, given an illustrative $D_{eff} \approx 5\times10^{-10}\ \text{cm}^2/\text{s}$ (a representative order-of-magnitude value for a constrained, narrow-cavity liquid diffusion process; actual values are process- and cavity-geometry-specific and determined empirically):

$$t = \frac{x^2}{2D_{eff}} = \frac{(3\times10^{-4}\ \text{cm})^2}{2\times5\times10^{-10}\ \text{cm}^2/\text{s}} = \frac{9\times10^{-8}}{1\times10^{-9}} = 90\ \text{s}$$

**Doubling block half-width to 6 µm** (illustrating Section 2.3's nonlinear time penalty for wider blocks):

$$t = \frac{(6\times10^{-4})^2}{1\times10^{-9}} = \frac{3.6\times10^{-7}}{1\times10^{-9}} = 360\ \text{s}$$

Doubling the lateral removal distance quadruples the required removal time under this diffusion-limited model (consistent with the $x \propto \sqrt{t}$, or equivalently $t \propto x^2$, scaling), a substantially less forgiving relationship than the linear scaling one might naively assume, and the direct quantitative justification for Section 2.3's claim that block width cannot be increased without bound: a modest architectural desire to widen blocks for area efficiency carries a disproportionately large nitride removal (and, by the related argument in Section 3.2, metal fill) time penalty, directly trading off against overall process throughput in a way that device architects must weigh against the area-efficiency benefit of wider blocks.

### 5.3 Why Overetch Margin for Complete Removal Compounds This Penalty Further

Just as the channel hole and slit vertical etches require overetch margin to ensure full clearing across all locations despite process variation (Chapter 12, Section 4.1), lateral nitride removal requires a similar margin — processing somewhat longer than the nominal calculated clearing time from Section 5.2 to ensure complete removal even at the furthest, slowest-clearing interior locations across all blocks on the wafer and across lot-to-lot process variation. Given Section 5.2's quadratic time-versus-distance relationship, this overetch margin, applied at the already-long interior clearing time rather than at a shorter edge-clearing time, represents a proportionally larger absolute time addition than the same fractional margin would represent for a less distance-sensitive process — a further, compounding reason total nitride removal process time is carefully optimized and characterized rather than treated as a straightforward, linearly-scaling process step.

---

## Part 6: Comparative Summary of the Three Replacement-Sequence Steps

| Step | Process Type | Primary Physics | Primary Risk | Relevant Chapter Linkage |
|---|---|---|---|---|
| Slit etch | Dry plasma etch | Trench-geometry transport, adapted from Chapter 10's cylindrical model | Incomplete clearing, profile defects analogous to Chapter 11 | Chapters 10-11 (adapted geometry) |
| Sacrificial nitride removal | Wet chemical (hot H3PO4) | Lateral liquid-phase diffusion/reaction, Section 5's quadratic time-distance scaling | Incomplete interior removal (Section 2.4); mechanical vulnerability onset (Part 4) | Chapter 2, Section 1.3 (sacrificial stack definition) |
| Metal fill (TiN/W) | ALD + CVD deposition | Lateral precursor transport through narrow cavity, analogous challenge to Section 2's removal problem | Voiding at lateral extremity, elevated word line resistance (Section 3.3) | Chapter 2, Section 4.2 (ALD conformality rationale) |

This table summarizes why the replacement sequence, despite being conceptually a single "replace nitride with metal" operation at the architectural level (Chapter 1, Section 2.3), in practice comprises three mechanistically distinct processes, each with its own characteristic physics, risk profile, and process control requirements, unified primarily by their shared dependence on the same slit access geometry and their shared exposure to the Part 4 structural vulnerability window.

---

## Summary and Forward Look

Word line replacement converts the sacrificial oxide/nitride stack into the final metal-gate structure through slit etch (sharing much of the channel hole etch's transport physics but with relaxed sidewall-quality and distinct selectivity requirements), highly selective wet-chemical sacrificial nitride removal (a liquid-phase, non-line-of-sight process fundamentally different from every plasma etch process discussed elsewhere in this book), and tungsten metal fill (facing its own lateral transport and void-formation challenge analogous to, but distinct from, the channel hole's vertical fill problem). The interval between nitride removal and completed metal fill represents the point of minimum mechanical integrity across the entire 3D NAND process flow, mitigated through interval-duration minimization, dedicated support pillar placement, and careful stress management rather than eliminated outright.

With Part III's full process physics and control framework now complete — etch rate (Chapter 10), profile (Chapter 11), selectivity (Chapter 12), multi-step compounding error (Chapter 13), and structural/replacement considerations (this chapter) — Part IV turns to how all of these individually-characterized phenomena are held in coordinated statistical control across a full production fab running multiple tools, multiple process steps, and continuous high-volume output simultaneously.
