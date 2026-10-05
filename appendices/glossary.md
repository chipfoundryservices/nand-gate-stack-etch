# Glossary: 3D NAND Etch-Specific Terminology

Terms are defined as used throughout this book. Where a term has a broader or alternate meaning elsewhere in the semiconductor industry, the definition below reflects this book's specific usage and chapter context.

---

**ALD (Atomic Layer Deposition)** — A self-limiting, cycle-based deposition technique producing highly conformal films, used for the ONO charge-trap stack and TiN word line barrier layer specifically because of its ability to coat extreme-aspect-ratio sidewalls uniformly. See Chapter 2, Section 4.2; Chapter 14, Section 3.1.

**Aspect Ratio (AR)** — Etched feature depth divided by minimum feature diameter (or width, for trench features). The central difficulty-scaling parameter throughout this book. See Chapter 1, Section 5.2; Chapter 10.

**ARDE (Aspect Ratio Dependent Etching)** — The phenomenon by which etch rate declines as a function of increasing feature aspect ratio, arising from ion trajectory filtering and Knudsen-regime neutral transport attenuation. See Chapter 10.

**Afterglow** — The interval following source power reduction in a pulsed plasma, during which electron temperature decays rapidly while ion and radical populations persist longer, producing a transient chemistry distinct from both the active-discharge and fully-decayed states. See Chapter 9, Section 2.2.

**Block** — The minimum unit of erase in 3D NAND; a group of strings sharing the same word lines, bounded by slit trenches. See Chapter 1, Part 3.

**Bowing** — A channel hole profile defect characterized by a local maximum in diameter at an intermediate etch depth, narrower above and below. See Chapter 11, Part 1.

**Breakthrough step / Overetch step** — The final channel hole etch recipe step, tuned for high selectivity against the bottom stop-layer material rather than for profile control. See Chapter 3, Section 4.2; Chapter 12, Part 4.

**C4F6, C4F8, CF4, CHF3** — Fluorocarbon etch gases used in channel hole etch chemistry, distinguished by carbon-to-fluorine ratio and resulting polymer-forming tendency. See Chapter 3, Part 2.

**Channel Hole (CH)** — The single vertical hole etched through the entire sacrificial oxide/nitride (or oxide/polysilicon) stack, later filled with the ONO stack and channel polysilicon to form one memory string. See Chapter 1, Part 3.

**Charge-Trap Cell** — A memory cell architecture storing charge in trap sites within a silicon nitride layer, as opposed to a discrete floating-gate conductor. The dominant cell architecture in modern 3D NAND. See Chapter 1, Part 2.

**Charging (Differential Charging)** — The accumulation of net positive charge at the bottom of an extreme-aspect-ratio dielectric feature, arising from the mismatch between directionally-constrained ion flux and comparatively isotropic electron flux reaching the feature bottom. A primary amplifier of twisting and bowing defects. See Chapter 11, Part 3.

**CCP (Capacitively Coupled Plasma)** — A plasma source architecture in which RF power is applied across parallel electrodes, coupling the plasma generation and wafer bias functions through the same applied field. See Chapter 5, Part 1.

**Clausing Factor / Transport Probability** — The probability that a gas molecule entering a feature's top opening successfully reaches the feature bottom without being lost to sidewall reaction, as a function of aspect ratio and sidewall reactivity. See Chapter 10, Part 2.

**Duty Cycle** — In pulsed RF operation, the fraction of each pulse period spent in the active (high-power) state. See Chapter 9, Part 2-3.

**Etch Stop** — The condition in which net sidewall/bottom polymer accumulation exceeds ion-assisted clearing capacity, halting further etch progress at a given depth. See Chapter 3, Section 5.3; Chapter 10, Section 4.3.

**FDC (Fault Detection and Classification)** — A production process control system monitoring real-time tool sensor data to detect acute, discrete process excursions. See Chapter 15, Section 5.3.

**ICP (Inductively Coupled Plasma)** — A plasma source architecture using an RF-driven coil to generate plasma via induced electric fields, allowing plasma density (source power) and wafer ion energy (bias power) to be controlled largely independently. See Chapter 5, Part 1.

**Knudsen Regime** — The gas transport regime in which the mean free path of gas molecules is comparable to or larger than the relevant feature dimension, such that molecules travel between sidewall collisions rather than diffusing via continuum (Fickian) transport. See Chapter 4, Section 3.3.

**Layer Pair** — One oxide layer plus its adjacent sacrificial layer (nitride or polysilicon), counted together as the basic repeating unit of the 3D NAND stack. See Chapter 1, Part 3.

**Microloading** — Etch rate or gas consumption variation driven by local feature pattern density, distinct from aspect-ratio-driven effects. See Chapter 6, Section 2.3.

**Necking** — A channel hole profile defect characterized by a local minimum in diameter at a specific depth, often coinciding with a recipe step transition. See Chapter 11, Part 4.

**ONO (Oxide-Nitride-Oxide)** — In this book, the charge-trap gate stack (tunnel oxide / trap nitride / blocking oxide) deposited inside the finished channel hole, distinct from the sacrificial oxide/nitride pairs etched during channel hole formation. See Chapter 1, Section 2.2; Chapter 2, Part 4.

**OPOP (Oxide-Polysilicon-Oxide-Polysilicon)** — A sacrificial stack variant using polysilicon rather than nitride as the sacrificial layer. See Chapter 2, Section 1.3.

**PECVD (Plasma-Enhanced Chemical Vapor Deposition)** — The deposition method used for the bulk sacrificial oxide/nitride stack, chosen for throughput at the cost of some density/stoichiometry non-ideality relative to thermal or ALD alternatives. See Chapter 2, Part 1-2.

**R2R (Run-to-Run) Control** — A production process control methodology using metrology feedback from completed wafers/lots to compute small corrective adjustments to subsequent lots' recipe parameters. See Chapter 15, Part 2.

**Replacement-Gate (Gate-Last) Integration** — The 3D NAND integration scheme in which a sacrificial oxide/nitride (or oxide/polysilicon) stack is etched first, then later removed and replaced with metal word lines through slit-based access. See Chapter 1, Section 2.3.

**SGD / SGS (Drain/Source Select Gate)** — Additional transistor layers at the top (SGD) and bottom (SGS) of each string, used to electrically select active strings during read/write/erase operations. See Chapter 1, Part 7.

**Slit** — A long vertical trench etched between blocks, used as the access path for sacrificial nitride removal and metal fill, and later filled as an isolation structure. See Chapter 1, Part 3; Chapter 14, Part 1.

**Staircase** — A stepped structure at the edge of each block where each word line layer is individually exposed at a distinct horizontal position for contact. See Chapter 1, Part 3; Chapter 13.

**String** — A single vertical channel hole with its associated ONO stack and channel polysilicon, forming a series-connected chain of memory cell transistors plus select transistors. See Chapter 1, Part 3.

**Taper** — A channel hole profile defect characterized by smooth, monotonic narrowing (or widening) of diameter with depth, without a local extremum. See Chapter 11, Part 5.

**Trim-Etch Cycle** — The repeated process of laterally trimming a protective mask followed by a vertical etch step, used to form the staircase structure one layer pair at a time. See Chapter 13, Part 2.

**Twisting** — A channel hole profile defect characterized by progressive lateral drift of the hole's center axis with depth, strongly amplified by differential charging. See Chapter 11, Part 2.

**Word Line (WL)** — A single horizontal conductive layer acting as the control gate for one memory cell in each string passing through it. See Chapter 1, Part 3.
