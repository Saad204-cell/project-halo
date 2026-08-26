# Project Halo

**In silico screening of halotolerant laccases for azo-dye decolorization in textile wastewater**

## Overview

Textile dyeing effluent in industrial hubs like Faisalabad, Pakistan contains synthetic azo dyes alongside very high salt concentrations. Standard laccase enzymes used for biological dye decolorization work well in clean water but often lose activity in high-salinity conditions, creating a gap between lab-demonstrated dye treatment and real-world effluent treatment performance.

This project investigates whether a halotolerant bacterial laccase (*Bacillus safensis*) shows structural features, specifically salt bridge density near its copper-binding active site, that could explain greater resilience to high salt compared to a standard, non-halotolerant fungal laccase (*Trametes versicolor*, used as the control).

**This is a computational screening and characterization project, not a wet-lab validated discovery.** Any findings here would require experimental confirmation before real-world application. That limitation is stated plainly throughout, not glossed over.

## Hypothesis

Does the candidate laccase (*Bacillus safensis*) show greater surface acidic residue density and salt bridge count near its copper-binding sites, compared to the control laccase (*Trametes versicolor*), consistent with structural (not just organismal) salt tolerance?

## Background

Halotolerance at the organism level and halotolerance at the enzyme level are not the same thing. A bacterium can survive high salt through cellular machinery (ion pumps, compatible solutes, cell wall adaptations) while its individual enzymes, once outside the cell, may still lose activity in the same conditions. This project screens specifically at the enzyme structure level, independent of whatever the source organism's own survival strategy might be.

## Methods

| Step | Tool | Purpose |
|---|---|---|
| Sequence retrieval | UniProt / NCBI | Candidate and control protein sequences |
| Structure prediction | ESMFold | 3D structure and per-residue confidence (pLDDT) |
| Active site identification | ESMFold feature annotation | Locating copper-binding (T1/T2/T3) regions |
| Docking | CB-Dock2 | Testing dye (Reactive Black 5) binding to each structure |
| Structural analysis | UCSF ChimeraX | Electrostatic surface mapping, salt bridge identification and validation |

All tools used are free and web/desktop accessible. No local GPU or paid compute used.

## Status

**In progress.** Currently completing structural comparison of candidate and control near the copper-binding regions. See `/results` for data collected so far.

## Repository Structure

```
/data/       Protein sequences and PDB structure files (candidate, control)
/results/    Analysis outputs: salt bridge reports, docking scores, structure screenshots
/notes/      Working notes, tool usage documentation, method reference
README.md    This file
```

## Known Limitations

- The exact laccase sequence for *Bacillus safensis* strain S31 (the specific strain characterized in prior published work) was not available in public databases. The original study deposited only a 16S rRNA sequence (used for species identification), not the laccase gene itself. A closely related CotA laccase from the same species is used as a proxy candidate, and this substitution is noted wherever relevant.
- All structural predictions are computational (ESMFold), not experimentally solved structures. Confidence scores are reported alongside all structural claims.
- This project does not include wet-lab expression, purification, or activity assays. All conclusions are structural/computational hypotheses, not confirmed biochemical results.

## Background Reading

This project's methodology and reasoning are also documented as a public series on [LinkedIn], including mistakes, corrections, and open questions encountered along the way.

## Author

Muhammad Saad Javed — BS Biotechnology, Riphah International University, Faisalabad, Pakistan
