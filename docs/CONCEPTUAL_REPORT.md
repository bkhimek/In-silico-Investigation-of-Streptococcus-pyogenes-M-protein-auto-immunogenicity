# Conceptual Overview & Biological Context

This report explains the biological motivation and high-level context
behind the analysis of *Streptococcus pyogenes* M-protein auto-immunogenicity
using in-silico molecular mimicry and MHC class II prioritisation.

---

## 1. Background — Why this problem matters

*Streptococcus pyogenes* (Group A Streptococcus, Strep A) causes
common human infections such as:
- **pharyngitis (strep throat)**
- **skin infections (impetigo)**

In a subset of cases, bacterial infection is followed by **autoimmune
complications**, most notably:
- **Acute rheumatic fever (ARF)** → rheumatic heart disease
- **Post-streptococcal glomerulonephritis (PSGN)** → kidney damage

Importantly:
- Different bacterial strains (*emm* types) are associated with
  different disease outcomes
- **Rheumatogenic emm types** (often throat-associated) are linked with ARF
- **PSGN-associated emm types** (often skin-associated) show different
  post-infection patterns

The leading hypothesis is **molecular mimicry** — certain bacterial
proteins share sequence or structural similarity with host proteins,
leading to immune cross-reactivity.

---

## 2. The M-protein and emm types

The **M-protein** is:
- a major **surface antigen** of *S. pyogenes*
- highly variable across strains
- encoded by the **emm gene**

Different *emm* types:
- differ especially in the **N-terminal region** of M-protein
- are correlated with **tissue preference** and disease sequelae

This variation makes M-protein an ideal target for studying
**strain-specific auto-immunogenicity**.

---

## 3. What this project asks

This investigation addresses three related questions:

1. Do **rheumatogenic emm types** show more sequence similarity to
   human cardiac proteins than **PSGN-associated types**?
2. Are these similarities concentrated in specific regions of
   the M-protein?
3. Among similar peptides, which are most likely to be presented
   to T cells (i.e. immunogenic)?

---

## 4. Why use in-silico analysis?

In-silico methods enable:
- **rapid hypothesis testing**
- **systematic comparison** across strains
- **prioritisation of candidates** before experimental validation

This workflow does *not* claim proof of causality. Instead, it:
- identifies patterns
- generates testable hypotheses
- narrows down the experimental search space

---

## 5. Key concepts (plain language)

### **Molecular mimicry**
Similarity between microbial and host protein sequences that may
cause immune cross-reactivity.

### **15-mer peptide**
A short peptide of 15 amino acids — typical for presentation
by **MHC class II** molecules to helper T cells.

### **MHC class II**
Proteins on antigen-presenting cells that display peptides to
CD4⁺ T cells. Only peptides that bind MHC-II efficiently can
activate T cells.

### **Pseudosequence (MHC)**
A simplified MHC representation containing only the key amino
acids that contact a peptide. Using pseudosequences speeds up
binding prediction while preserving biological relevance.

---

## 6. High-level conclusions

At a conceptual level, this analysis shows:

- Cardiac mimicry is **not uniform** across *emm* types
- **Rheumatogenic strains** show higher mimicry burden and
  higher-quality matches to cardiac proteins
- Adding **MHC-II binding prediction** helps prioritise
  immunologically plausible mimicry candidates

These insights help bridge sequence similarity with
immunological relevance in a reproducible computational framework.
