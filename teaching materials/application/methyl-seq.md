# Epigenomics and Methyl-Seq

## Introduction
- **Epigenomics** studies modifications that regulate gene expression without altering the DNA sequence.  
- **DNA methylation** (mainly at cytosines in CpG dinucleotides) plays a key role in gene regulation.  
- The **genome sequence** is the same in all cell types, but methylation patterns differ across tissues, cell types, and developmental stages.  

### CpG Islands
- Regions rich in CpG sites.  
- Often associated with gene promoters.  
- Adjacent regions:  
  - **CpG shores** → within 2 kb from CpG island.  
  - **CpG shelves** → within 2–4 kb.  

**Methylation effect**:  
- Hypermethylation of promoter regions often silences gene expression.  
- Hypomethylation can promote gene activation.  

## Bisulfite Sequencing
**Principle**: treatment of DNA with sodium bisulfite converts cytosines, but **methylated cytosines are protected**.

1. **Unmethylated cytosines (C)** → converted to **uracil (U)** → sequenced as **thymine (T)**.  
2. **Methylated cytosines (5mC)** → remain as **cytosine (C)**.  

### Workflow
1. Extract DNA.  
2. Treat with sodium bisulfite.  
3. Sequence DNA (NGS).  
4. Map reads back to reference genome.  

**Interpretation**:
- If base = **C** → cytosine was methylated.  
- If base = **T** → cytosine was unmethylated.  

## Challenges
- A **C→T change** in sequencing can represent:  
  1. **Bisulfite conversion** (true methylation signal).  
  2. A **genuine variant (SNP)**.  
- Distinguishing between these requires careful experimental design and sometimes complementary sequencing approaches.  

## Library Preparation Strategies
- Different library prep methods have been developed to maximize sensitivity and distinguish:  
  - **Variants (SNPs)** vs **Methylation status**.  
  - Whole-genome vs exome-level methylation.  
- Approaches include:  
  - Whole-genome bisulfite sequencing (**WGBS**).  
  - Reduced representation bisulfite sequencing (**RRBS**).  
  - Targeted bisulfite sequencing (specific loci).  


## Applications of Methyl-Seq
- Studying **tissue-specific regulation**.  
- Identifying **epigenetic biomarkers** in cancer.  
- Understanding developmental processes.  
- Disentangling **genetic variants vs epigenetic modifications**.  

## Summary
- DNA methylation is a key epigenetic mechanism regulating gene expression.  
- **Bisulfite sequencing** is the gold standard for detecting methylated cytosines.  
- Distinguishing between **C→T SNPs** and **C→T due to bisulfite conversion** is critical.  
- Several strategies (WGBS, RRBS, targeted Methyl-Seq) exist to explore methylation patterns across the genome.  
