# Theory of Quality Control (QC) in NGS

## 1. Introduction
Quality Control (QC) is a **fundamental step** in NGS workflows.  
- Ensures that the **raw data** (FASTQ, BAM, etc.) are reliable.  
- Identifies biases introduced by **library preparation**, **sequencing platform**, or **sample quality**.  
- Prevents **false positives** in downstream variant discovery.  

Professor’s recommended tools:  
- **FastQC** → widely used, Java-based, modular, with HTML reports.  
- **Prinseq** → efficient for trimming and filtering.

## 2. FastQC Overview
FastQC provides modular analyses:
1. Import data from BAM, SAM, FASTQ.  
2. Quick overview of potential problems.  
3. Summary graphs & tables.  
4. Export of results to HTML reports.  
5. Works offline.  

### Key Modules
- **Basic Statistics** → sequence count, length distribution.  
- **Per-base sequence quality** (critical).  
- **Per-sequence quality score**.  
- **Per-base sequence content**.  
- **GC content**.  
- **Sequence duplication levels**.  

## 3. Interpreting FastQC Results

### Per-base Sequence Quality
- Boxplots per position along the read.  
- Aggregated **Phred scores** show accuracy.  
- Threshold: **Q ≥ 20** (≥99% base-call accuracy).  
- **Green zone** = good, **orange** = warning.  
- Typically, quality drops towards the **end of reads**.  

### Per-sequence Quality Score
- X-axis: average Phred score.  
- Y-axis: number of reads.  
- Shows distribution of read-level quality.  
- Reads with mean Q < 20 should be discarded.  
- Ensures dataset reliability before alignment.  

### Per-base Sequence Content
- Shows frequency of A, T, C, G at each position.  
- Ideal: stable percentages across read length.  
- Fluctuations at the start/end → sequencing errors or **library prep bias** (e.g., restriction enzyme digestion).  

### GC Content
- Distribution of GC content per read.  
- Compared against **theoretical distribution** of the target genome.  
- Deviations indicate:  
  - **Biases** in library prep.  
  - **Contaminants** (e.g., environmental DNA).  
- Example: cattle DNA expected → one Gaussian distribution.  
  - If multiple peaks → contaminants or mixed DNA sources.  

### Sequence Duplication Levels
- Expected: most reads are **unique**.  
- High duplication → bias in library prep (often PCR).  
- Amplicon sequencing: duplication expected.  
- Duplicated reads can bias variant calls → must be removed.  
- After **deduplication**, most reads should be unique.  

## 4. Improving Data Quality

### Trimming
Removing low-quality bases increases dataset reliability.  
Two main approaches:

1. **Threshold-based trimming**  
   - Define Q threshold (e.g., Q20).  
   - Remove bases below threshold until high-quality base reached.  

2. **Window-based trimming (preferred)**  
   - Define window size (e.g., 5 nt).  
   - Calculate average quality in the window.  
   - If average < threshold → trim region.  
   - Retains more nucleotides by smoothing local fluctuations.  

Software: **Prinseq** (efficient implementation).  

## 5. Workflow of QC
1. Run **FastQC** → identify quality issues.  
2. Apply **trimming/filtering** (e.g., Prinseq, Trimmomatic).  
3. Remove low-quality bases & duplicated reads.  
4. Re-run **FastQC** → confirm improvement.  
5. Only then proceed with alignment & variant discovery.  

## 6. Why QC Matters
- Poor-quality reads → false SNPs/indels (false positives).  
- GC bias → misinterpretation of gene regions.  
- Duplicates → inflated coverage, misleading variant calling.  
- Without QC, downstream analyses (alignment, variant calling, annotation) are unreliable.  
