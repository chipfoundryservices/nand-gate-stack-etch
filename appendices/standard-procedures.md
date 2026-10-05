# Appendix C: Standard Operating Procedures

This appendix consolidates representative standard operating procedure (SOP) outlines for the three major etch-adjacent processes developed in this book: channel hole etch, staircase trim-etch, and slit etch/word line replacement. These outlines are illustrative, process-flow-level summaries intended to show how the main text's chapter content maps onto an actual production procedure structure; they are not a substitute for tool-specific, fully validated production SOPs.

---

## C.1 Channel Hole Etch SOP Outline

**Scope:** Full-stack channel hole etch, from hard mask open through breakthrough/overetch, per Chapters 2-12.

1. **Incoming wafer verification.** Confirm stack deposition completion, measure incoming wafer bow (Chapter 2, Section 5.1) against specification, verify lithography/hard-mask pattern CD and overlay prior to loading.
2. **Chamber readiness check.** Confirm current chamber seasoning state (Chapter 8, Section 2.3) and cumulative RF hours/wafer count since last dry clean (Chapter 8, Section 3.4) are within qualified range.
3. **Mask open step.** Execute mask-open recipe (Chapter 2, Section 5.2; Chapter 7, Section 5.2) under CF4/CHF3-weighted chemistry, lower-AR-appropriate pressure/power settings.
4. **Bulk etch step(s).** Execute depth-ramped bulk etch recipe (Chapter 7, Section 3.2; Chapter 10, Section 5.1) using C4F6/C4F8+SF6 chemistry blend (Chapter 3, Part 4) with pulsed bias per the duty cycle schedule established in qualification (Chapter 9, Part 3).
5. **Breakthrough/overetch step.** Transition to high stop-layer-selectivity chemistry (Chapter 12, Part 4), monitor endpoint signal (Appendix F) to determine step termination.
6. **Post-etch inspection.** Sample-based cross-sectional CD/profile measurement (Chapter 11, Part 7) and/or non-destructive scatterometry; route to R2R control system (Chapter 15, Section 2.3) for next-lot feedback.
7. **Chamber state update.** Log cumulative RF hours/wafer count; schedule dry clean per Chapter 8, Section 5.2's cadence calculation if threshold reached.

## C.2 Staircase Trim-Etch Cycle SOP Outline

**Scope:** Single trim-etch cycle within the full staircase formation sequence, per Chapter 13.

1. **Cycle readiness check.** Confirm mask remaining thickness is within the budget established in Chapter 13, Section 6.3 for the current cycle number.
2. **Mask trim step.** Execute controlled lateral trim per the qualified trim-rate-consistency recipe (Chapter 13, Section 6.2).
3. **Vertical etch step.** Execute single-layer-pair vertical etch across all currently-exposed steps.
4. **In-line metrology checkpoint** (every N cycles per Chapter 13, Section 7.1). Measure step height/position on sampled test structures; compare against expected cumulative trend.
5. **Drift correction decision.** If systematic drift detected, compute and apply forward-only correction to subsequent cycle parameters (Chapter 13, Section 7.2); no retroactive correction to already-completed steps is possible.
6. **Repeat** steps 1-5 for the full layer-pair count, or until the current mask reaches its replenishment threshold (Chapter 13, Section 6.3).

## C.3 Slit Etch and Word Line Replacement SOP Outline

**Scope:** Full replacement sequence from slit etch through completed metal fill, per Chapter 14.

1. **Slit etch.** Execute trench etch to full stack depth using a recipe tuned for stop-layer selectivity and clearing rather than sidewall smoothness (Chapter 14, Section 1.3).
2. **Pre-removal inspection.** Verify slit clearing and dimensional specification via sampled cross-section.
3. **Sacrificial nitride removal.** Execute hot phosphoric acid wet process (Chapter 14, Part 2) for the qualified duration, including overetch margin per Chapter 14, Section 5.3's compounding-time consideration; verify complete removal across full block width via characterized removal-rate model and/or direct inspection (Chapter 14, Section 2.4).
4. **Minimum-support-interval tracking.** Log elapsed time in the unsupported structural interval (Chapter 14, Part 4); flag for expedited handling if approaching the qualified maximum unsupported duration.
5. **Barrier/metal fill.** Execute ALD TiN barrier deposition followed by CVD tungsten fill (Chapter 14, Section 3.1), through the same slit access path.
6. **Post-fill inspection.** Verify void-free fill via sampled cross-section, particularly at the lateral extremity farthest from the slit (Chapter 14, Section 3.2-3.3); measure word line resistance uniformity across block width.
7. **Structural integrity verification.** Confirm no block tilting, sagging, or wafer-level warpage interaction occurred during the unsupported interval (Chapter 14, Part 4).

---

*These outlines summarize the process flow logic developed across Chapters 2-14; actual production SOPs include additional tool-specific parameter values, safety procedures, and documentation requirements beyond this book's scope.*
