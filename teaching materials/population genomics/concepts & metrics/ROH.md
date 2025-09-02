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
$$
F_{\text{ROH}} = \frac{S_{\text{ROH}}}{L_{\text{GEN}}}
$$

Interpretation: **% of the autosomal genome contained in ROH**. Higher values = higher genomic inbreeding.

## 3) # IBD vs IBS and Relation to Pedigree

- **IBD (Identical by Descent)**: two alleles are copies from a common ancestor  
  → this is what pedigree-based inbreeding coefficient ($F_{\text{PED}}$) targets.  

- **IBS (Identical by State)**: alleles look identical, but their origin is unknown.  

- **ROH-based methods** count homozygosity regardless of origin (**IBD + IBS**).  
  - **Short ROH** can arise by chance → may reflect IBS.  
  - **Long ROH** are unlikely to arise randomly → more likely IBD.  

Thus, **$F_{\text{ROH}}$** approximates the genome-wide autozygosity and is often more informative than **$F_{\text{PED}}$** when pedigrees are shallow or incomplete.


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
### ## Computing $F_{\text{ROH}}$

$$
F_{\text{ROH}} = \frac{\mathrm{KB\_HOM}}{L_{\text{GEN (kb)}}}
$$

- **KB_HOM**: total length of homozygous segments per individual (from `*.hom.indiv`).  
- **$L_{\text{GEN (kb)}}$**: total genome length in kilobases.  

### Notes
- For **whole-genome sequencing (WGS)**, it is recommended to use **length-based approaches** (post-processing `*.hom` files).  
- Apply **depth and variant quality filters** to reduce false positives in ROH detection.


### 7) How to read ROH summaries

**Per individual**
- `nROH` ↑ and `S_ROH` ↑ → more inbreeding.

**Distribution by length**
- **Long ROH** (e.g., > 8 Mb): recent consanguinity.  
- **Medium ROH** (4–8 Mb): intermediate events.  
- **Short ROH** (1–4 Mb): ancient background/LD.

**Across the population**
- **Large, outbred population** → few, short ROH.  
- **Admixed population** → very few ROH, small `S_ROH`.  
- **Small or isolated population** → more ROH, longer average length.  
- **Recent consanguinity** → many long ROH.  
- **Bottleneck** → increased ROH count; if followed by inbreeding, also longer ROH.

### 8) ROH islands (population-level signal)

A **ROH island** is a genomic region with **high ROH frequency** across individuals.

- Often indicates **selection** (natural or artificial) favoring homozygosity at/near a locus.
- **Visualization:** Manhattan-like plot with chromosomal position (x) vs ROH frequency (y).

**Next steps**
- Map genes in the island.  
- Test functional hypotheses (e.g., pathogen resistance, local adaptation).

# Linking ROH, Pedigree, and Hardy–Weinberg Equilibrium

## Inbreeding and HWE

Inbreeding increases the probability that two alleles at a locus are **identical by descent (IBD)**.  
This does **not change allele frequencies**, but it does increase the frequency of **homozygotes** and decrease the frequency of **heterozygotes**.  

As a result, inbreeding produces **deviations from Hardy–Weinberg equilibrium (HWE)**:

- Expected genotype frequencies under HWE:  
  - $p^2$, $2pq$, $q^2$  
- With inbreeding coefficient $F$:  
  - Homozygotes increase by factor $(1 + F)$  
  - Heterozygotes decrease by factor $(1 - F)$  

These deviations can be formally tested using a **$\chi^2$ test (df = 1)** that compares **observed vs expected genotype counts**.

## Pedigree vs Genomic Inbreeding Estimates

- **$F_{\text{PED}}$** (pedigree-based):  
  - Estimates *expected autozygosity* based on known pedigree structure.  
  - Underestimates inbreeding when pedigrees are **shallow or incomplete**.  

- **$F_{\text{ROH}}$** (ROH-based):  
  - Captures *realized genomic autozygosity* by directly measuring homozygous tracts.  
  - Reflects the actual recombination and inheritance mosaic across the genome.  
  - Often more informative than $F_{\text{PED}}$ in real populations.

## Computing $F_{\text{ROH}}$

$$
F_{\text{ROH}} = \frac{\mathrm{KB\_HOM}}{L_{\text{GEN (kb)}}}
$$

- **KB_HOM**: total length of homozygous runs per individual (from `*.hom.indiv`).  
- **$L_{\text{GEN (kb)}}$**: total autosomal genome length in kilobases.  

### Practical Notes
- For **whole-genome sequencing (WGS)**:
  - Use **length-based ROH approaches** (post-process `*.hom` files).  
  - Apply **depth and variant QC filters** to avoid false ROH calls.  

## Reporting Checklist for ROH Studies

When reporting ROH analyses, include:

1. **Genotyping/sequencing platform** and **variant QC thresholds**.  
2. **ROH calling parameters**:  
   - Window size (number of SNPs)  
   - Maximum allowed heterozygotes/missing sites  
   - Minimum ROH length  
   - SNP density thresholds  
   - Allowed gaps between SNPs  
3. **Autosomes and genome length ($L_{\text{GEN}}$)** used in calculations.  
4. **Per-individual statistics**:  
   - Number of ROH (nROH)  
   - Total ROH length ($S_{\text{ROH}}$, in Mb)  
   - Mean/median ROH length ($L_{\text{ROH}}$)  
   - $F_{\text{ROH}}$  
5. **ROH length classes** (short / medium / long) with counts.  
6. **Population summaries** and **ROH-island analysis** (regions recurrently autozygous across individuals).  

## Take-Home Message

- Inbreeding shifts populations away from HWE, **increasing homozygosity**.  
- Pedigree-based estimates ($F_{\text{PED}}$) capture expected autozygosity, but can miss hidden relatedness.  
- ROH-based estimates ($F_{\text{ROH}}$) directly measure realized genomic homozygosity, often giving a more accurate picture.  
- Proper reporting of methods, QC, and ROH statistics is essential for reproducibility and interpretation.
