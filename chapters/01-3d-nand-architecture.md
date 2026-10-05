# Chapter 1: Introduction to 3D NAND Architecture & Industrial Context

## Executive Summary

Before any discussion of plasma chemistry, reactor design, or profile control is useful, we need a precise picture of what a 3D NAND device actually is and why it is built the way it is. This chapter establishes that picture. We trace the transition from planar (2D) NAND flash to vertical (3D) NAND, explain the two dominant cell architectures (charge-trap and replacement-gate), define the structural vocabulary used throughout the rest of this book — strings, blocks, planes, word lines, channel holes, staircases, and slits — and set the industrial context: who makes these devices, at what layer counts, and why etch is the process step that ultimately gates how fast layer counts can climb. Readers who already have a working knowledge of 3D NAND architecture may skim this chapter for terminology; readers new to memory process technology should treat it as required grounding for everything that follows.

---

## Part 1: From Planar to Vertical — Why 3D NAND Exists

### 1.1 The Planar NAND Scaling Wall

NAND flash memory stores information in arrays of floating-gate or charge-trap transistors, each capable of holding a charge state that persists without power. Through the 2000s and into the early 2010s, NAND flash scaled the same way logic did: shrink the lithographic half-pitch, shrink the cell, fit more cells per unit area.

This approach ran into a set of compounding physical limits as planar cells shrank below roughly the 20nm node, worsening toward 15nm:

**Cell-to-cell interference.** As floating gates moved closer together, the charge stored on one cell increasingly perturbed the threshold voltage of its neighbor through parasitic capacitive coupling. This coupling scales roughly as the inverse of cell pitch, so it worsens faster than linearly as cells shrink.

**Few-electron storage.** A floating gate's charge state at advanced planar nodes was represented by only a few hundred, then a few dozen, stored electrons. Statistical variation in electron count — and even single-electron leakage events — produced increasingly large relative threshold voltage shifts, degrading retention and endurance.

**Lithography cost.** Each half-pitch shrink demanded tighter overlay control and, eventually, multiple-patterning lithography (self-aligned double or quadruple patterning), adding significant cost per additional bit of density gained.

**Coupling noise and read disturb.** Narrower word lines and bit lines increased capacitive and resistive coupling throughout the array, worsening read disturb and program disturb — unwanted threshold voltage shifts induced in unselected cells during program or read operations on their neighbors.

By approximately the 1Y/1Z (15-16nm class) planar NAND generation, these effects combined to make further planar scaling economically and technically unattractive. The industry needed a new scaling vector entirely decoupled from lithographic pitch.

### 1.2 The Vertical Scaling Insight

The insight that defined 3D NAND: if cell density is limited by how small you can print a cell footprint, stop trying to shrink the footprint and instead stack cells vertically on the same footprint.

A 3D NAND array replaces the single layer of planar memory transistors with a vertical stack of conductive word line layers, separated by insulating dielectric layers, with a single vertical channel running through the entire stack. Each point where the vertical channel passes through a word line layer forms one memory cell. A single lithographically defined hole, etched once through the entire stack, therefore creates an entire vertical string of memory cells — 32, 64, 96, 128, 176, or more, depending on generation.

This is the central economic logic of 3D NAND: **bit density now scales with layer count, a parameter controlled by deposition and etch process capability, rather than by lithographic resolution.** Adding capacity no longer requires a new lithography node — it requires depositing and successfully etching more layers.

This logic also explains why etch, not lithography, became the long-pole process step in 3D NAND scaling. Lithography still defines the channel hole's diameter and pitch at the top of the stack, but it does so once, at a single, comparatively relaxed critical dimension (typically 100-150nm channel hole diameter — far looser than contacted logic gate pitch at equivalent technology generations). The etch step, by contrast, must propagate that single lithographically defined opening through an increasingly tall stack without the hole closing, drifting, or deforming. As layer count climbs, lithography's job stays essentially constant while etch's job gets monotonically harder.

### 1.3 Industrial Timeline and Current State

| Era | Approx. Layer Count | Representative Generation Naming | Notes |
|-----|---------------------|-----------------------------------|-------|
| 2013-2014 | 24-32 | 1st-2nd gen (Samsung V-NAND) | First commercial 3D NAND; charge-trap cell introduced |
| 2015-2016 | 32-48 | 3rd-4th gen | Multiple manufacturers (SK hynix, Toshiba/Kioxia, Micron/Intel) enter production |
| 2017-2018 | 64-72 | 5th-6th gen | String stacking (two tiers bonded) introduced to manage aspect ratio |
| 2019-2020 | 96-128 | 6th-7th gen | Aspect ratio exceeds 50:1 for single-tier etch |
| 2021-2022 | 128-176 | 7th-8th gen | Aspect ratio approaches/exceeds 80:1-100:1; string stacking near-universal |
| 2023-2026 | 176-300+ | 8th-9th+ gen | Multi-tier stacking (3-4 tiers), per-tier AR managed near 50-70:1; total effective layer count climbs while per-etch-step AR is partially decoupled via stacking |

**Note on string stacking:** as single-etch aspect ratio became a hard limiter (addressed in depth in Chapter 10), manufacturers increasingly etch the channel hole in two or more vertically stacked tiers, each deposited and etched separately, then aligned and connected. This does not eliminate the extreme-AR etch problem — it caps the *per-step* aspect ratio at a more manageable value while total layer count continues to climb. Alignment between tiers (channel hole-to-channel hole overlay through an already-etched lower tier) introduces its own yield-limiting challenge, discussed in Chapter 15.

### 1.4 Industry Participants

The 3D NAND manufacturing base is concentrated among a small number of memory manufacturers, each running a largely vertically integrated process (design, fab, and in most cases significant in-house process development):

- **Samsung Electronics** — pioneered commercial V-NAND (vertical NAND) using a charge-trap cell architecture
- **SK hynix** — charge-trap architecture, significant 3D NAND volume alongside DRAM
- **Kioxia (formerly Toshiba Memory) / Western Digital** — joint venture fabs, charge-trap architecture, co-developed with Toshiba's original BiCS (Bit Cost Scalable) 3D NAND concept
- **Micron Technology** — initially partnered with Intel (IM Flash Technologies) on a floating-gate-derived 3D architecture (CTF variant), now independent following Intel's 2021 exit from NAND
- **YMTC (Yangtze Memory Technologies Corporation)** — later entrant, notable for Xtacking architecture that separates peripheral CMOS circuitry from the memory array, bonding them together, allowing independent process optimization of each

Equipment suppliers central to the etch steps discussed in this book include Lam Research (a long-standing leader in high-aspect-ratio dielectric etch), Applied Materials, and Tokyo Electron, each of whom has developed dedicated channel-hole and staircase etch platforms distinct from their logic-oriented etch tools.

---

## Part 2: Cell Architecture — Charge-Trap and Replacement-Gate Designs

### 2.1 The Charge-Trap Cell

Most 3D NAND architectures (Samsung, SK hynix, Kioxia/WD, YMTC) use a **charge-trap** memory cell rather than the floating-gate cell that dominated planar NAND. The distinction matters directly for etch:

**Floating-gate cell (planar NAND legacy):** stores charge in a discrete, electrically isolated conductive floating gate (typically doped polysilicon), separated from the channel by a thin tunnel oxide and from the control gate by an interpoly dielectric (commonly ONO — oxide-nitride-oxide — used as a capacitive-coupling and leakage-blocking stack, not as the charge storage layer itself).

**Charge-trap cell:** stores charge in trap sites within a layer of silicon nitride (or in some designs, a high-k charge-trapping dielectric), rather than in a discrete conductive floating gate. The cell stack, moving outward from the channel, is: tunnel oxide → charge-trapping nitride → blocking oxide → control gate (word line) metal. This is frequently called an ONO stack by analogy with the planar interpoly dielectric, but functionally the nitride layer here is the charge storage layer, not merely a capacitive/blocking layer.

**Why charge-trap suits a vertical, etched structure:** a floating-gate cell requires a discrete, electrically isolated polysilicon island at every single memory layer — difficult to form and electrically isolate from neighboring cells in a vertically etched hole shared by dozens to hundreds of layers. A charge-trap cell's charge storage nitride layer can instead run continuously along the full height of the vertical channel hole sidewall, with each word line layer's gate simply wrapping around the outside of the common ONO stack at that height. Isolation between vertically adjacent cells' stored charge relies on the trap sites' limited lateral mobility within the nitride, not on physical, etched separation. This is a direct, structural reason vertical scaling pushed the industry toward charge-trap architectures.

### 2.2 The Gate Stack Cross-Section — Charge-Trap (ONO) Variant

Reading radially outward from the vertical channel at any single word-line height:

1. **Channel polysilicon** — a thin (typically 5-10nm) polysilicon liner deposited inside the etched channel hole, forming the transistor's conduction channel for the entire vertical string
2. **Tunnel oxide** (SiO2, ~3-6nm) — permits electron tunneling during program/erase while blocking leakage during read/retention
3. **Charge-trapping nitride** (Si3N4, ~5-7nm) — stores charge in trap states; forms the "N" in ONO
4. **Blocking oxide** (SiO2 or high-k dielectric such as Al2O3, ~5-10nm) — prevents charge injected toward the control gate from leaking back, and withstands the programming field
5. **Word line metal** (typically TiN barrier + W fill, or in some designs a different metal gate stack) — the control gate, shared across the entire plane at that vertical height, acting as the control gate for every memory cell at that layer across the whole array

This ONO-plus-metal-gate stack is deposited (for the ONO portion) largely conformally inside the already-etched channel hole, after the channel hole etch itself — meaning the channel hole etch chapter (addressing the vertical dielectric stack etch) and the ONO deposition are sequential, cooperating steps, not the same step. The word line metal is introduced later still, during the replacement-gate process described below.

### 2.3 Replacement-Gate (Gate-Last) Integration

A critical and non-obvious point: the stack through which the channel hole is actually etched is **not** the final oxide/metal-gate word line stack. For both charge-trap and most modern 3D NAND architectures, the industry uses a **replacement-gate** (also called gate-last or "oxide-nitride" sacrificial) integration scheme:

1. The stack is deposited as **alternating oxide and *sacrificial* silicon nitride** layers (an OPOP-adjacent naming convention: oxide-poly-oxide-poly is used in some literature for a related sacrificial-polysilicon variant; oxide-nitride, "ON," is the more common sacrificial pairing in current charge-trap 3D NAND).
2. The **channel hole is etched through this full sacrificial oxide/nitride stack** — this is the headline high-aspect-ratio etch step this book centers on.
3. The ONO charge-trap stack and channel polysilicon are deposited conformally inside the finished channel hole.
4. Later, **slit trenches** are etched down through the stack between blocks, and the **sacrificial nitride is removed through these slits** with a highly selective wet or dry etch, leaving behind a stack of thin horizontal cavities (oxide layers now unsupported except by the channel hole pillars).
5. **Word line metal (typically TiN + W) is deposited through the same slits**, filling the cavities left by the removed nitride, forming the final control gate at every layer simultaneously.

**Why go through this replacement sequence instead of depositing the final metal gate stack directly?** Depositing silicon nitride (a dielectric, deposited by well-controlled CVD/ALD) as a sacrificial placeholder is far more manufacturable at this stage than attempting to deposit void-free tungsten in every one of 96-176+ ultra-thin horizontal layers simultaneously, with a channel hole etch happening afterward through a stack that would otherwise contain many thin metal layers (etch chemistry and selectivity against metal word lines directly would be a substantially harder problem, and thermal budget constraints on finished metal word lines would restrict later high-temperature anneal steps). Using a sacrificial dielectric defers the metal step until after the hard etch and anneal steps are complete, at the cost of adding the slit-etch-and-replace sequence as its own, separately difficult process (treated in depth in Chapter 14).

This replacement-gate sequence is why this book's scope explicitly includes **both** channel hole etch through the oxide/sacrificial-nitride stack **and** the later slit etch / word line replacement step — they are etch-adjacent steps in the same overall integration scheme, and an etch engineer working on one is very likely to also own or interact with the other.

---

## Part 3: Structural Vocabulary

The remainder of this book uses the following terms freely; precise definitions here will save confusion later.

| Term | Definition |
|------|------------|
| **String** | A single vertical channel hole with its associated ONO stack and channel polysilicon, running through the entire layer stack; electrically, a single series-connected chain of memory cell transistors plus top/bottom select transistors |
| **Word line (WL)** | A single horizontal conductive layer, shared across many strings, acting as the control gate for one memory cell in each string that passes through it; one word line exists at each vertical "layer" of the stack |
| **Block** | The minimum unit of erase; a group of strings sharing the same set of word lines, bounded by slit trenches on each side |
| **Plane** | A group of blocks that can operate somewhat independently for performance (parallel read/write across planes); multiple planes exist per die |
| **Channel hole (CH)** | The single vertical hole etched through the entire oxide/sacrificial-nitride stack, later filled with the ONO stack and channel polysilicon, forming one string |
| **Slit** | A long vertical trench etched between blocks, used first to remove sacrificial nitride (replacement-gate process) and later filled with an isolation structure between blocks; distinguished from the channel hole by its trench (not cylindrical hole) geometry and typically different (though related) aspect ratio challenges |
| **Staircase** | A stepped structure at the edge of each block where each word line layer is individually exposed at a different horizontal position, allowing vertical contact plugs to land on and electrically connect to each word line independently; formed by repeated trim-etch cycles (Chapter 13) |
| **Select gate (SGS/SGD)** | Additional transistor layers at the bottom (source select, SGS) and top (drain select, SGD) of each string, used to electrically select which string is active during a given read/write/erase operation; etched as part of the same channel hole but often requiring distinct process control due to different stack composition at these layers |
| **ONO** | Oxide-Nitride-Oxide; in this book, refers to the charge-trap gate stack deposited inside the finished channel hole (tunnel oxide / trap nitride / blocking oxide), distinct from the sacrificial oxide/nitride pairs etched during channel hole formation |
| **OPOP** | Oxide-Polysilicon-Oxide-Polysilicon; a sacrificial stack variant (polysilicon rather than nitride as the sacrificial layer) used in some replacement-gate schemes; mechanically and electrically distinct etch behavior from oxide/nitride sacrificial stacks, discussed where relevant in Chapter 2 |
| **Pair** or **layer pair** | One oxide layer plus its adjacent sacrificial layer (nitride or polysilicon), counted together; "128-layer" 3D NAND typically means 128 word-line-equivalent pairs, i.e., 128 oxide/sacrificial pairs (256 individual deposited films) |

**A note on "layer count" ambiguity:** marketing and even technical literature are inconsistent about whether "128-layer" refers to 128 word lines (pairs) or 128 total deposited films (half that many word lines). Throughout this book, layer count refers to word-line-equivalent pairs unless explicitly stated otherwise, consistent with how most memory manufacturers report generation naming.

---

## Part 4: Why Etch Gates the Roadmap

### 4.1 The Three Etch Steps That Matter Most

This book's four parts are organized around chamber design and process physics in the abstract, but it is worth stating plainly, early, which three etch steps actually determine whether a given 3D NAND generation ships:

1. **Channel hole etch** — the vertical etch through the full oxide/sacrificial stack, at aspect ratios now exceeding 100:1 at the per-tier level even with string-stacking mitigation. This is the subject of Parts II and III in full.
2. **Staircase etch** — dozens of sequential trim-and-etch cycles exposing each word line for contact; errors compound multiplicatively across steps, and total process time scales with layer count. Chapter 13.
3. **Slit etch and word line replacement** — a high-aspect-ratio trench etch (though generally lower AR than the channel hole) followed by a highly selective sacrificial removal and metal fill, performed on a mechanically unsupported stack. Chapter 14.

### 4.2 Why Aspect Ratio, Specifically, Is the Roadmap Bottleneck

Returning to the central economic logic from Section 1.2: because bit density scales with layer count, and layer count directly increases channel hole aspect ratio (hole diameter is roughly fixed by lithography and cell electrical requirements; hole depth scales with layer count), **every subsequent 3D NAND generation requires etching a deeper hole through the same or a narrower opening.** There is no way to add layers without increasing aspect ratio, short of either string-stacking (capping per-step AR, at the cost of added process complexity and tier-to-tier alignment risk) or widening the channel hole diameter (directly reducing bit density, defeating the purpose).

This is why channel hole etch capability — specifically, a reactor and process's ability to maintain acceptable etch rate, selectivity, and profile control as aspect ratio climbs — is widely regarded within the industry as *the* long-pole capability gating 3D NAND layer-count roadmaps. A new deposition tool capable of laying down 50 additional layer pairs is of limited value if no etch process exists that can cut a straight, non-bowed, fully-cleared hole through the resulting stack.

### 4.3 What "Success" Looks Like for a Channel Hole Etch

To ground the rest of this book's technical content, it is useful to state the acceptance criteria a production channel hole etch process must satisfy simultaneously:

- **Full clearing:** the etch must reach the bottom of the stack and clear through to the underlying source/channel contact layer, across every channel hole on the wafer, with margin for across-wafer and across-lot process variation
- **CD (critical dimension) control:** top CD, bottom CD, and CD at intermediate depths must each fall within a tight specification window (typically a few nanometers at advanced generations), since CD directly affects cell electrical characteristics and string resistance
- **Profile control:** minimal bowing, twisting, necking, or taper (Chapter 11), since each distorts local electric fields, can cause adjacent-hole shorting (bowing), or can produce localized resistance bottlenecks (necking) that degrade string performance or yield
- **Selectivity to the stop layer:** the etch must stop (or be stopped by an engineered endpoint signal, Appendix F) at the correct underlying layer without significant overetch damage
- **Within-wafer and wafer-to-wafer uniformity:** the above criteria must hold not just for a single, best-case channel hole, but across potentially trillions of channel holes per wafer lot at production volume
- **Throughput:** the etch must complete in a commercially viable time per wafer, a target made harder, not easier, by every improvement in aspect ratio

Every subsequent chapter in this book builds toward understanding how chemistry, chamber design, and process control combine to meet these criteria, and what happens, mechanistically, when they are not met.

---

---

## Part 5: Quantifying the Scaling Problem

### 5.1 Bit Density as a Function of Layer Count

The economic argument in Section 1.2 is worth making quantitative. For a given channel hole pitch (center-to-center spacing between adjacent strings) and a given number of bits stored per cell (SLC, MLC, TLC, QLC — 1, 2, 3, or 4 bits respectively), the areal bit density of a 3D NAND array scales linearly with word line layer count:

$$\text{Bits/mm}^2 \approx \frac{N_{\text{layers}} \times B_{\text{bits/cell}}}{A_{\text{pitch}}}$$

where $N_{\text{layers}}$ is the word-line-equivalent layer count, $B_{\text{bits/cell}}$ is bits stored per cell, and $A_{\text{pitch}}$ is the effective area per string (a function of channel hole pitch in both the X and Y directions, accounting for staircase and slit area overhead, which does not scale with layer count and therefore becomes a *smaller* fractional overhead as layer count rises — a secondary, favorable scaling effect).

**Worked example:** Consider a channel hole pitch producing roughly $2.0 \times 10^{-10}\ \text{mm}^2$ effective area per string (a representative value for advanced-generation channel hole arrays), TLC (3 bits/cell) operation, and compare 128-layer to 232-layer generations:

- 128-layer, TLC: $\dfrac{128 \times 3}{2.0 \times 10^{-10}} \approx 1.92 \times 10^{12}\ \text{bits/mm}^2$
- 232-layer, TLC: $\dfrac{232 \times 3}{2.0 \times 10^{-10}} \approx 3.48 \times 10^{12}\ \text{bits/mm}^2$

An 81% increase in layer count (128 → 232) yields a corresponding ~81% increase in areal bit density, at constant lithographic pitch — this is the direct arithmetic expression of "bit density now scales with layer count." No lithography shrink was required to achieve this gain; the entire gain was purchased with deposition and etch capability.

### 5.2 Aspect Ratio Growth and Why It Is Nonlinear in Impact

Aspect ratio (AR) is defined as etched depth divided by minimum etched diameter:

$$AR = \frac{D_{\text{depth}}}{d_{\text{diameter}}}$$

Stack height grows roughly linearly with layer count (each layer pair contributes a largely fixed combined oxide + sacrificial-layer thickness, typically in the 35-55nm total range per pair depending on generation and cell design). Channel hole diameter, by contrast, is held nearly fixed across generations — shrinking it would reduce channel polysilicon volume and raise string resistance, degrading read current and performance, so manufacturers resist shrinking it even as layer count climbs.

The result: aspect ratio grows nearly in direct proportion to layer count, while the *difficulty* of maintaining etch rate, selectivity, and profile control grows considerably faster than linearly with aspect ratio, for transport-physics reasons developed fully in Chapter 10. A rough illustration using representative values:

| Generation (word-line layers) | Representative Stack Height | Representative CH Diameter | Approx. Aspect Ratio |
|---|---|---|---|
| 32 | ~1.5 µm | ~120 nm | ~12:1 |
| 64 | ~3.0 µm | ~120 nm | ~25:1 |
| 96 | ~4.5 µm | ~115 nm | ~39:1 |
| 128 (single-tier) | ~6.0 µm | ~110 nm | ~55:1 |
| 176 (single-tier) | ~8.5 µm | ~105 nm | ~81:1 |
| 232+ (per-tier, string-stacked) | ~5.5 µm per tier × 2 tiers | ~100 nm | ~55:1 per tier (×2 tiers) |

(Figures are illustrative, derived from publicly reported stack height and CD ranges across generations; exact values vary by manufacturer and are frequently not disclosed precisely.)

The rightmost rows illustrate directly why string stacking became necessary: without it, a 176-layer-class single-tier etch would need to sustain roughly 81:1 aspect ratio, and a hypothetical single-tier 232-layer device would approach or exceed 110:1 — aspect ratios at which, as Chapter 10 develops quantitatively, etch rate falls sharply and profile control becomes extremely difficult to hold. Splitting the same total layer count across two tiers approximately halves the per-step aspect ratio back into a more tractable range, at the cost of a second full deposition-etch-fill sequence and a tier-to-tier overlay/alignment requirement.

### 5.3 Why Lithography Is Not the Bottleneck Here

It is worth being explicit about why this book centers etch rather than lithography, since in logic scaling the reverse is usually true. Channel hole diameter and pitch are lithographically defined once, at the top of the stack, before etch begins. A 100-150nm channel hole diameter is, in absolute terms, a comparatively relaxed critical dimension — roughly an order of magnitude larger than contacted gate pitch in logic processes at an equivalent technology generation. Multiple-patterning techniques developed for logic are not generally required to resolve channel hole arrays at these pitches using modern immersion lithography.

What lithography cannot do is guarantee that the pattern it defines at the top of the stack survives, undistorted, all the way to the bottom of an 80:1+ aspect ratio feature. That guarantee is entirely the etch process's responsibility, which is why etch capability — not lithographic resolution — gates the layer-count roadmap. This is a structurally different scaling relationship than logic, where lithographic pitch is usually the first-order limiter, and it is the reason 3D NAND etch tooling and process development commands the specialized attention this book devotes to it.

---

---

## Part 6: Economic Context — Capital Intensity and Equipment Differentiation

### 6.1 Why Memory Fabs Are Different From Logic Fabs

3D NAND fabs share equipment categories with logic fabs (lithography, deposition, etch, CMP, metrology) but differ sharply in process economics:

- **Fewer unique mask layers, far more repetition of a smaller process set.** A logic process may use 60-90+ unique mask layers with great layer-to-layer variety. A 3D NAND process uses relatively few unique masks (channel hole, staircase steps, slit, contacts, interconnect), but the channel hole and staircase steps are each extraordinarily demanding and consume outsized tool-hours.
- **Deposition and etch tool-hours dominate cost, not lithography tool-hours.** Each additional layer pair requires its own deposition step (adding incremental, roughly linear cost) and makes the single channel hole etch step incrementally harder (adding more-than-linear cost in etch time and consumables, per Section 5.2). Lithography cost per wafer is comparatively flat across generations because channel hole CD and pitch are not aggressively scaled layer-count-over-layer-count the way logic pitch scales node-over-node.
- **Etch tool capital cost and tool count scale with layer-count ambition.** A fab targeting 300+ layer generations must deploy etch platforms with sufficient ion energy, chemistry delivery precision, and pulsing capability to hold acceptable channel hole etch performance at the resulting aspect ratios — directly linking capital equipment roadmap to the physics developed in Parts II and III of this book.

### 6.2 Yield Economics at High Layer Count

Consider the yield impact of a single defective channel hole. In planar NAND, a single defective cell corresponded to a single bit (or a small, localized group of bits in the case of column/row defects) — a comparatively contained yield loss. In 3D NAND, a single channel hole etch failure (incomplete clearing, severe bowing causing an adjacent-hole short, or a necking defect severing the channel) can disable an *entire vertical string* — every memory cell at every layer along that one hole.

As layer count rises, the amount of storage capacity riding on each individual channel hole's etch quality rises in direct proportion. A channel hole etch defect rate that was tolerable at 64 layers (where a lost string sacrifices 64 cells' worth of capacity) becomes proportionally more costly at 232 layers (where the same per-hole defect rate now sacrifices 232 cells' worth of capacity per failure). This is the quantitative form of the yield-sensitivity argument introduced in the Preface, and it is a direct consequence of the architecture described in this chapter: it explains why channel hole etch process control (Chapters 7, 10, and 11) receives such disproportionate engineering investment relative to its apparent position as "just one etch step" in the overall process flow.

### 6.3 Forward References Within This Book

To orient the reader for what follows, the major open questions this chapter has raised, and the chapters that resolve them, are:

- *What exactly is being etched, materials-wise, and how does that constrain chemistry?* → Chapter 2 (stack materials) and Chapter 3 (fluorocarbon chemistry)
- *Why does etch rate fall and profile control degrade so sharply as aspect ratio rises, beyond simple intuition?* → Chapter 10 (ARDE at extreme AR), building on reactor and chemistry foundations in Chapters 4-9
- *What specifically causes bowing, twisting, and necking, and how are they controlled?* → Chapter 11
- *How does the staircase get etched without compounding CD error across dozens of steps?* → Chapter 13
- *How does the sacrificial nitride actually get removed and replaced with metal, given the structure has no mechanical support once the nitride is gone?* → Chapter 14
- *How is all of this held in statistical control across a production fab running many tools and many lots simultaneously?* → Chapter 15

---

## Part 7: Select Gates, String Geometry, and Edge-of-Array Effects

### 7.1 Select Gate Layers

Every string requires more than just the memory cell word lines. At the bottom of the stack, one or more **source select gate (SGS)** layers connect the string to a common source line; at the top, one or more **drain select gate (SGD)** layers connect the string to its bit line and allow individual strings within a block to be selected independently during read and program operations (since an entire block shares the same word lines, SGD layers are what allow one string within that block to be addressed without disturbing its neighbors).

SGD layers are frequently split into multiple, electrically isolated sub-layers (two to four, depending on design) specifically to improve per-string selectivity and reduce program disturb on unselected strings sharing the same word lines. These additional, finely divided layers near the top of the stack impose their own local CD and isolation requirements on the channel hole etch, distinct from the bulk memory-layer requirements lower in the stack — the etch process must perform correctly across a stack that is not materially uniform even in the categories "memory layer" versus "select layer."

### 7.2 Why Select Gate Layers Complicate the Etch Problem

From an etch perspective, select gate regions matter for two reasons developed further in Chapters 11 and 12:

1. **Different local stack composition near the top of the hole** (thinner individual sub-layers, sometimes different dielectric choices for improved isolation) means the etch front experiences a materially different environment in roughly the first several hundred nanometers of depth compared to the bulk memory array region — exactly where plasma and neutral species are most abundant and where you might otherwise assume etch behavior is simplest and most stable.
2. **Top CD at the SGD layers has a tighter electrical specification** than bulk memory-layer CD in many designs, because select transistor on/off characteristics directly gate read/program disturb margins — meaning the etch step's hardest CD control requirement is sometimes not at the bottom of the hole (where clearing and bottom CD dominate concerns) but near the top, in a region etch engineers might otherwise be tempted to treat as "the easy part."

### 7.3 Comparative Cell Architecture Summary

| Manufacturer | Cell Type | Sacrificial Stack | Distinguishing Architectural Feature |
|---|---|---|---|
| Samsung | Charge-trap (ONO) | Oxide/nitride | Pioneered commercial V-NAND; multi-tier string stacking from ~128L generation onward |
| SK hynix | Charge-trap (ONO) | Oxide/nitride | PBE (Peripheral under Cell) design places peripheral circuitry beneath the array |
| Kioxia / Western Digital | Charge-trap (ONO), BiCS lineage | Oxide/nitride | Joint-venture fabs; BiCS FLEX multi-tier architecture |
| Micron | Charge-trap (CTF, floating-gate-derived) | Oxide/nitride | Replacement-gate CTF (charge trap flash) cell; independent process following 2021 Intel JV exit |
| YMTC | Charge-trap (ONO), Xtacking | Oxide/nitride | Xtacking bonds separately optimized peripheral CMOS wafer to array wafer, decoupling peripheral transistor process from array thermal budget |

While manufacturers differ in cell electrical design, select gate configuration, and tiering strategy, all current mainstream 3D NAND architectures share the core elements this chapter establishes as the book's scope: a charge-trap cell, a sacrificial oxide/nitride replacement-gate stack, and a single etched channel hole per string. This commonality is why the etch physics and chamber engineering developed in the remainder of this book apply broadly across the industry rather than to a single manufacturer's design.

### 7.4 Generation Naming Is Not Standardized

Readers consulting manufacturer literature or industry press should be aware that "generation" and layer-count naming conventions are not standardized across companies, and are not always literal. A manufacturer's "176-layer" product may refer to word-line-equivalent count, may be achieved via two stacked tiers of 88 each, and may coexist in the same company's roadmap with internal engineering generation numbers that do not match the externally marketed layer count. This book uses layer-count terminology (as defined in Part 3) descriptively and consistently, but when cross-referencing external literature, confirm which convention a given source is using before comparing figures directly.

---

## Summary and Forward Look

3D NAND exists because planar NAND flash scaling hit a wall around the mid-2010s, and the industry's answer was to stack memory cells vertically rather than continue shrinking them laterally. This vertical stacking decouples bit density from lithographic pitch and instead ties it to layer count — a parameter controlled by deposition and etch capability. Most 3D NAND uses a charge-trap cell architecture, built via a replacement-gate (gate-last) integration scheme: a sacrificial oxide/nitride (or oxide/polysilicon) stack is deposited and etched first, the charge-trap ONO stack and channel polysilicon are added inside the resulting channel hole, and the sacrificial nitride is later removed and replaced with metal word lines through separately etched slit trenches.

This architecture makes channel hole etch — a single hole etched through tens to hundreds of alternating dielectric layers at aspect ratios now exceeding 100:1 — the central bottleneck process in 3D NAND scaling, with staircase etch and slit/word-line-replacement etch as closely related, comparably demanding supporting processes.

The next chapter examines the materials that make up the stack being etched: the specific properties of the oxide and sacrificial nitride (or polysilicon) films, how they are deposited, and how those deposition-driven properties constrain the etch chemistry and process window available to subsequent chapters.
