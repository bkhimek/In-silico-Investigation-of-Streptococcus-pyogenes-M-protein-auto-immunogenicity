# Step-by-Step Technical Workflow

This document describes the computational pipeline used to investigate
molecular mimicry between *Streptococcus pyogenes* M-protein peptides
and human cardiac proteins, and to prioritise immunogenic candidates
via MHC class II binding prediction.

---

## Step 1 — Input data

**Bacterial sequences**
- M-protein sequences from multiple emm types
  - Selected to represent:
    - rheumatogenic strains
    - PSGN-associated strains

**Human target proteins**
- Cardiac proteins implicated in rheumatic heart disease:
  - *MYH7* (β-myosin heavy chain)
  - *TPM1* (tropomyosin)
  - *ACTC1* (cardiac actin)

---

## Step 2 — Sequence curation and alignment

**Why this matters**
- M-proteins differ in length and composition
- Direct comparison requires homologous regions

**What was done**
- Signal peptides removed
- Mature M-protein sequences aligned using MAFFT
- Two comparable N-terminal regions defined:
  - Region A — highly conserved
  - Region B — broader but biologically relevant

---

## Step 3 — Peptide generation

From each region:
- Overlapping **15-mer peptides** were generated
- Sliding window with step size 1 ensures exhaustive coverage

**Why 15-mers?**
- Standard length for MHC class II epitope presentation
- Captures T-cell–relevant information

---

## Step 4 — Molecular mimicry scoring

For each M-protein 15-mer:
- Compared against all 15-mers from cardiac proteins
- Similarity measured as identity score (0–15)
- Only the best matching cardiac peptide retained

This produces:
- A conservative estimate of maximal mimicry per peptide

---

## Step 5 — Threshold-based analysis

Similarity thresholds applied:
- ≥7/15 → permissive
- ≥8/15 → moderate
- ≥9/15 → high stringency

Counts were summarised:
- per emm type
- per region (A vs B)

This reveals strain-specific and region-specific trends.

---

## Step 6 — Candidate selection for immunological prioritisation

From mimicry results:
- Peptides with identity ≥8/15 selected
- Duplicates collapsed
- Provenance retained (emm type, region, target protein)

This produces a **candidate peptide list**.

---

## Step 7 — MHC-II binding prediction (DeepMHCII)

**Why this step**
- Sequence similarity alone does not imply immunogenicity
- Peptides must bind MHC-II to activate T cells

**Approach**
- Trained DeepMHCII neural network used
- Predictions run for multiple HLA-DRB1 alleles
- MHC pseudosequences used as model input

**Outputs**
- Binding score per peptide per allele

---

## Step 8 — Aggregation and ranking

For each peptide:
- Best MHC-II score across alleles
- Mean score across alleles
- Combined with mimicry score

Peptides ranked by:
1. mimicry strength
2. MHC-II binding potential

---

## Step 9 — Visualisation

Bar plots generated to compare:
- total mimicry burden per emm type
- MHC-II–prioritised mimicry burden

This makes strain differences immediately interpretable.

---

## Step 10 — Reproducibility

The final workflow:
- Uses script-only execution (no notebooks required)
- Separates environments (analysis vs prediction)
- Writes all outputs to `results/`
