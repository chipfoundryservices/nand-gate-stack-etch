# Chapter 12: Selectivity Engineering — Oxide/Nitride/Poly in Stacked Films

## Executive Summary

Chapters 10 and 11 developed how etch rate and profile evolve with depth in an idealized single-material or uniform-stack sense. This chapter addresses the question those chapters deferred: because the channel hole etch cuts through dozens to hundreds of alternating, chemically distinct films (Chapter 2), what does "selectivity" even mean in this context, and how is it engineered and controlled? We develop the averaged-selectivity framework introduced conceptually in Chapter 4, Section 4.2, extend it quantitatively, address the distinct selectivity requirements of the oxide/polysilicon (OPOP) sacrificial variant, and treat the bottom-of-stack stop-layer selectivity problem that determines when and how the etch must terminate. This chapter closes the loop between Chapter 2's materials discussion and Chapters 10-11's transport/profile physics by showing how selectivity requirements constrain the process window these earlier chapters established.

---

## Part 1: What Selectivity Means for an Alternating Stack

### 1.1 Instantaneous Versus Averaged Selectivity, Formally Defined

Chapter 4, Section 4.2 introduced the distinction between instantaneous selectivity (the oxide:nitride etch rate ratio at a single moment, within a single film) and averaged selectivity (the practically relevant metric for a multi-layer etch). Formally:

$$S_{inst}(t) = \frac{R_{ox}(t)}{R_{nit}(t)} \quad \text{(defined only while etching within a single film type at time } t\text{)}$$

$$S_{avg} = \frac{\sum_i d_{ox,i}}{\sum_j d_{nit,j}} \bigg/ \frac{t_{ox,total}}{t_{nit,total}} = \frac{\bar{R}_{ox}}{\bar{R}_{nit}}$$

where $\bar{R}_{ox}$ and $\bar{R}_{nit}$ are the time-averaged etch rates across all oxide and all nitride layers respectively, encountered over the full depth of the etch. $S_{avg}$ is the metric that actually determines whether, after a full channel hole etch, all oxide and all nitride layers have been removed to a consistent, acceptable final CD — not $S_{inst}$ at any single point.

### 1.2 Why Averaged Selectivity Can Differ Substantially From Any Single Instantaneous Measurement

Because Chapter 10 established that both $R_{ox}$ and $R_{nit}$ individually decline with depth (through the same transport attenuation mechanisms, applied to whichever material the etch front currently occupies), and because Chapter 2's materials discussion established that oxide and nitride layers do not necessarily have identical, depth-independent intrinsic reactivity (density/stoichiometry drift, Chapter 2, Section 1.2), $S_{avg}$ is not simply equal to $S_{inst}$ measured at the top of the stack, extrapolated unchanged to all depths. A process characterized only via a short, low-depth test etch (common in early process development, before full-depth test structures are available) can show a misleadingly favorable or unfavorable $S_{inst}$ relative to the true $S_{avg}$ that will actually be realized across the full production stack depth — a direct, practical reason full-depth selectivity characterization (even if costly and slow during development) is treated as a required, non-skippable qualification step rather than an optional refinement.

---

## Part 2: Why Nitride Intrinsically Etches Faster, and How That Default Is Overridden

### 2.1 The Intrinsic Reactivity Baseline

Chapter 4, Section 2.2 established that Si-N bonds are, on average, somewhat weaker than Si-O bonds, meaning nitride's intrinsic (undecorated by deliberate selectivity engineering) etch rate in a generic fluorine-rich chemistry tends to exceed oxide's. Left entirely uncorrected, a channel hole etch using an undifferentiated, maximally aggressive fluorine chemistry would etch nitride layers measurably faster than oxide layers, producing a stepped, non-uniform sidewall profile at each oxide/nitride transition (locally wider at nitride layers, narrower at oxide layers) rather than the smooth, consistent sidewall Chapter 1's acceptance criteria require.

### 2.2 Polymer-Mediated Selectivity Reduction

The primary engineering lever for suppressing this intrinsic nitride-fast default is the same polymer-forming chemistry developed in Chapter 3: because nitride's higher intrinsic reactivity under polymer-limited (fluorine-rich, carbon-poor) conditions is specifically a chemical-etch-rate effect, increasing the carbon-rich, polymer-forming character of the chemistry (Chapter 3, Section 2.1) suppresses both oxide and nitride etch rate to some degree, but — because the suppression acts on the chemical etch pathway nitride relies on more heavily for its reactivity advantage — it suppresses nitride's rate proportionally more, narrowing the gap toward a more balanced $S_{avg}$ closer to 1.0 (comparable oxide and nitride removal rate), or, if desired, deliberately engineering it toward the opposite imbalance (oxide etching faster than nitride) through further chemistry tuning.

### 2.3 Why a Fully Balanced $S_{avg} \approx 1$ Is the Typical Bulk-Etch Target

For the bulk channel hole etch step specifically, process targets generally aim for $S_{avg}$ reasonably close to 1.0 — neither oxide nor nitride etching dramatically faster than the other — because a strongly imbalanced selectivity during the bulk etch would produce the stepped sidewall profile described in Section 2.1, directly degrading the smooth-sidewall requirement that downstream ONO deposition (Chapter 2, Section 4.1) depends on. This is a notable contrast to many other etch applications (including the stop-layer problem addressed in Part 4 below) where high, deliberately engineered selectivity is the explicit goal — in the bulk channel hole etch, by contrast, deliberately *reduced* selectivity differential (a near-1:1 removal rate ratio) is usually the actual target.

---

## Part 3: The OPOP Variant — Oxide/Polysilicon Selectivity

### 3.1 Why Oxide/Polysilicon Selectivity Behaves Differently

For the OPOP sacrificial stack variant (Chapter 2, Section 1.3), the relevant selectivity pair is oxide (dielectric) versus polysilicon (semiconductor), a materially larger intrinsic reactivity contrast than oxide/nitride, since polysilicon's covalent Si-Si bonding and semiconductor electronic structure respond to fluorine chemistry through a somewhat different mechanism than either oxide's Si-O or nitride's Si-N bonding (though still ultimately forming the same general volatile SiF4 byproduct, Chapter 3, Section 1.1).

### 3.2 Consequence for OPOP Recipe Design

Because oxide/polysilicon intrinsic selectivity contrast tends to be larger than oxide/nitride's, achieving the same near-1:1 averaged selectivity target described in Section 2.3 for an OPOP stack generally requires correspondingly more aggressive selectivity-suppressing chemistry (further toward the carbon-rich, polymer-forming end of Chapter 3's chemistry spectrum) than an equivalent oxide/nitride ON stack would need, all else equal — a direct, practical reason OPOP and ON stacks are not simply interchangeable from a chemistry-recipe perspective even though both nominally solve the same sacrificial-stack integration problem (Chapter 2, Section 1.3).

### 3.3 A Secondary Consideration: Semiconducting Sidewall Charging Interaction

Because polysilicon, unlike oxide or nitride, is semiconducting rather than a pure dielectric, OPOP stacks introduce an additional interaction with the charging mechanism developed in Chapter 11, Part 3: a semiconducting sacrificial layer provides some limited charge mobility/dissipation pathway along its own exposed sidewall surface during etch, distinct from the fully insulating behavior of a dielectric sidewall. This can, in principle, modestly alter the charging accumulation and dissipation balance described in Chapter 11, Section 3.1-3.2 relative to an all-dielectric ON stack, though the net practical effect depends on specific polysilicon doping, grain structure, and process conditions, and is not uniformly characterized as either a net benefit or detriment across the industry's limited public literature on this comparatively less common integration variant.

---

## Part 4: Bottom-of-Stack Stop-Layer Selectivity

### 4.1 Why the Bottom Interface Requires High, Not Balanced, Selectivity

Unlike the bulk etch's near-1:1 target (Section 2.3), the final overetch/breakthrough step, addressing the bottom-of-stack interface where the channel hole must clear through to the underlying source contact layer (Chapter 2, Section 5.1) without excessive damage, requires deliberately high selectivity of the etch toward the sacrificial oxide/nitride stack *relative to* the stop-layer material, so that normal across-wafer and lot-to-lot overetch margin (needed to ensure full clearing at every channel hole across the wafer, Chapter 1, Section 4.3) does not simultaneously erode or damage the stop layer excessively at locations that cleared earliest.

### 4.2 Chemistry Transition for the Breakthrough Step

This high-selectivity requirement is the direct motivation for the distinct breakthrough/overetch recipe step introduced conceptually in Chapter 3, Section 4.2: a chemistry blend and power condition specifically tuned to maximize etch rate contrast between the final sacrificial layer being cleared and the stop-layer material beneath it, generally sacrificing some of the bulk-etch's profile-optimized character (since profile control concerns are largely resolved by this point in the etch, Chapter 3, Section 4.2) in favor of this selectivity-maximizing objective.

### 4.3 Endpoint Detection as the Practical Enabler of Stop-Layer Protection

Even with deliberately engineered high stop-layer selectivity, some finite overetch time is generally still required to ensure full clearing across all channel holes (given the across-wafer and lot-to-lot variation addressed throughout Chapters 6-10), and this overetch time must be bounded as tightly as possible to minimize cumulative stop-layer damage. Endpoint detection (developed fully in Appendix F) — real-time monitoring of optical emission or other plasma signals that change character when the etch front reaches and begins exposing the stop-layer material across a statistically significant fraction of the wafer's channel holes — is the practical tool that allows the overetch step's duration to be set dynamically, per-wafer, rather than via a fixed, conservatively long worst-case overetch time that would otherwise be required to guarantee full clearing without real-time feedback.

---

## Part 5: Selectivity Interactions With Depth-Dependent Transport

### 5.1 Why Selectivity Itself Is Not Depth-Independent

Chapter 10's transport attenuation mechanisms (ion trajectory narrowing, Knudsen neutral transport) act on both oxide and nitride etch rate simultaneously but, in general, not with perfectly identical magnitude, since the specific chemical reaction pathways and sidewall sticking probabilities ($\gamma$ in Chapter 10, Section 2.2's notation) can differ somewhat between oxide and nitride surfaces even when both are exposed to the same incoming flux. This means $S_{avg}$, as experienced over the full depth of an extreme-AR channel hole etch, can itself drift somewhat with depth — a subtlety beyond the simpler, depth-independent treatment Parts 1-2 of this chapter present for clarity, and one that requires full-depth characterization (Section 1.2) to properly capture rather than being predictable from shallow-feature selectivity measurements alone.

### 5.2 Practical Implication for Recipe Ramping

Because of this depth-dependent selectivity drift, the depth-ramped power and chemistry compensation strategies introduced in Chapter 7, Section 3.2 and Chapter 10, Section 5.1 must be designed jointly considering both etch rate (the primary concern in those earlier chapters' framing) and selectivity (this chapter's concern) simultaneously — a ramping schedule optimized purely for sustaining adequate bulk etch rate at depth, without regard to its selectivity consequence, risks introducing the stepped-sidewall profile defect described in Section 2.1 specifically at the greatest depths, where margin for correction is most limited and where Chapter 11's profile and charging concerns are already most acute.

---

## Part 6: A Worked Averaged-Selectivity Calculation

### 6.1 Setting Up the Calculation

Suppose process characterization on shallow (low-AR) test structures shows oxide etch rate $R_{ox,0} = 120\ nm/min$ and nitride etch rate $R_{nit,0} = 140\ nm/min$ near the top of the stack ($S_{inst,top} \approx 0.857$, nitride etching modestly faster, consistent with Section 2.1's intrinsic baseline before full chemistry-based correction). Suppose further that Chapter 10's transport attenuation, applied separately to each material's effective sidewall sticking probability $\gamma$ (oxide $\gamma_{ox}=0.25$, nitride $\gamma_{nit}=0.32$, reflecting a modest but real difference in effective neutral consumption probability), produces different relative attenuation by the bottom of a 128-layer (~55:1 AR) stack.

### 6.2 Applying Chapter 10's Transport Model

Using Chapter 10, Section 2.2's modified transport probability form at $AR=55$:

$$K(55, 0.25) \approx \frac{1}{1+0.375\times55\times\frac{0.25}{0.875}} = \frac{1}{1+20.6\times0.286}=\frac{1}{1+5.89}\approx0.145$$

$$K(55, 0.32) \approx \frac{1}{1+0.375\times55\times\frac{0.32}{0.84}} = \frac{1}{1+20.6\times0.381}=\frac{1}{1+7.85}\approx0.113$$

Applying these attenuation factors to the top-opening rates (treating neutral transport as the dominant attenuation mechanism for this illustrative selectivity comparison, holding ion-related attenuation, Chapter 10, Part 3, as approximately equal between the two materials for simplicity):

$$R_{ox}(55{:}1) \approx 120 \times 0.145 \approx 17.4\ nm/min \qquad R_{nit}(55{:}1) \approx 140 \times 0.113 \approx 15.8\ nm/min$$

$$S_{avg}(\text{at full depth}) \approx \frac{17.4}{15.8} \approx 1.10$$

### 6.3 Interpreting the Result

Despite nitride etching modestly *faster* than oxide at the shallow-feature reference condition ($S_{inst,top} \approx 0.857$), the full-depth averaged selectivity has shifted to oxide etching modestly *faster* than nitride ($S_{avg} \approx 1.10$), purely as a consequence of nitride's somewhat higher effective sidewall sticking probability producing somewhat steeper transport attenuation with depth. This qualitative reversal — not merely a magnitude change, but a flip in which material etches faster — is precisely the kind of outcome Section 1.2 warned could not be predicted from shallow-feature characterization alone, and underscores why full-depth selectivity qualification (Section 1.2) is treated as a mandatory, not optional, step in channel hole process development: a process team relying solely on the shallow-feature $S_{inst,top}=0.857$ measurement would reasonably conclude the chemistry needs further adjustment to slow nitride down, when in fact, at full production depth, the opposite correction may be required.

---

## Part 7: Selectivity Specification Summary

### 7.1 Representative Selectivity Targets by Process Step

| Process Step | Selectivity Target | Rationale |
|---|---|---|
| Hard mask open (Chapter 2, Section 5.2) | High mask:stack selectivity | Preserve maximum mask thickness budget for the subsequent demanding bulk etch |
| Bulk channel hole etch (ON stack) | $S_{avg} \approx 1.0 \pm 0.15$ (illustrative) | Avoid stepped sidewall profile defect (Section 2.1, 2.3) |
| Bulk channel hole etch (OPOP stack) | $S_{avg} \approx 1.0$, requiring more aggressive polymer-forming chemistry to achieve (Section 3.2) | Same profile rationale as ON stack, against larger intrinsic contrast |
| Breakthrough/overetch step | High stack:stop-layer selectivity (often >10:1 or higher, process dependent) | Protect bottom source contact/stop-layer during across-wafer overetch margin (Section 4.1) |

### 7.2 Why These Targets Are Not Independent of Chapters 10-11's Process Window

Each selectivity target in Section 7.1's table must be achieved using chemistry and power settings that simultaneously satisfy Chapter 7's pressure-power-bias phase space boundaries and avoid driving Chapter 11's profile defects to unacceptable severity — selectivity engineering is not a separable, independently-optimized recipe dimension, but one more constraint occupying the same shared, already heavily-constrained process window this book's Part II and Part III chapters have progressively narrowed down. This is the direct, practical reason production channel hole recipe development is typically described by practitioners as a multi-way optimization rather than a sequential, one-variable-at-a-time tuning exercise.

---

## Summary and Forward Look

Selectivity in channel hole etch must be understood as a time-averaged, full-depth quantity rather than an instantaneous, single-film property, since the etch continuously transitions between chemically distinct oxide and nitride (or polysilicon) layers throughout its depth. The bulk etch step generally targets near-balanced ($S_{avg} \approx 1$) selectivity to avoid stepped sidewall defects, achieved by tuning the polymer-forming character of the chemistry to suppress nitride's intrinsically faster chemical etch rate, while the final breakthrough step deliberately targets high, imbalanced selectivity to protect the underlying stop layer during the overetch margin required for full-wafer clearing. Both targets are complicated by the depth-dependent transport attenuation developed in Chapter 10, which does not act with perfectly identical effect on each material and therefore requires full-depth, rather than shallow-feature, characterization to properly engineer.

With etch rate (Chapter 10), profile (Chapter 11), and selectivity (this chapter) now established for the channel hole itself, the next chapter turns to a related but structurally distinct etch problem introduced in Chapter 1: the staircase structure, where dozens of sequential lithography and etch cycles must each expose a single word line layer with tightly controlled step height, compounding this book's etch-rate and selectivity concerns across a multi-step sequence rather than a single continuous etch.
