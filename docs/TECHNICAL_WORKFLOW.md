Step-by-step technical explanation
Title:
Step-by-step in-silico workflow for M-protein molecular mimicry and MHC-II prioritisation
Step 1 — Input data
Bacterial sequences
•	M-protein sequences from multiple emm types
•	Selected to represent:
o	rheumatogenic strains
o	PSGN-associated strains
Human target proteins
•	Cardiac proteins implicated in rheumatic heart disease:
o	MYH7 (β-myosin heavy chain)
o	TPM1 (tropomyosin)
o	ACTC1 (cardiac actin)
________________________________________
Step 2 — Sequence curation and alignment
Why this matters:
•	M-proteins differ in length and composition
•	Direct comparison requires homologous regions
What was done:
•	signal peptides removed
•	mature M-protein sequences aligned using MAFFT
•	two comparable N-terminal regions defined:
o	Region A — highly conserved
o	Region B — broader but biologically relevant
________________________________________
Step 3 — Peptide generation
From each region:
•	overlapping 15-mer peptides were generated
•	sliding window with step size 1
•	ensures exhaustive coverage of potential epitopes
Why 15-mers:
•	standard length for MHC-II presentation
•	captures T-cell–relevant information
________________________________________
Step 4 — Molecular mimicry scoring
For each M-protein 15-mer:
•	compared against all 15-mers from cardiac proteins
•	similarity measured as identity score (0–15)
•	only the best matching cardiac peptide retained
This produces:
•	a conservative estimate of maximal mimicry per peptide
________________________________________
Step 5 — Threshold-based analysis
Similarity thresholds applied:
•	≥7/15 → permissive
•	≥8/15 → moderate
•	≥9/15 → high stringency
Counts were summarised:
•	per emm type
•	per region (A vs B)
This reveals strain-specific and region-specific trends.
________________________________________
Step 6 — Candidate selection for immunological prioritisation
From mimicry results:
•	peptides with identity ≥8/15 selected
•	duplicates collapsed
•	provenance retained (emm type, region, target protein)
This produces a candidate peptide list.
________________________________________
Step 7 — MHC-II binding prediction (DeepMHCII)
Why this step:
•	sequence similarity alone does not imply immunogenicity
•	peptides must bind MHC-II to activate T cells
Approach:
•	trained DeepMHCII neural network used
•	predictions run for multiple HLA-DRB1 alleles
•	MHC pseudosequences used as model input
Outputs:
•	binding score per peptide per allele
________________________________________
Step 8 — Aggregation and ranking
For each peptide:
•	best MHC-II score across alleles
•	mean score across alleles
•	combined with mimicry score
Peptides ranked by:
1.	mimicry strength
2.	MHC-II binding potential
________________________________________
Step 9 — Visualisation
Bar plots generated to compare:
•	total mimicry burden per emm type
•	MHC-II–prioritised mimicry burden
This makes strain differences immediately interpretable.
________________________________________
Step 10 — Reproducibility
The final workflow:
•	uses script-only execution (no notebooks required)
•	separates environments (analysis vs prediction)
•	writes all outputs to results/
________________________________________
PART 2 — Moving the project to GitHub (step-by-step)
This is very straightforward now.
________________________________________
1️⃣ Decide what to include (recommended)
Include:
README.md
scripts/
analysis/        (optional, if you want to show development)
results/figures/
results/*.csv
docs/            (put the two reports here)
Do not include:
•	conda environments
•	large temporary files
•	raw tool binaries
________________________________________
2️⃣ Initialise Git (if not already)
From project root:
cd ~/projects/M_protein_autoimmunogenicity
git init
________________________________________
3️⃣ Add a .gitignore
Create:
nano .gitignore
Paste:
# environments
.env
.venv
conda_envs/

# Python cache
__pycache__/
*.pyc

# OS files
.DS_Store
Thumbs.db

# Large intermediates (optional)
*.mafft.fasta
________________________________________
4️⃣ Add and commit
git add README.md scripts/ results/figures/ results/*.csv docs/
git commit -m "Add molecular mimicry and DeepMHCII prioritisation pipeline"
________________________________________
5️⃣ Create GitHub repo
On GitHub:
1.	New repository
2.	Name: M_protein_autoimmunogenicity
3.	Do not initialise with README (you already have one)
Then link it:
git remote add origin https://github.com/<your-username>/M_protein_autoimmunogenicity.git
git branch -M main
git push -u origin main


