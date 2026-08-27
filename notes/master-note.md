# Master Note — Project Halo

A running record of core concepts, corrections, and terminology built up over the course of this project. Written to track actual understanding, including mistakes made and fixed along the way, not just final conclusions.

## Core Enzyme Biology

**Laccase mechanism**: Laccases are multicopper oxidase enzymes. They oxidize a substrate (in this project, azo dyes) by stripping electrons from it, then pass those electrons through the protein to reduce molecular oxygen fully to water. This is a clean 4-electron reduction with no toxic partial-reduction byproducts (like superoxide or peroxide) released along the way.

**The three copper sites**:
- **T1**: where the substrate is actually oxidized. Gives laccases their blue color.
- **T2 and T3**: form a trinuclear cluster (T2 is one copper, T3 is a pair) where the collected electrons ultimately reduce oxygen to water.
- Electron path: dye → T1 → through the protein → T2/T3 cluster → oxygen reduced to water.

**Cupredoxin domains**: the structural protein fold (beta-sheet heavy) that holds the copper sites in a stable geometric arrangement. Domains are the scaffold; copper sites are the functional parts within that scaffold. Laccases are built from 2 or 3 cupredoxin-like domains depending on organism (fungi/insects/coral: 3 domains; bacteria/mammals: 2 domains).

**Correction made**: domain count and copper site count are not the same axis. A 2-domain bacterial laccase still has all three copper site types (T1, T2, T3); it just assembles them differently, sometimes compensating structurally by functioning as a trimer.

## Organism-Level vs Enzyme-Level Halotolerance

**Correction made**: a halotolerant organism does not automatically mean its enzymes are individually salt-tolerant. A bacterium can survive high salt through cellular machinery (ion pumps, cell wall remodeling, compatible solutes like glycerol and glutamate) while its enzymes, once outside the cell and acting alone, may still lose activity in the same salt conditions. This project screens specifically at the enzyme structure level, independent of the source organism's own survival strategy.

**Real example encountered**: Bacillus safensis strain S31 (halotolerant organism) showed its own laccase drop to roughly 20% relative activity at 0.1 M NaCl in published data, despite the organism itself thriving in much higher salinity. Survival and enzymatic function are separate questions.

## Salt Tolerance at the Protein Structure Level

Why salt normally hurts a protein: high salt concentration floods the solution with ions that compete with the protein for the water molecules forming its hydration shell, and interferes with internal charged-residue interactions (salt bridges) that help hold the fold together. Enough disruption denatures the protein or distorts its active site.

How salt-tolerant proteins resist this:
- Excess acidic surface residues (Glu, Asp) holding a tighter hydration shell
- More or stronger salt bridges specifically positioned to remain stable under high ionic strength
- Fewer exposed hydrophobic patches, reducing aggregation risk
- Sometimes higher intrinsic flexibility

**Salt bridge, defined**: an attractive interaction between a negatively charged residue (Asp, Glu) and a positively charged residue (Lys, Arg), generally counted as structurally real when the distance between their charged atoms is under approximately 4 Angstroms. Same-charge pairs (two acidic or two basic residues) do not attract and cannot form a salt bridge.

**Histidine, a special case**: conditionally charged depending on surrounding pH (pKa near neutral pH). Salt bridges involving Histidine are treated as conditional/weaker evidence compared to unconditional Asp/Glu-Lys/Arg pairs.

## Method Lessons

**Structure prediction confidence (pLDDT) is not uniform trust**: low confidence in a predicted region can mean either the model lacks information, or the region is genuinely biologically flexible/disordered (e.g. unprocessed precursor regions like pre-proinsulin before cleavage). Cross-checking two independent tools (ESMFold vs AlphaFold) on the same protein revealed real disagreement in confident regions, teaching that no single tool's confidence score should be trusted blind.

**Docking score alone is not enough**: a high Vina score from CB-Dock2 does not confirm a biologically real binding site. Always cross-check the top-ranked pocket's contact residues against known/expected functional residues. Demonstrated directly: NAG-lysozyme toy run gave a plausible-looking score at a pocket that did not include the real catalytic residues (Glu35, Asp52); Indinavir-HIV protease gave both a strong score and correct catalytic residue match (Asp25), confirming what a trustworthy result looks like by contrast.

**Distance alone does not confirm a real salt bridge; angle matters too**: a raw distance-only search (ChimeraX contacts command) produces false positives that fail proper geometric validation. ChimeraX's dedicated H-Bonds tool, with "salt bridges only" filter and angle+distance tolerance, is the validated method. A manual distance-only count of 17 candidate pairs on the control structure was reduced to 5 real, validated salt bridges once properly checked.

**Watch for duplicate/overlapping models in the same session**: an accidentally duplicated structure occupying identical coordinates can cause spatial proximity searches to return nearly the entire protein instead of a real local cluster. Always confirm "1 model selected" in the log before trusting a zone/proximity search result.

## Known Project Limitations (stated honestly, not hidden)

- The exact laccase sequence for Bacillus safensis strain S31 was not publicly available; the original characterization paper deposited only a 16S rRNA sequence (species identification), not the enzyme gene. A closely related CotA laccase from the same species is used as a proxy candidate.
- All structural work is computational (ESMFold predictions), not experimentally solved structures.
- No wet-lab expression, purification, or activity assay work is part of this project. All findings are structural/computational hypotheses requiring future experimental validation.
- Most salt bridges found in both candidate and control structures sit outside the narrowly-defined copper-binding loop region; only a small subset directly touch or fall within it. This is stated explicitly rather than smoothed over.

## Glossary (plain language, built as terms came up)

- **Residue**: one amino acid unit in a protein chain
- **Acidic residue**: Aspartate (Asp/D) or Glutamate (Glu/E), negatively charged
- **Basic residue**: Lysine (Lys/K) or Arginine (Arg/R), positively charged
- **pLDDT**: per-residue confidence score from a structure prediction tool (0-1 or 0-100 scale depending on tool)
- **Vina score**: docking tool's predicted binding strength in kcal/mol; more negative indicates stronger predicted binding
- **HETATM / HOH**: PDB file codes for non-protein atoms; HOH specifically denotes a water molecule
