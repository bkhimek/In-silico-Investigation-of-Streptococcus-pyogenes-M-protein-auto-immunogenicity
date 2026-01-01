# Investigation of M-protein auto-immunogenicity

## Overview
Acute rheumatic fever (ARF) is a post-infectious autoimmune complication of
*Streptococcus pyogenes* infection, driven by molecular mimicry between bacterial
antigens and human cardiac proteins. In contrast, post-streptococcal
glomerulonephritis (PSGN) is associated with different emm types and tissue
targets.

This project implements a fully reproducible **in-silico pipeline** to assess
whether **rheumatogenic emm types of the S. pyogenes M-protein show enriched
sequence similarity to human cardiac proteins**, compared with PSGN-associated
emm types.

The analysis focuses on biologically relevant regions of the M-protein and
T-cell–relevant peptide lengths.

---

## Data

### Bacterial sequences
M-protein sequences from six emm types:
- **Rheumatogenic**: emm1, emm3, emm5, emm6, emm24  
- **PSGN-associated**: emm12  

Sequences were curated to:
- remove signal peptides
- focus on the mature N-terminal portion
- align homologous regions across emm types
- extract comparable regions for analysis

### Human target proteins
Cardiac proteins implicated in rheumatic heart disease:
- **MYH7** – β-myosin heavy chain
- **TPM1** – tropomyosin α-1 chain
- **ACTC1** – cardiac α-actin

Only **human** reference sequences (UniProt) were used.

---

## Methods

1. **Sequence curation and alignment**
   - M-protein sequences were aligned using MAFFT.
   - Two comparable N-terminal regions were selected:
     - **Region A** (strictly conserved block)
     - **Region B** (relaxed coverage block with broader alignment retention).

2. **Peptide generation**
   - Overlapping **15-mer peptides** were generated from each region.
   - 15-mers were chosen to reflect typical MHC class II epitope length.

3. **Molecular mimicry scoring**
   - Each M-protein 15-mer was compared against all 15-mers derived from
     human cardiac proteins.
   - A simple identity score (0–15 identical residues) was computed.
   - For each M-protein peptide, the **best matching cardiac peptide** was retained.

4. **Threshold-based analysis**
   - Mimicry was evaluated at similarity thresholds ≥7/15, ≥8/15, and ≥9/15.
   - Hit counts were summarised per emm type and per region.

---

## Key Results

- Mimicry signals were **enriched in rheumatogenic emm types** (emm1, emm6, emm24).
- PSGN-associated **emm12 showed consistently fewer high-identity matches**.
- Differences became most pronounced at **higher similarity thresholds (≥8–9/15)**.
- Region B (relaxed block) showed stronger discrimination than Region A.

These findings are consistent with the hypothesis that **cardiac-directed autoimmunity
in rheumatic fever is driven by selective molecular mimicry**, rather than nonspecific
cross-reactivity.

---

## MHC-II prioritisation (DeepMHCII)

To increase immunological plausibility beyond sequence similarity alone, high-mimicry
peptides were prioritised using **MHC class II binding prediction**.

### Workflow
1. Start from cardiac mimicry candidates (15-mers with identity ≥8/15).
2. Predict MHC-II presentation propensity using a trained **DeepMHCII** model,
   applied to a representative HLA-DRB1 allele panel
   (DRB1_0101, DRB1_0401, DRB1_0701, DRB1_1501).
3. Aggregate predictions across alleles for each peptide
   (e.g. best score and mean score).
4. Rank peptides by mimicry strength (identity_15) and predicted MHC-II score.

### Output
- `results/mimicry_prioritized_mhc2.csv` – ranked peptide list with DeepMHCII scores.
- `results/deepmhcii/pred_*.tsv` – allele-specific prediction outputs.

### Visual summary

The plot below compares overall cardiac mimicry burden (15-mers with identity ≥8/15)
with the subset of mimicry peptides that also score highly in DeepMHCII
(default best score ≥0.35).

![Mimicry vs MHC-II burden](results/figures/burden_mimicry_ge8_mhc2_ge0.35.png)

![Cardiac mimicry (overall, ≥8/15)](results/figures/mimicry_overall_ge8.png)

---

## Reproducibility

- All intermediate and final results are written to the `results/` directory.
- The analysis is implemented as a **script-only pipeline** (`scripts/01–04`),
  enabling deterministic re-runs without manual intervention.
- Environment separation is used for mimicry analysis and DeepMHCII inference.

## Future extensions

Planned or optional extensions include:
- Extension to kidney-associated targets relevant to PSGN.
- Inclusion of additional HLA class II loci (DP, DQ).
- Comparison with non-rheumatogenic emm types as negative controls.
- Integration into automated lab or cloud-based protein engineering platforms.

## Author Krzysztof Giżyński
