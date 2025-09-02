# Variant Calling and Annotation

## 1. Introduction
After sequencing, alignment, QC, and filtering, the next step is **variant calling**.  
- Goal: identify genetic differences (SNPs, indels, SVs) compared to a reference genome.  
- Main software: **GATK (Genome Analysis Toolkit)** – standard in the field.  
- Output: **VCF (Variant Call Format)** file.  

## 2. Key Considerations Before Calling Variants
Calling a variant requires careful evaluation of multiple factors:

- **Base call quality** of each supporting base.  
- **Mapping quality (MQ)** of aligned reads.  
- **Sequencing depth** → minimum number of reads supporting the variant.  
- **Proximity to indels or homopolymer runs** (error-prone regions).  
- **Single-sample vs multi-sample calling**.  
  - More samples = higher confidence.  

Example: in **homopolymeric regions** (e.g., AAAAAA), a detected SNP may be an artifact.  

## 3. Variant Calling Strategies
### a) Per-sample calling
- Each sample analyzed separately.  
- Produces **one VCF file per sample**.  

### b) Joint calling
- All samples analyzed together.  
- Produces **one merged VCF file**.  
- Advantages:  
  - Increases statistical power.  
  - Better detection of heterozygous variants.  
  - Reduces false negatives from low coverage.  

Recommended: **joint calling** for population studies.

## 4. VCF File Format
A **VCF file** has two sections:  

### a) Header
- Lines start with `##`.  
- Define metadata, filters, INFO fields, FORMAT descriptors.  
- Last header line starts with `#CHROM` → column names.  

### b) Variant Records
Each row represents one variant.  
Columns include:  

1. **CHROM** → Chromosome ID.  
2. **POS** → Position of variant.  
3. **ID** → Variant ID (e.g., dbSNP `rs` number, or `.` if novel).  
4. **REF** → Reference allele.  
5. **ALT** → Alternative allele(s).  
6. **QUAL** → Phred-scaled variant quality score.  
7. **FILTER** → PASS/FAIL (e.g., “PASS”, “q10”).  
8. **INFO** → Additional annotations (DP = depth, AF = allele frequency, etc.).  
9. **FORMAT** → Defines per-sample genotype fields (e.g., GT, DP, GQ).  
10+. **Samples** → Genotypes and metrics for each sample.  

### Genotype Codes
- `0|0` → homozygous reference.  
- `0|1` or `1|0` → heterozygous.  
- `1|1` → homozygous alternate.  
- If multiple alternate alleles exist: `2`, `3`, etc.  

## 5. Interpreting Variants
- **High-quality variants** are supported by many reads with high base quality.  
- **Low coverage positions** (<3 reads) → unreliable.  
- **Homopolymer-associated variants** → likely false positives.  
- **Filters in VCF** help identify low-confidence calls.  

## 6. Software for Variant Visualization
- **IGV (Integrative Genomics Viewer)** → gold standard for inspecting alignments.  
- Inputs: reference genome (FASTA), alignment (BAM), and variants (VCF).  
- Features:  
  - Visualize reads aligned at a given locus.  
  - Detect true variants vs sequencing errors.  
  - Depth bar shows number of supporting reads.  
  - Color-coding distinguishes reference vs alternate alleles.  

### Example in IGV:
- Half of reads show `G`, half `T` → heterozygous SNP.  
- A single read shows a unique substitution → likely sequencing error.  

## 7. Variant Annotation
Once variants are called, the next step is to understand their **biological impact**.

- Variants can occur in **genes, introns, regulatory regions**.  
- Consequences vary depending on location (e.g., coding region indel vs intergenic SNP).  

### Example – Indel Variant
- Sample shows a **28-base deletion** in half the reads.  
- Reference genome retains all 28 bases.  
- Interpretation: the individual is **heterozygous** for this variant.  

## 8. Tools for Variant Annotation
### Ensembl Genome Browser
- Allows visualization of **genomes, genes, transcripts, proteins, and variants**.  
- Example: searching the **KMO gene** gives:  
  - Chromosomal location.  
  - Gene description.  
  - Transcript IDs and number.  
  - Encoded protein + UniProt link.  
  - Variant table for known polymorphisms (dbSNP, Ensembl).  

### Variant Effect Predictor (VEP)
- Provided by Ensembl.  
- Takes VCF as input.  
- Outputs:  
  - Genomic location of variants.  
  - Variant type (missense, synonymous, frameshift…).  
  - Functional consequences on gene/protein.  

### dbSNP
- Repository of **known SNPs and small indels**.  
- Variants deposited with IDs (`rsXXXX`).  
- Can be cross-referenced to validate if a variant is novel.  

## 9. Applications of Annotation
- **Identify novel variants** after excluding known ones.  
- Correlate variants with **phenotypes** (e.g., disease vs healthy).  
- In clinical settings: interpret pathogenic variants (cancer, rare diseases).  
- In population genomics: compute **allele frequencies** and study evolutionary forces.  
- In applied research: adapt pipelines depending on species or goal (cancer, microorganisms, animal genomes).  

## Key Takeaways
- Variant calling produces **VCF files**, but interpretation requires **annotation**.  
- Tools like **Ensembl, dbSNP, VEP** enable biological interpretation.  
- Known vs novel variants must be distinguished.  
- Annotation pipelines differ depending on the research context (clinical, cancer, population genetics, etc.).  
- Always validate key variants using visualization tools like **IGV**.  
