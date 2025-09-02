# Variant Discovery in NGS

## 1. Introduction
**Variant discovery** is a central application of Next-Generation Sequencing (NGS).  
It combines two dimensions:
- **Computational**: data processing, alignment, variant calling.  
- **Biological**: interpretation of variants, their classification, and consequences.  

Goal: starting from raw sequencing reads, identify and characterize genomic variants that may affect phenotype, disease, or population traits.

## 2. Types of Genetic Variants

### Small Variants
- **SNPs (Single Nucleotide Polymorphisms)**  
  - Substitution of one base with another.  
  - Must occur in ≥1% of the population → polymorphism.  
  - If <1%, it is considered a **mutation**.  

- **Indels**  
  - Small insertions or deletions.  

- **Substitutions**  
  - Multiple bases replaced by different ones.  

### Structural Variants
- **CNVs (Copy Number Variants)** → duplicated or deleted regions.  
- **Inversions** → DNA region flipped in orientation.  
- **Translocations** → block of DNA moved to another chromosome or region.  

## 3. Ontologies for Variant Annotation
Variants must be described consistently using **controlled vocabularies (ontologies)**.  
- Ontologies organize terms in **directed graphs**:  
  - Specific terms are subsets of broader ones.  
  - Example: *missense_variant* ⊂ *sequence_variant*.  

### Example: Missense Variant in Donkey Albinism
- **Species**: Asinara white donkey (*Equus asinus*).  
- **Gene**: Tyrosinase (TYR), required for melanin synthesis.  
- **Variant**: c.604C>G → p.His202Asp substitution.  
- **Effect**: loss of copper-binding function → albinism phenotype.  

### Example: TF Binding Site Variant
- **Transcription Factors (TFs)** bind promoters.  
- Variants in TF Binding Sites (TFBS) can cause:  
  - Loss of binding site.  
  - Gain of binding site.  
  - Change in binding affinity.  

## 4. Visualizing Variants – Entropy Logos
- **Sequence logos** show conservation of nucleotides/amino acids.  
- Larger letters = more conserved positions (higher information content).  
- Variants in conserved positions are likely to have stronger effects.  

## 5. NGS Workflow for Variant Discovery
The pipeline is short in code but complex in interpretation:

1. **Input**: `FASTQ` files (reads + quality scores).  
2. **Alignment**: map reads to reference genome → `BAM` file (compressed).  
3. **Variant Calling**: detect SNPs/indels → `VCF` file.  
4. **Variant Annotation**: classify as missense, frameshift, intronic, etc.  
5. **Interpretation**: biological meaning, disease relevance, population genetics.  

## 6. Challenges in NGS Variant Discovery
- **Read length**: short reads are harder to place uniquely.  
- **Big data**: terabytes of sequencing data require computational resources.  
- **Trade-off**: speed vs sensitivity (fast tools may lose accuracy).  
- **Genome complexity**: repeats, polyploidy, low complexity regions complicate mapping.  
- **Reference issues**: assemblies may contain errors or misassembled regions.  

## 7. Alignment Algorithms
- **BWA-MEM** → based on Burrows-Wheeler Transform (BWT).  
- **Bowtie2** → hash-table based.  
- **BLAST** → too slow for large-scale NGS.  

Example:  
- Same dataset aligned with **BWA** and **Bowtie2**, variants called with **SAMtools**.  
- Only **24.5% of variants** overlapped.  
- Different aligners → different results.  

➡ Recommendation: test multiple aligners and compare.  

## 8. Quality Control (QC)
Always check data at each step:  
- **Per-base quality** (FASTQ Phred scores).  
- **Mapping Quality (MQ)** → probability a read is correctly aligned.  
- **Filtering**: remove duplicates, adapters, poor quality reads.  
- **Coverage analysis**: ensure sufficient depth.  

False positives can arise if QC is skipped.  

## 9. Tools and Best Practices
- **SAMtools** → manipulate SAM/BAM, variant calling.  
- **GATK Best Practices** → widely adopted pipeline for:  
  - Germline variant discovery.  
  - Somatic mutation detection.  
  - RNA-seq variant analysis.  

## 10. File Formats

### FASTQ
- Four lines per entry:  
  1. `@` identifier  
  2. Sequence (ACGT)  
  3. `+` separator  
  4. Quality scores (ASCII-encoded, Phred scale)  

### BAM
- Binary, compressed version of SAM.  
- Standard for storing aligned reads.  

### VCF
- Variant Call Format.  
- Stores SNPs, indels, and annotations.  

## 11. Quality Scores – Phred Scale
Phred score formula:  

\[
Q = -10 \cdot \log_{10}(P)
\]

Where **P** = probability of incorrect base call.  

- Q10 → 1 error in 10 bases (90% accuracy).  
- Q30 → 1 error in 1000 bases (99.9% accuracy).  

Encoding differs by technology (Sanger, Illumina versions, Solexa). Always check before processing.  

## 12. Paired-End Sequencing
- Each DNA fragment is sequenced from both ends.  
- Produces **two FASTQ files** (forward `/1` and reverse `/2`).  
- Improves mapping accuracy, especially in repetitive regions.  
- Facilitates structural variant detection and gap filling.  

## Key Takeaways
- Variant discovery = **NGS pipeline + biological interpretation**.  
- Variants include SNPs, indels, CNVs, inversions, and translocations.  
- Ontologies provide consistent terminology for annotation.  
- Workflow: `FASTQ → BAM → VCF → Annotation → Interpretation`.  
- Tools: **BWA, Bowtie2, SAMtools, GATK**.  
- File formats: **FASTQ, BAM, VCF** are standards in NGS.  
- QC and Phred scores are essential to ensure reliable results.  
- Biological interpretation is the hardest part → understanding consequences is as important as detection.  
