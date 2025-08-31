# Runs of Homozygosity (ROH) and the Genomic Inbreeding Coefficient (F_ROH)

**Goal:** quantify individual- and population-level inbreeding from genome-wide genotypes or sequencing by identifying **Runs of Homozygosity (ROH)** and summarizing them as a **genomic inbreeding coefficient** (*F_ROH*).

## 1) What is an ROH?

A **Run of Homozygosity (ROH)** is a **contiguous chromosomal segment** where all informative polymorphic sites are **homozygous**.

- Conceptually: two haplotypes (maternal/paternal) carry **the same alleles** across a stretch of the genome.
- **Boundaries** of a ROH are defined by the first heterozygous SNPs (or missing-data limits) on each side.
- ROHs come in **different sizes** (short/medium/long), reflecting **time since common ancestry**:
  - **Long** ROH → recent common ancestors (consanguinity, strong bottlenecks).
  - **Short** ROH → older events / background LD.

## 2) From ROH to genomic inbreeding: *F_ROH*

Let:
- `nROH` = number of ROH segments in an individual  
- `L_ROH` = average ROH length (Mb)  
- `S_ROH` = **sum of all ROH lengths** in an individual (Mb)  
- `L_GEN` = total **autosomal** genome length considered (Mb)

Then the **genomic inbreeding coefficient** is:
\[
F_{\text{ROH}} = \frac{S_{\text{ROH}}}{L_{\text{GEN}}}
\]

Interpretation: **% of the autosomal genome contained in ROH**. Higher values = higher genomic inbreeding.

## 3) IBD vs IBS and relation to pedigree (F_PED)

- **IBD (Identical by Descent)**: two alleles are copies from a **common ancestor** (what pedigree-based \(F_{\text{PED}}\) targets).
- **IBS (Identical by State)**: alleles look identical but origin is unknown.

**ROH-based methods count homozygosity regardless of origin (IBD + IBS).**  
However, **long ROH** are unlikely to arise by chance → **more likely IBD**.  
Thus, *F_ROH* approximates the genome-wide **autozygosity** and is often more **informative** than \(F_{\text{PED}}\) when pedigrees are shallow/incomplete.

## 4) Calling ROH: key choices & biases

Different methods ≈ different **windows/thresholds**:

- **Window definition**
  - Number of SNPs to define the sliding window.
  - **Max heterozygous SNPs** permitted within a window (to tolerate genotyping error).
  - **Max missing SNPs** permitted.
  - **Minimum ROH length** (in kb/Mb).
- **SNP density**
  - Low-density arrays → require **fewer SNPs** per ROH and **larger minimum length**.
  - High-density arrays/seq → stricter thresholds possible.
- **Genotyping error & missingness**
  - A single miscalled heterozygote can break a ROH.
  - Define small tolerances for **HET** and **MISS** per window.
- **Linkage disequilibrium (LD) & recombination rate**
  - Populations with **high LD** (some livestock) tend to produce **longer background ROH**; set **longer minimum length** to avoid false positives.
  - In **humans** (lower LD), minimum ROH can be shorter.
- **Reference length**
  - Always restrict to **autosomes** when computing *F_ROH* and report the **exact `L_GEN`** used.

> Practical tip: choose thresholds guided by **literature for your species**, perform **sensitivity analysis** (vary parameters), and report them explicitly.

## 5) Typical parameterization (rule-of-thumb)

| Platform | Min SNPs per ROH | Max HET in window | Max MISS in window | Min ROH length |
|---------:|------------------:|------------------:|-------------------:|---------------:|
| 50K SNP array | 30–60 | 1 | 2–3 | 1–2 Mb |
| 700K SNP array | 50–100 | 1 | 2–3 | 0.5–1 Mb |
| WGS (≥10×) | length-driven | allow occasional errors | allow | 0.3–0.5 Mb |

*Adjust for species-specific LD.*

## 6) Computing ROH and F_ROH with PLINK

> PLINK implements a sliding-window ROH caller for SNP-array data.

Example (human-like settings, autosomes only):

```bash
# 1) Basic ROH calling
plink \
  --bfile data/genotypes_autosomes \
  --homozyg \
  --homozyg-window-snp 50 \
  --homozyg-snp 50 \
  --homozyg-kb 1000 \
  --homozyg-density 100 \
  --homozyg-gap 1000 \
  --homozyg-window-het 1 \
  --homozyg-window-missing 2 \
  --homozyg-window-threshold 0.05 \
  --out results/roh_calls

# Outputs:
#   results/roh_calls.hom   (per-ROH segments)
#   results/roh_calls.hom.indiv (per-individual summary: nROH, S_ROH, mean length)

# 2) Compute F_ROH per individual
#    L_GEN must be the autosomal genome length analyzed (e.g., 2,867,000 kb for GRCh38 autosomes)
```
To get 
𝐹
ROH
F
ROH
	​

:

𝐹
ROH
=
KB_HOM
𝐿
GEN (kb)
F
ROH
	​

=
L
GEN (kb)
	​

KB_HOM
	​


where KB_HOM is per individual from *.hom.indiv.

For WGS, prefer length-based approaches (postprocess *.hom) and consider depth/variant QC filters.

7) How to read ROH summaries

Per individual:

nROH ↑ and S_ROH ↑ → more inbreeding.

Distribution by length:

Long ROH (e.g., >8 Mb): recent consanguinity.

Medium ROH (4–8 Mb): intermediate events.

Short ROH (1–4 Mb): ancient background/LD.

Across the population, patterns in nROH and S_ROH help infer history:

Large, outbred population → few, short ROH.

Admixed population → very few ROH, small S_ROH.

Small or isolated population → more ROH, longer average length.

Recent consanguinity → many long ROH.

Bottleneck → increased ROH count; if followed by inbreeding, also longer ROH.

8) ROH islands (population-level signal)

A ROH island is a genomic region with high ROH frequency across individuals.

Often indicates selection (natural or artificial) favoring homozygosity at/near a locus.

Visualization: Manhattan-like plot with chromosomal position (x) vs ROH frequency (y).

Next steps:

Map genes in the island.

Test functional hypotheses (e.g., pathogen resistance, local adaptation).

9) Linking ROH to pedigree and HWE

Inbreeding depression emerges as increased homozygote frequencies (no change in allele frequencies), producing deviations from Hardy–Weinberg equilibrium.

Test deviations with a χ² test (df = 1) using observed vs expected genotype counts.

𝐹
PED
F
PED
	​

 may underestimate inbreeding when pedigrees are shallow/incomplete; F_ROH leverages the realized genomic mosaic.

10) Reporting checklist

Genotyping/seq platform, variant QC thresholds.

ROH calling parameters (window SNPs, max HET/MISS, min length, density, gap).

Autosomes and L_GEN used.

Per-individual: nROH, S_ROH (Mb), L_ROH mean/median, F_ROH.

ROH length classes (short/medium/long) with counts.

Population summaries, ROH-island analysis, and interpretation.

11) Quick example table (per individual)
ID	nROH	S_ROH (Mb)	mean L_ROH (Mb)	F_ROH (= S_ROH / L_GEN)
A01	32	145	4.5	0.0506
A02	6	18	3.0	0.0063
A03	74	410	5.5	0.1430

(Assuming L_GEN = 2,867 Mb autosomes)

12) Key takeaways

F_ROH is the fraction of the genome in ROH and a practical proxy for genomic inbreeding.

Parameter choices matter; match them to platform density and species LD.

Long ROH = recent inbreeding; ROH islands = candidate selection targets.

Combine F_ROH with 
𝐹
PED
F
PED
	​

, HWE tests, and demographic context for robust inference.
