# Salt Bridge Comparison — Candidate vs Control

## Project Halo | Phase 4 Result

## Overview

This report compares salt bridge presence near the copper-binding loop region of the candidate enzyme (*Bacillus safensis* laccase, halotolerant) against the control enzyme (*Trametes versicolor* laccase, standard fungal) to test the project hypothesis: that the candidate shows greater structural salt tolerance evidence near its active site, not just at the organism level.

## Method Summary

- Structures: ESMFold predictions (candidate 510 aa, control 519 aa)
- Region of interest: Cupredoxin copper-binding loop for each protein, identified via ESMFold feature activation
  - Candidate loop: LEU 104 - PHE 125
  - Control loop: SER 82 - GLN 104
- Tool: ChimeraX H-Bonds, "Salt bridges only" filter, angle and distance validated (0.4 Å / 20° tolerance), intramodel only
- Salt bridges classified as strong/unconditional (Asp/Glu with Lys/Arg) or conditional (involving Histidine, whose charge is pH-dependent)

## Results

### Candidate — Bacillus safensis (8 unique salt bridges)

| Bridge | Distance range (Å) | Type | Position relative to loop (104-125) |
|---|---|---|---|
| ARG 123 — ASP 124 | 3.539 | Strong | **Inside loop** |
| LYS 75 — ASP 124 | 2.614 | Strong | Touches loop (ASP 124 inside) |
| HIS 424 — ASP 114 | 2.708 | Conditional | Touches loop (ASP 114 inside) |
| LYS 99 — GLU 95 | 2.891 | Strong | Just outside loop, adjacent |
| LYS 71 — GLU 135 | 2.687 | Strong | Outside loop, nearby |
| ARG 299 — ASP 465 | 2.692 - 3.361 | Strong | Distant |
| LYS 464 — ASP 279 | 2.690 - 2.705 | Strong | Distant |
| ARG 487 — ASP 507 | 2.682 - 3.232 | Strong | Distant |

### Control — Trametes versicolor (5 unique salt bridges)

| Bridge | Distance range (Å) | Type | Position relative to loop (82-104) |
|---|---|---|---|
| HIS 86 — ASP 444 | 2.845 | Conditional | Touches loop (HIS 86 inside) |
| HIS 420 — ASP 97 | 2.786 | Conditional | Touches loop (ASP 97 inside) |
| ARG 63 — ASP 116 | 2.679 - 3.132 | Strong | Outside loop, nearby |
| ARG 263 — ASP 444 | 2.661 - 3.180 | Strong | Distant |
| ARG 443 — ASP 244 | 2.857 - 3.099 | Strong | Distant |

## Direct Comparison

| Metric | Control (Trametes) | Candidate (Bacillus) |
|---|---|---|
| Total unique salt bridges | 5 | 8 |
| Strong/unconditional bridges | 3 | 7 |
| Conditional (pH-dependent) bridges | 2 | 1 |
| Strong bridge sitting fully inside the loop | 0 | 1 (ARG123-ASP124) |
| Strong bridges touching the loop | 0 | 1 (LYS75-ASP124) |
| Bridges touching the loop, any type | 2 (both conditional) | 3 (2 strong, 1 conditional) |

## Interpretation

The candidate enzyme shows more total salt bridges than the control, and critically, a genuinely strong, unconditional salt bridge (ARG123-ASP124) sitting directly inside its copper-binding loop region, something the control lacks entirely. The control's only loop-adjacent bridges are both conditional, dependent on Histidine's pH-sensitive charge, a less reliable form of structural stabilization than the Lys/Arg-Asp/Glu bridges dominating the candidate's result.

This finding is consistent with, and supportive of, the project hypothesis: the halotolerant candidate shows a real structural feature, extra salt-bridge stabilization near its active site, that the non-halotolerant control does not show to the same degree.

## Limitations and Caveats

- Both structures are computational predictions (ESMFold), not experimentally solved. All conclusions are structural hypotheses pending further validation, not confirmed biochemical fact.
- Most salt bridges identified in both proteins sit outside the narrowly-defined loop region entirely. This comparison is based on the small subset that touch or fall within the loop boundary, not the full salt bridge count for either protein.
- Sample size is small (one candidate, one control, one loop region each). This is a single comparative data point, not a statistically powered result.
- The candidate protein is a CotA laccase used as a proxy for the originally studied *Bacillus safensis* strain S31, whose exact sequence was not publicly available (see project README for details).

## Next Steps Under Consideration

Docking the target dye (Reactive Black 5) into both structures via CB-Dock2, and checking whether the docked pocket overlaps with these same loop and salt-bridge regions, would add a second, independent line of evidence to this comparison.
