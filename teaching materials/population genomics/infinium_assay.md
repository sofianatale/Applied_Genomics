# SNP Genotyping – Infinium Assay and Related Approaches

## 1. Infinium Assay – Principle

The Infinium assay enables SNP genotyping using **probes covalently linked to a surface** (e.g., a microscope slide).

### How it works
1. **Probe hybridization**  
   - Probes are single-stranded DNA sequences complementary to the region of interest.  
   - They hybridize to target DNA and terminate **one nucleotide before the SNP site**.  

2. **Single nucleotide extension**  
   - A primer extension reaction adds the complementary base at the SNP position.  
   - Each nucleotide is labeled with a different fluorescent color.  

3. **Signal detection**  
   - Fluorescent signals are detected by a scanner.  
   - **Homozygous genotypes**: all probes extended with the same nucleotide (one color).  
   - **Heterozygous genotypes**: mixture of two colors.  

Important: probes must avoid repetitive regions to prevent biased results.

## 2. Alternative Array-Based Platforms

### Affymetrix Axiom Genome Arrays
- Based on **multiple hybridization signals** rather than single-primer extension.  
- Probes overlap to ensure robust detection.  
- Less robust than Illumina arrays, but widely used.  
- Thermo Fisher Scientific acquired Axiom technology.  
- Population-specific tools are available for targeted applications.  

## 3. GenomeStudio – Genotyping Module

Illumina’s **GenomeStudio software** is used to analyze Infinium and GoldenGate array data.  

- **Genoplot display**:  
  - Red = AA, Purple = AB, Blue = BB  
  - Genotypes are separated based on **signal intensity (Norm R)** and **allele frequency (Norm Theta)**.  
- Features:  
  - Normalization of data  
  - Genotype calling and clustering  
  - Loss of heterozygosity (LOH) analysis  
  - Copy number variation (CNV) analysis  

Applications include **inbreeding analysis** (runs of homozygosity), **CNV detection**, and detailed clustering of genotypes.

## 4. SNP Chips vs Custom Genotyping Arrays

### SNP Chips
- Predefined number of SNPs → only obtain data for variants included on the chip.  
- Fixed design: cannot add new variants without redesigning the chip.  

### Custom Genotyping Arrays
- Targeted panels designed for specific populations, traits, or species.  
- Advantages:  
  - Focus on variants of interest (e.g., disease-associated SNPs, missense mutations).  
  - Cost-effective for large-scale studies (~20–25 € per sample).  
  - Avoid irrelevant genomic regions.  

## 5. Hardy–Weinberg Equilibrium (HWE) and SNP Quality Control

- SNPs not in HWE may indicate:  
  - **Technical problems** (e.g., poor probe design, CNVs, assay bias).  
  - **Biological phenomena** (selection, population structure, inbreeding).  

- Workflow:  
  1. Genotype an initial batch of samples.  
  2. Identify SNPs deviating from HWE.  
  3. Flag problematic SNPs → remove them in the second generation of the array.  

- QC thresholds must balance:  
  - Detecting **true biological deviations** from HWE.  
  - Excluding **technical artifacts**.  

## 6. Sequencing-Based Genotyping Approaches

Array-based methods are complemented by **Next-Generation Sequencing (NGS)** approaches:

### 6.1 Amplicon Sequencing
- Targeted amplification of predefined regions.  
- Very high depth (thousands of reads per SNP).  
- Used in **clinical applications** (e.g., cancer predisposition panels).  

### 6.2 Genotyping by Sequencing (GBS)
- PCR-based, multiplexed amplification of many regions.  
- Widely applied in plants and non-model species.  

### 6.3 Hybridization-Based Enrichment
- Capture selected genome regions before sequencing.  
- Example: **Exome sequencing**.  

### 6.4 RAD-seq (Restriction-site Associated DNA Sequencing)
- Digest DNA with restriction enzymes at palindromic sites.  
- Amplify and sequence fragments anchored to consistent genomic positions.  
- Does not necessarily require a reference genome.  

### 6.5 Reduced Representation Sequencing
- Sequence only a fraction of the genome at high depth.  
- Enrich for informative SNPs while reducing cost.  

## 7. Practical Considerations

- **Depth of sequencing**:  
  - Essential for accurate SNP calling.  
  - ≥100× coverage recommended to minimize allele dropout.  

- **Pooling strategies**:  
  - DNA pooling allows allele frequency estimation across populations.  
  - Useful for detecting **selection signatures** and **diversity patterns**.  

- **Costs**:  
  - SNP chips: cost fixed by predefined content.  
  - Custom arrays: ~20–25 € per sample.  
  - Sequencing-based approaches: scalable but bioinformatics-intensive.  

## 8. Summary

- **Infinium Assay**: robust SNP genotyping using probe hybridization and single-nucleotide extension.  
- **Array-based methods** (Illumina, Affymetrix): standardized, cost-effective, but limited to predefined variants.  
- **Sequencing-based methods** (Amplicon, GBS, RAD-seq, exome capture): flexible, high-resolution, often used in non-model species or targeted studies.  
- **QC with Hardy–Weinberg equilibrium** is crucial to detect both technical issues and biological signals.  
- Choice of method depends on:  
  - Research question  
  - Population size  
  - Budget  
  - Reference genome availability  
