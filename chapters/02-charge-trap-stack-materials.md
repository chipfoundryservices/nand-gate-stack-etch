# Chapter 2: Charge-Trap Stack Materials — ONO/OPOP Layers & Properties

## Executive Summary

Chapter 1 established what a 3D NAND channel hole etch must accomplish structurally. This chapter establishes what it must accomplish *materially* — the specific films being cut, how they are deposited, what properties those deposition methods impart, and how those properties constrain the etch chemistry and process window developed in later chapters. We examine the sacrificial oxide/nitride (ON) stack that the channel hole etch actually cuts through, the oxide/polysilicon (OPOP) sacrificial variant used in some integration schemes, the later-deposited ONO charge-trap stack that is not part of the channel hole etch but shapes the hole's final electrical requirements, and the film property data (stress, density, wet etch rate, deposition-induced composition gradients) that process integration and etch engineers must jointly manage. Readers should leave this chapter with a working, quantitative sense of why "etching oxide and nitride" is a dramatically harder statement than it first appears once stack height, layer count, and deposition non-idealities are taken into account.

---

## Part 1: The Sacrificial Stack — What the Channel Hole Etch Actually Cuts

### 1.1 Oxide/Nitride (ON) Stack Composition

As established in Chapter 1, the channel hole etch cuts through a sacrificial stack, not the final charge-trap/metal-gate stack. The dominant sacrificial stack across the industry is alternating silicon dioxide (SiO2) and silicon nitride (Si3N4), deposited by plasma-enhanced chemical vapor deposition (PECVD):

| Layer | Material | Typical Thickness (per layer) | Deposition Method | Role |
|---|---|---|---|---|
| Oxide | SiO2 | 20-30 nm | PECVD (TEOS or silane-based) | Final interlayer dielectric; isolates adjacent word lines after replacement |
| Sacrificial nitride | Si3N4 | 25-35 nm | PECVD (silane + ammonia or similar) | Placeholder, removed and replaced with metal word line in Chapter 14's process |

A representative 128-layer stack therefore comprises 128 oxide/nitride pairs — 256 individually deposited films — with a total stack height in the 5.5-6.5 micron range depending on exact per-layer thickness targets. Each of these 256 films is deposited sequentially, meaning total deposition time and film property consistency across the full stack height are both first-order manufacturing concerns before etch ever begins.

### 1.2 Why PECVD, and What It Costs in Film Quality

PECVD is used (rather than, say, thermal CVD or ALD for the bulk oxide/nitride stack) primarily for deposition rate and throughput reasons — at 128-256+ individual film depositions per wafer, even modest per-layer throughput advantages compound into substantial total fab cost differences. PECVD's throughput advantage comes at the cost of several film non-idealities that matter directly to etch:

**Density and stoichiometry gradients.** PECVD oxide and nitride films are typically somewhat understoichiometric and lower density than thermally grown or ALD-deposited equivalents. Si3N4 deposited by PECVD frequently has a Si-rich or H-rich composition relative to ideal stoichiometric Si3N4, with hydrogen content from precursor gases (silane, ammonia) incorporated into the film at levels of several atomic percent. This directly affects etch rate (Chapter 3) and wet-removal selectivity (Chapter 14), since both depend on the Si-N and Si-H bond population and overall film density, not simply on nominal "nitride" composition.

**Intrinsic film stress.** PECVD oxide is typically deposited with modest tensile or compressive stress depending on process conditions (commonly in the range of -200 to +200 MPa), while PECVD nitride is frequently deposited with higher compressive or tensile stress (sometimes several hundred MPa to over 1 GPa in magnitude, again depending on deposition conditions, particularly plasma frequency and precursor ratio). Stacking many alternating high-stress films creates a net stack stress that must be managed; uncontrolled stress can cause wafer bow sufficient to disrupt downstream lithography overlay and etch uniformity (addressed further in Section 3 of this chapter).

**Within-wafer and within-stack thickness non-uniformity.** PECVD deposition rate varies modestly across a 300mm wafer (center-to-edge non-uniformity typically within a few percent for well-tuned processes) and can drift slightly from the first-deposited layer (bottom of stack) to the last-deposited layer (top of stack) due to chamber conditioning changes across a long multi-layer deposition sequence. This "layer drift" directly contributes to the etch rate variation with depth that Chapters 10 and 11 must distinguish from genuine aspect-ratio-driven transport effects — not every etch rate change with depth is ARDE; some is simply inherited from non-uniform input film thickness or composition.

### 1.3 The Oxide/Polysilicon (OPOP) Sacrificial Variant

A smaller set of integration schemes use **polysilicon**, rather than nitride, as the sacrificial layer — an oxide/polysilicon/oxide/polysilicon (OPOP) stack. This variant trades one set of challenges for another:

| Consideration | ON (oxide/nitride) stack | OPOP (oxide/polysilicon) stack |
|---|---|---|
| Sacrificial removal chemistry | Hot phosphoric acid (H3PO4) wet etch, highly selective to oxide | Wet or dry silicon etch (e.g., TMAH-based or halogen-based), different selectivity profile to oxide |
| Channel hole etch selectivity target | Oxide vs. nitride (both dielectrics; moderate intrinsic selectivity contrast) | Oxide vs. polysilicon (dielectric vs. semiconductor; typically larger achievable selectivity contrast, but polysilicon introduces different byproduct chemistry) |
| Stress profile | Nitride stress typically dominates net stack stress | Polysilicon stress behavior differs (often lower intrinsic stress than PECVD nitride, but grain-structure-dependent) |
| Conductivity concerns during processing | Nitride is a good insulator throughout processing; no concern | Polysilicon is semiconducting; charge accumulation and leakage paths during plasma processing require separate consideration (interacts with the charging effects discussed in Chapter 11) |
| Industry prevalence | Dominant approach across most manufacturers | Used in specific integration schemes targeting particular selectivity or stress profiles; less common at scale |

This book's chemistry and process chapters (3, 4, 10-12) primarily treat the oxide/nitride stack as the reference case, given its industry prevalence, but flag OPOP-specific divergence where the underlying physics genuinely differs rather than merely restating the same mechanisms with different material names.

---

## Part 2: Film Property Data Relevant to Etch

### 2.1 SiO2 (PECVD, TEOS-Based) Reference Properties

| Property | Typical Value | Etch-Relevant Consequence |
|---|---|---|
| Density | 2.1-2.2 g/cm³ | Lower than thermal oxide (2.2-2.3 g/cm³); slightly higher chemical etch susceptibility |
| Refractive index (633nm) | 1.45-1.46 | Used as a rapid in-line proxy for stoichiometry/density; deviations flag process drift before etch rate data is even available |
| Wet etch rate (dilute HF, 100:1) | 1.5-3× thermal oxide rate | Higher wet etch rate indicates lower film density/higher porosity, correlating with somewhat higher plasma etch rate as well |
| Intrinsic stress | -300 to +300 MPa (process-tunable) | Contributes to net stack stress (Section 3) |
| Dielectric constant (k) | ~4.0-4.2 | Not directly an etch parameter, but confirms stoichiometry is close to ideal SiO2 |

### 2.2 Si3N4 (PECVD) Reference Properties

| Property | Typical Value | Etch-Relevant Consequence |
|---|---|---|
| Density | 2.6-2.8 g/cm³ (vs. ~3.1-3.2 g/cm³ for stoichiometric LPCVD Si3N4) | Lower density than LPCVD nitride; faster plasma and wet etch rates, more process-condition-sensitive |
| Si/N ratio | Often Si-rich (ratio above the ideal 0.75 Si:N stoichiometric value) | Si-rich films etch somewhat differently in fluorocarbon chemistry (Chapter 3) and respond differently to hot phosphoric acid removal (Chapter 14) |
| Hydrogen content | 2-8 atomic % (process dependent) | H content affects film density and both wet and dry etch rates; higher H content generally correlates with faster removal in both regimes |
| Intrinsic stress | -1.2 GPa to +1.0 GPa (highly process-tunable via deposition frequency/pressure) | Dominant contributor to net multilayer stack stress; frequently deliberately tuned to counteract oxide layer stress (Section 3) |
| Wet etch rate (85% H3PO4, 160°C) | Baseline reference rate used industry-wide for sacrificial nitride removal (Chapter 14) | Oxide/nitride wet etch selectivity in this chemistry is extremely high (often >100:1), which is precisely why hot phosphoric acid is the sacrificial removal chemistry of choice |

### 2.3 Why "Oxide" and "Nitride" Are Not Single, Fixed Materials

A recurring theme worth stating explicitly: because both films are PECVD-deposited and highly tunable via plasma frequency, pressure, precursor ratio, and temperature, "the oxide" and "the nitride" in a given fab's stack are specific, deliberately engineered film recipes, not generic SiO2 and Si3N4. Etch engineers qualifying a channel hole process must characterize etch rate, selectivity, and byproduct behavior against the *actual* deposited films from their own fab's deposition recipe, not against generic literature values for stoichiometric oxide and nitride — deposition-recipe-to-deposition-recipe variation in density and composition alone can shift plasma etch rate by tens of percent. This is a direct, practical consequence of Section 1.2's density/stoichiometry discussion, and it is why etch and deposition process integration teams in 3D NAND fabs work in unusually tight coordination compared to many other process modules.

---

## Part 3: Stack-Level Stress Management

### 3.1 Why Net Stack Stress Matters Before Etch Even Begins

With 128-256+ individual films, even a modest per-film stress imbalance accumulates into substantial net wafer stress. Net compressive or tensile stack stress causes wafer bow — a change in the wafer's overall curvature that:

- **Degrades lithography overlay** for the channel hole pattern itself and for subsequent staircase and slit patterning steps, since scanner overlay correction models assume a nominally flat (or consistently, predictably curved) wafer
- **Introduces non-uniform mechanical loading during etch**, particularly on electrostatic chuck (ESC) systems (Chapter 5), where a bowed wafer makes imperfect, non-uniform thermal and electrical contact with the chuck surface, directly degrading the across-wafer etch uniformity that Chapter 7 and Chapter 10 require
- **Risks wafer breakage or handling failures** in extreme cases, particularly during the already mechanically delicate slit/word-line-replacement sequence (Chapter 14), where large unsupported stack regions exist simultaneously

### 3.2 Stress Compensation Strategy

Because oxide and nitride PECVD stress is independently tunable (Section 2.1, 2.2), deposition process integration teams deliberately engineer the oxide stress and nitride stress to approximately offset one another across the full stack, targeting a net wafer bow within an acceptable range (commonly specified in tens of microns of bow across a 300mm wafer, with exact targets set by downstream lithography overlay budget).

This stress compensation is not, strictly, an etch engineering responsibility — it belongs to deposition process integration. It is included in this chapter because etch engineers must be aware that:

1. **Stress compensation targets can conflict with etch-optimal film density/composition targets.** A film composition that etches most favorably (fastest rate, best selectivity) is not necessarily the composition that hits the required stress target, and process integration frequently must negotiate a compromise recipe rather than independently optimizing deposition for etch and stress separately.
2. **Stress state can evolve during etch and subsequent thermal processing**, particularly once channel holes are cut (locally relieving some stack stress near each hole) and later once sacrificial nitride is removed and replaced with metal (Chapter 14), which has a substantially different intrinsic stress than the nitride it replaces. The net stack stress state is not static across the full process flow — it is a moving target that etch and replacement steps actively perturb.

---

## Part 4: The ONO Charge-Trap Stack — Deposited After Channel Hole Etch

### 4.1 Why This Stack Is Discussed Here, Despite Not Being Etched by the Channel Hole Step

Chapter 1 established that the ONO charge-trap stack (tunnel oxide / trap nitride / blocking oxide) is deposited conformally inside the channel hole *after* the hole is etched, not etched by the channel hole step itself. It is included in this materials chapter because the channel hole etch's acceptance criteria (Chapter 1, Section 4.3) — particularly sidewall roughness, CD uniformity with depth, and profile verticality — exist specifically because the ONO stack and channel polysilicon must subsequently be deposited conformally and uniformly onto the etched sidewall. A channel hole etch can "succeed" by every direct etch metric (full clearing, nominal CD) and still produce a device that fails if the resulting sidewall surface quality prevents good conformal ONO deposition. The etch and the subsequent ONO deposition are, in this sense, a coupled system, and etch process qualification in production fabs typically includes downstream electrical test of fully integrated devices, not just etch-metric inspection, for exactly this reason.

### 4.2 ONO Stack Deposition Method and Thickness Budget

| Layer | Typical Thickness | Deposition Method | Key Property Requirement |
|---|---|---|---|
| Tunnel oxide | 3-6 nm | ALD or high-quality thermal/PECVD, highly conformal | Pinhole-free, uniform thickness along entire multi-micron hole depth; defects here directly cause charge leakage |
| Trap nitride | 5-7 nm | ALD or conformal PECVD | Trap density and uniformity determine program/erase window and retention |
| Blocking oxide (or high-k, e.g., Al2O3) | 5-10 nm | ALD, sometimes with high-k material for improved charge retention | Must block charge leakage toward the word line under full programming field |
| Channel polysilicon | 5-10 nm | LPCVD or ALD, conformal | Forms the actual conduction channel; thickness and crystallinity determine string resistance and read current |

Note the near-universal preference for ALD in this stack, in contrast to the sacrificial stack's PECVD. ALD's self-limiting, conformal growth mechanism is required here because the ONO stack must coat the sidewall of an already-etched, 50:1-100:1+ aspect ratio hole with highly uniform thickness along its entire depth — a requirement PECVD's directional, line-of-sight-influenced deposition cannot reliably meet at this aspect ratio. This is the deposition-side mirror of the etch-side transport problems developed in Chapter 10: both deposition and etch inside extreme-AR features are limited by precursor/etchant transport into the feature, and ALD's self-limiting chemistry is deposition's answer to the same transport bottleneck that pulsed, carefully engineered chemistry (Chapters 3, 9) is etch's answer to.

### 4.3 Macaroni Structure and Core Fill

After the four conformal layers above are deposited, a substantial open core typically remains at the center of the channel hole (particularly at smaller channel hole diameters and thicker ONO/polysilicon stacks). This open core is filled with a dielectric core fill material (commonly a flowable or spin-on oxide), giving the finished string a layered, roughly concentric "macaroni" cross-section: core fill → channel polysilicon → blocking oxide → trap nitride → tunnel oxide → surrounding word line stack.

This core fill step is not an etch step, but it is directly sized by the channel hole etch's final bottom CD: if bottom CD is too small (common at high aspect ratio, per the taper and necking effects discussed in Chapter 11), insufficient room remains for the full ONO/polysilicon/core-fill sequence to be deposited without voids or incomplete fill — a direct, quantitative link between channel hole etch CD control and downstream integration yield that recurs throughout this book.

---

## Part 5: Quantifying Stress and Its Downstream Impact

### 5.1 A Worked Stress-to-Bow Estimate

Wafer bow resulting from a thin-film stack's net stress can be estimated using Stoney's equation, which relates substrate curvature to film stress, film thickness, and substrate properties:

$$\sigma_f = \frac{E_s}{6(1-\nu_s)} \cdot \frac{t_s^2}{t_f} \cdot \frac{1}{R}$$

where $\sigma_f$ is film stress, $E_s$ and $\nu_s$ are the substrate's Young's modulus and Poisson's ratio, $t_s$ and $t_f$ are substrate and total film thickness, and $R$ is the resulting radius of curvature. Rearranged to estimate bow (deflection) $\delta$ at wafer radius $r$:

$$\delta \approx \frac{r^2}{2R} = \frac{3 \sigma_f t_f r^2 (1-\nu_s)}{E_s t_s^2}$$

**Worked example:** Take a 300mm wafer ($t_s = 775\ \mu m$, $r = 150\ mm$, silicon $E_s \approx 130\ GPa$, $\nu_s \approx 0.28$), a 128-layer stack with total film thickness $t_f \approx 6\ \mu m$, and assume imperfect stress compensation leaves a net residual stack stress of $\sigma_f = 150\ MPa$ (tensile):

$$\delta \approx \frac{3 \times (150 \times 10^6\ Pa) \times (6 \times 10^{-6}\ m) \times (0.15\ m)^2 \times (1-0.28)}{130 \times 10^9\ Pa \times (775 \times 10^{-6}\ m)^2}$$

$$\delta \approx \frac{3 \times 150\times10^6 \times 6\times10^{-6} \times 0.0225 \times 0.72}{130\times10^9 \times 6.0\times10^{-7}} \approx \frac{4.37\times10^1}{7.8\times10^4} \approx 5.6 \times 10^{-4}\ m \approx 560\ \mu m$$

Even a comparatively modest 150 MPa of *residual*, imperfectly compensated net stack stress produces several hundred microns of wafer bow at this film thickness and layer count — far beyond typical lithography overlay budgets (commonly tens of microns). This is why Section 3.2's stress compensation is not optional fine-tuning but a hard requirement, and why the achievable residual stress after compensation (not the raw, uncompensated stress of either individual film) is the actual engineering target that deposition process integration must hit, generation over generation, as stack height continues to grow with rising layer count.

### 5.2 Stress Evolution Across the Process Flow

Net stack stress is not static. Four points in the process flow materially change it, each of relevance to later chapters:

1. **As-deposited (post full stack deposition):** the baseline, stress-compensated state described in Section 3.2.
2. **Post channel hole etch:** removing a regular array of cylindrical holes through the stack locally relieves some stress near each hole, modestly reducing net wafer-level stress but potentially introducing new local stress concentration at hole edges — a secondary contributor to localized profile defects discussed in Chapter 11.
3. **Post slit etch (pre-replacement):** cutting slit trenches between blocks (Chapter 14) removes mechanical continuity between blocks and further relieves stress, but also removes stack rigidity, increasing susceptibility to mechanical deformation during the subsequent, unsupported nitride-removal step.
4. **Post word line replacement:** replacing sacrificial nitride (with its deliberately engineered stress) with deposited tungsten (which has distinctly different, typically high tensile, intrinsic stress) changes the net stack stress state again, after the mechanically most vulnerable point in the entire process (Section 3.2, point 2 revisited) has already been passed.

This stress trajectory — compensated, then partially relieved, then partially relieved again, then reset by a stress-dissimilar metal fill — means that mechanical stability is a moving target across the full integration flow, not a single property set once at deposition. Chapter 14 returns to point 3 and 4 in detail, since the mechanically unsupported interval between slit etch and completed metal fill is widely regarded as the single highest structural-collapse-risk interval in the entire 3D NAND process flow.

### 5.3 Representative Failure Modes Traceable to Materials Properties

| Failure Mode | Material Root Cause | Process Stage Observed |
|---|---|---|
| Wafer breakage / cracking | Uncompensated or excessive net stack stress (Section 5.1) | Post-deposition, pre-etch, or during handling/chucking |
| Lithography overlay failure (channel hole or staircase misregistration) | Wafer bow exceeding scanner correction range | Post-deposition, prior to channel hole or staircase patterning |
| Etch rate drift from bottom to top of a single channel hole, independent of AR effects | Layer-to-layer thickness/composition drift during long multilayer PECVD deposition (Section 1.2) | Observed during channel hole etch, must be deconvolved from genuine ARDE (Chapter 10) |
| Channel hole bottom CD undersized relative to ONO/polysilicon fill budget | Compounded top-to-bottom taper interacting with nominal CD targets set without sufficient margin (Section 4.3) | Observed post-ONO deposition, root cause traces to etch profile and original CD budget decisions made using this chapter's materials data |
| Block/stack collapse or tilting during word line replacement | Loss of mechanical support after sacrificial nitride removal, compounded by residual stress state (Section 5.2, points 3-4) | During or immediately after slit-based nitride removal, before metal fill is complete (Chapter 14) |

---

## Part 6: Edge and Interface Effects Specific to the Materials Stack

### 5.1 Bottom Interface — Source Contact

At the bottom of the stack, the channel hole etch must clear through to an underlying source contact or sacrificial source layer (design-dependent), which is itself typically a different material (doped polysilicon or, in some designs, a sacrificial layer later replaced similarly to the word line sacrificial layers). This bottom interface is where the etch's selectivity and endpoint detection requirements (Chapter 12, Appendix F) are most acute: overetching into or through this layer can damage the eventual source connection for the entire string, while underetching leaves resistive or non-functional bottom contact.

### 5.2 Top Interface and Hard Mask

The channel hole etch begins by etching through a hard mask layer (commonly amorphous carbon or a carbon-based advanced patterning film, chosen for its own etch selectivity against the lithographic photoresist pattern used to open it) before reaching the first oxide/nitride pair of the actual sacrificial stack. Hard mask selectivity and consumption rate directly set a budget on how much mask thickness must be deposited to survive the full depth of the subsequent channel hole etch — at the etch rates and total etch times associated with 100:1+ aspect ratio features, hard mask erosion is a first-order constraint on the overall process window, not an afterthought, and is addressed quantitatively in Chapter 7's phase space discussion and Chapter 9's chemistry/pulsing tradeoffs.

---

---

## Part 7: Deposition Sequencing and Its Interaction With Etch Economics

### 7.1 Total Deposition Time Scaling

Total sacrificial stack deposition time scales directly with layer count, since each layer pair requires its own, largely fixed-duration PECVD step plus chamber transition/purge overhead:

$$t_{\text{dep,total}} \approx N_{\text{layers}} \times (t_{\text{oxide}} + t_{\text{nitride}} + t_{\text{transition}})$$

For representative per-layer deposition times on the order of 30-60 seconds per film (process and tool dependent) plus transition overhead of similar order, a 128-layer stack (256 films) can require on the order of several hours of dedicated deposition tool time per wafer lot pass, scaling toward correspondingly longer times at 176 and 232+ layer generations. This is the deposition-side mirror of the etch-side throughput concern raised in Chapter 1, Section 4.3: both deposition and etch tool-hours scale with layer count, and both must be weighed together in fab capacity planning, since a fab cannot usefully add etch capacity to address a channel-hole bottleneck without correspondingly sufficient upstream deposition capacity to supply fully stacked wafers.

### 7.2 Why Deposition and Etch Must Be Co-Qualified, Not Independently Qualified

A direct consequence of this chapter's material: because deposition process parameters (precursor ratios, plasma frequency, pressure, temperature) simultaneously determine film stress (Section 3), density/stoichiometry (Section 2), and the layer-to-layer thickness consistency that confounds etch-rate analysis (Section 1.2, Section 5.3), a deposition recipe change made purely to improve throughput or stress margin can silently change etch behavior in ways that are not obvious until the next etch qualification run. Mature 3D NAND fabs address this with formal deposition-etch co-qualification procedures — any sacrificial stack deposition recipe revision triggers a corresponding etch process requalification pass, rather than treating deposition and etch as independently tunable, serially connected process steps. This operational practice is a direct, practical consequence of the materials coupling this chapter has described, and is referenced again in Chapter 15's discussion of production process control.

---

## Summary and Forward Look

The channel hole etch cuts through a sacrificial PECVD oxide/nitride (or, less commonly, oxide/polysilicon) stack — not the final metal-gate word line stack, and not the ONO charge-trap stack, both of which are introduced later in the process flow. The specific, deposition-recipe-dependent density, stoichiometry, and stress properties of these PECVD films directly shape achievable etch rate and selectivity, and must be actively coordinated between deposition and etch process integration teams rather than treated as fixed, generic material properties. The ONO charge-trap stack, deposited by ALD after the hole is etched, imposes sidewall quality and bottom CD requirements on the channel hole etch that go beyond simple clearing and nominal CD, linking etch process quality directly to downstream deposition and device yield.

With the materials now defined, the next chapter turns to the plasma chemistry used to etch them: the fluorocarbon-based gas systems (CF4, C4F8, C4F6, CHF3) and their SF6 and O2 co-reactants, the polymer passivation mechanism central to achieving selective, anisotropic etch of these alternating films, and how chemistry choice connects to the aspect-ratio and selectivity requirements this chapter has established.
