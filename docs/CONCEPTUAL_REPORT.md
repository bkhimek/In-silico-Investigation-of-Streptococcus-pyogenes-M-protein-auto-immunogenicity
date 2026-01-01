REPORT  — Broad context & biological rationale
Title:
Investigating Streptococcus pyogenes M-protein auto-immunogenicity using in-silico molecular mimicry and MHC-II prioritisation
1. Background: why this problem matters
Streptococcus pyogenes (Group A Streptococcus, Strep A) causes common infections such as:
•	pharyngitis (strep throat)
•	skin infections (impetigo)
In a subset of cases, infection is followed by autoimmune complications, most notably:
•	Acute rheumatic fever (ARF) → rheumatic heart disease
•	Post-streptococcal glomerulonephritis (PSGN) → kidney damage
Importantly:
•	Different bacterial strains (emm types) are associated with different outcomes
•	ARF is linked mainly to throat-associated, rheumatogenic emm types
•	PSGN is more often associated with skin-associated emm types
The leading hypothesis is molecular mimicry:
parts of bacterial proteins resemble host proteins closely enough that the immune system attacks both.
________________________________________
2. The M-protein and emm types
The M-protein:
•	is a major surface protein of S. pyogenes
•	is highly variable between strains
•	is encoded by the emm gene
Different emm types:
•	differ primarily in their N-terminal region
•	are strongly associated with tissue tropism and disease outcome
This makes the M-protein an ideal candidate for studying strain-specific auto-immunogenicity.
________________________________________
3. What this project asks
This project asks three connected questions:
1.	Do rheumatogenic emm types show more sequence similarity to human cardiac proteins than PSGN-associated types?
2.	Are these similarities concentrated in specific regions of the M-protein?
3.	Among similar peptides, which are most likely to be presented to T cells (i.e. truly immunogenic)?
________________________________________
4. Why in-silico analysis?
In-silico approaches allow:
•	rapid hypothesis testing
•	systematic comparison across strains
•	prioritisation of candidates before wet-lab work
This workflow does not claim causality — instead, it:
•	identifies patterns
•	generates testable hypotheses
•	reduces the search space for experimental validation
________________________________________
5. Key concepts (plain language)
Molecular mimicry
Similarity between microbial and host protein sequences that can lead to immune cross-reactivity.
15-mer peptide
A short stretch of 15 amino acids. This length is typical for peptides presented by MHC class II molecules to CD4⁺ T cells.
MHC class II
Proteins on antigen-presenting cells that display peptides to helper T cells. Only peptides that bind MHC-II can trigger T-cell responses.
Pseudosequence (MHC)
A reduced representation of an MHC molecule:
•	instead of using the full MHC protein sequence
•	only key amino acids that contact the peptide are retained
This dramatically simplifies and speeds up binding prediction models.
________________________________________
6. High-level conclusions
At a conceptual level, this workflow shows that:
•	cardiac mimicry is not uniform across emm types
•	rheumatogenic strains show higher-burden and higher-quality mimicry
•	adding MHC-II prediction refines mimicry into immunologically plausible candidates
________________________________________
________________________________________
