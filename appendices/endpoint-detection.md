# Appendix F: Endpoint Detection Calibration

This appendix develops endpoint detection methodology for multi-layer stack etch in more detail than the main text's references in Chapter 12, Section 4.3 and Chapter 15, Section 2.1, consolidating the practical calibration approach used to determine when a channel hole, staircase, or slit etch step should terminate.

---

## F.1 Why Endpoint Detection Is Necessary

Chapter 12, Section 4.1-4.3 established that the breakthrough/overetch step requires bounded, not indefinite, overetch time to balance full-wafer clearing against stop-layer damage. A fixed, conservatively long timed overetch would guarantee clearing but at the cost of excessive stop-layer damage at locations that cleared earliest; a fixed, conservatively short timed overetch would protect the stop layer but risk incomplete clearing at the slowest-clearing locations. Endpoint detection resolves this by monitoring a real-time process signal that changes character when the etch front reaches the target transition, allowing overetch duration to be set dynamically per-wafer rather than via a fixed worst-case assumption.

## F.2 Optical Emission Spectroscopy (OES) Endpoint

**Mechanism.** OES monitors specific emission wavelengths characteristic of species present in the plasma as a byproduct of the current etch reaction. As the etch front transitions from one material to another (e.g., from the final sacrificial nitride layer to the underlying stop-layer material, Chapter 2, Section 5.1), the relative population of etch byproduct species shifts, producing a measurable change in emission intensity at wavelengths associated with the materials involved.

**Representative monitored species/wavelengths for this book's chemistry system:**

| Species | Approx. Wavelength | Relevance |
|---|---|---|
| CN (from nitride etch, carbon-nitrogen byproduct interaction) | ~388 nm | Nitride-specific signal, drops as nitride clears |
| SiF (from oxide/nitride Si-F byproduct chemistry) | ~440 nm | General Si-containing-film signal |
| N2/N2+ (from nitride nitrogen release, Chapter 4, Section 2.2) | ~337 nm, ~391 nm | Nitride-specific signal |
| CO/CO2-related bands | Various, UV-visible range | Polymer/carbon chemistry activity indicator |

**Calibration procedure outline:**
1. Run a representative, fully-characterized wafer (known-good clearing behavior from destructive cross-section verification) while recording full-spectrum or targeted-wavelength OES data throughout the etch.
2. Identify the specific wavelength(s) showing the clearest, most reproducible intensity transition coinciding with the known clearing depth/time from the cross-section reference.
3. Establish a trigger threshold (intensity change magnitude and/or rate-of-change criterion) on the selected wavelength(s) that reliably identifies this transition across multiple characterization wafers.
4. Validate the calibrated trigger across a statistically meaningful sample of production-representative wafers before deploying as the production overetch-termination criterion.

## F.3 Why Dense Feature Arrays Complicate OES-Based Endpoint

Chapter 6, Section 2.3 noted that local gas consumption scales with feature density. A direct consequence for endpoint detection: the OES signal transition associated with a given fraction of channel holes reaching the stop layer is a *statistical, averaged* signal across the full population of holes on the wafer, not a signal from any single hole. In regions of differing feature density (dense array vs. sparse staircase/peripheral regions, Chapter 1, Section 7), the aggregate OES signal is weighted toward whichever region dominates total etched area, meaning OES endpoint calibration implicitly assumes a representative, production-typical feature density distribution, and recalibration is required if that distribution changes significantly (e.g., a layout redesign altering the dense-array-to-peripheral-area ratio).

## F.4 Electrical/Impedance-Based Endpoint Signals

**Mechanism.** As plasma impedance characteristics shift with changing etch byproduct composition (analogous reasoning to OES, but measured via RF electrical characteristics rather than optical emission), RF matching network tuning position or reflected power can also exhibit a detectable signature at material transitions, providing a complementary or backup endpoint signal to OES.

**When this method is preferred.** Electrical/impedance-based endpoint signals can be useful when optical access (viewport placement, Chapter 6, Section 5.1) is limited, or as a cross-check against OES-based detection to improve detection confidence through signal redundancy, particularly valuable given the statistical/averaged nature of the signal discussed in Section F.3.

## F.5 Layer-Transition Endpoint for Staircase Trim-Etch Cycles

Beyond the channel hole's single bottom-of-stack endpoint, staircase trim-etch cycles (Chapter 13, Part 2) can similarly benefit from per-cycle endpoint detection, confirming that each cycle's single-layer-pair vertical etch has reached the next oxide/nitride interface (rather than relying solely on a fixed, timed etch step per cycle), which, per Chapter 13, Section 3.1's compounding error discussion, can help bound the per-cycle etch-depth error contribution to the overall compounding error budget, complementing the in-line dimensional metrology checkpoints discussed in Chapter 13, Section 7.1.

## F.6 Endpoint Signal Calibration Maintenance

Because chamber conditioning state (Chapter 8) and consumable component wear (Chapter 8, Section 1.3) can gradually shift baseline OES intensity and background signal levels, endpoint detection trigger thresholds calibrated in Section F.2 must be periodically reverified against current chamber state, typically incorporated into the same chamber matching and drift characterization procedures discussed in Chapter 6, Section 5.3 and Chapter 8, Part 4, rather than treated as a permanently fixed calibration performed once and never revisited.

---

*This appendix summarizes endpoint detection methodology referenced throughout the main text. Specific wavelength selection, threshold values, and calibration procedures are tool- and process-specific and must be established through the empirical procedure outlined in Section F.2 for each production reactor and recipe combination.*
