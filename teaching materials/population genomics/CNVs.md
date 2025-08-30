# Copy Number Variations (CNVs) – Definitions, Detection, and Applications
## 1. Definition

- **Redon et al. (2006):**  
  A DNA segment that is **≥1 kb** and present at variable copy number compared with a reference genome.  

- **Lee et al. (2008):**  
  Intra-specific **gains or losses of more than 1 kb** of genomic DNA.  

### Characteristics
- Usually occur **in tandem** on the same haplotype (copies gained or lost together).  
- Often consist of **tandem repeats** (local duplications), not genome-wide repeats.  
- Difficult to detect because duplicated sequences are **identical**, complicating mapping.  
- In terms of **nucleotide content**, CNVs represent a larger class of polymorphism compared to SNPs.  

## 2. Platforms for CNV Detection

### 2.1 Array Comparative Genomic Hybridization (aCGH)
- Based on **microarray probes** hybridizing to DNA.  
- Two types of arrays:
  1. **Whole genome tilepath arrays** (BAC clones).  
  2. **Oligonucleotide arrays** (e.g., NimbleGen, Agilent).  

- Workflow:  
  - Label reference and test DNA with different fluorophores (e.g., red/green).  
  - Co-hybridize on the array.  
  - Measure the **log₂ ratio** of signals:  
    - log₂ ratio = 0 → equal copy number.  
    - log₂ ratio > 0 → gain in test DNA.  
    - log₂ ratio < 0 → loss in test DNA.  

- Limitations:  
  - Resolution depends on probe density (e.g., 1 probe every 10–50 kb).  
  - Cannot precisely define CNV boundaries.  
  - Must mask repetitive regions.  

### 2.2 SNP Arrays (Affymetrix, Illumina)
- Originally designed for **SNP genotyping**, but signal intensity can also reveal CNVs.  
- Use **comparative intensity analysis** of SNPs.  
- Limitations:  
  - Coverage is incomplete (arrays not designed for CNVs).  
  - Higher error rates (false positives/negatives).  

### 2.3 Next-Generation Sequencing (NGS)
- Provides **genome-wide CNV detection**.  
- Requires **high sequencing depth** for accurate copy number estimation.  
- Approaches:
  - **Exome sequencing** → reduced representation, focused on coding regions.  
  - **Short-read platforms** → coverage depth and paired-end mapping used to infer CNVs.  
  - **Long-read platforms** → can directly span CNVs, resolving breakpoints.  

## 3. Case Studies and Applications

- **Goat experiment (aCGH with cattle genome as reference):**  
  - CNVs detected in the *agouti* gene, associated with **coat color**.  
  - Demonstrated cross-species probe design when reference genome was unavailable.  

- **Sex chromosome CNVs:**  
  - Example: co-hybridization of male vs female DNA reveals loss on X chromosome in XY individuals.  
  - Applications in cytogenetics (e.g., **Klinefelter, Turner syndromes**).  

- **KIT locus (pig pigmentation):**  
  - CNV in the KIT gene explains white coat phenotype (e.g., “Peppa Pig” breed).  
  - CNV disrupts melanoblast migration, leading to patches/loss of pigmentation.  


## 4. Technical Considerations

- **Resolution**: depends on probe density or sequencing depth.  
- **Normalization**: GC content can bias results (e.g., GC waves); computational correction required.  
- **Reference choice**: essential for comparative methods (e.g., aCGH, SNP arrays).  
- **Relative vs absolute quantification**:  
  - aCGH → relative CNV (sample vs reference DNA).  
  - High-depth WGS → potential for absolute CNV calling.  

## 5. Summary

- CNVs = gains or losses of large DNA segments (≥1 kb).  
- Detection methods:  
  - **aCGH** → first platform, still widely used, complements cytogenetics.  
  - **SNP arrays** → secondary use of genotyping platforms.  
  - **NGS** → highest resolution but requires depth and computational power.  
- Biological relevance:  
  - Affect **larger fraction of nucleotides** than SNPs.  
  - Involved in **phenotypic variation, adaptation, and disease**.  
  - Used in **livestock breeding**, **medical genetics**, and **population genomics**.  
