# SAM/BAM Formats, Alignment Flags & CIGAR Strings

## 1. Introduction
Once sequencing data (FASTQ) are aligned against a **reference genome**, the results are stored in:
- **SAM (Sequence Alignment/Map)** → text-based format, human-readable.
- **BAM (Binary Alignment/Map)** → binary version of SAM, compressed, space-efficient.

SAM/BAM are standard formats in genomics and widely used in downstream analysis (variant calling, metagenomics, etc.).

## 2. Workflow Recap
1. Start from **FASTQ file** (raw reads).  
2. Align reads to reference genome with **BWA-MEM** (or similar).  
3. Output → **BAM file** (compressed alignment).  
4. BAM can be converted back to SAM if needed for inspection.  
5. SAM/BAM files can be re-used, sub-sampled, or re-aligned to save time & resources.  

## 3. Structure of SAM Format
A SAM file has two sections:

### a) Header
- Lines start with `@`.  
- Contains metadata about alignment:  
  - Reference sequence IDs & lengths.  
  - Alignment program & command line (`@PG`).  
- Important for reproducibility & database submission.  

### b) Alignment Section
Each read is represented by a row with **11 mandatory fields**:
1. **QNAME** → read identifier.  
2. **FLAG** → integer encoding alignment properties.  
3. **RNAME** → reference sequence name (chromosome).  
4. **POS** → starting position on reference.  
5. **MAPQ** → mapping quality score.  
6. **CIGAR** → compact description of alignment.  
7. **RNEXT** → mate/next read info.  
8. **PNEXT** → position of mate/next read.  
9. **TLEN** → observed template length.  
10. **SEQ** → read sequence.  
11. **QUAL** → base quality (Phred).  

## 4. FLAG Field
The **FLAG** encodes properties of each read as integers.  
Examples:  
- `4` → read is **unmapped**.  
- `256` → secondary alignment.  
- `1024` → PCR duplicate.  

Multiple values can be combined.  
Online tools can decode FLAG values into human-readable form.  

### Example use
- Extract **unmapped reads** (FLAG 4) → align them to microbial/viral databases → **metagenomics applications**.  
- Detect **contaminants** in sequencing experiments.  

## 5. Metagenomics & One Health
- **Unmapped reads** from a cattle genome could reveal microbial or viral DNA.  
- Pipelines can re-align unmapped reads to pathogen databases.  
- Applications:  
  - Human virome studies.  
  - Animal surveillance.  
  - **One Health**: studying interactions between humans, animals, and environment.

## 6. CIGAR Strings
**CIGAR = Compact Idiosyncratic Gapped Alignment Report**.  
Describes how each read aligns to the reference.

### Common symbols:
- **M** → match/mismatch (aligned).  
- **I** → insertion (present in read, absent in reference).  
- **D** → deletion (absent in read, present in reference).  
- **S** → soft clipping (part of the read not aligned).  

### Example
4S8M2I4M1D
- 4 bases soft-clipped.  
- 8 matches.  
- 2 inserted bases.  
- 4 matches.  
- 1 deleted base.  

**Mismatches** are not explicitly shown in CIGAR (handled in variant calling).  

### Applications
- Detecting **indels** and **structural variants**.  
- Identifying ancient mitochondrial insertions in nuclear genomes.  

## 7. Filtering Alignments
Quality control continues **after alignment**:

### a) Mapping Quality (MAPQ)
- Probability that read is correctly mapped.  
- **MAPQ = 0** → read could map to multiple locations (e.g., repetitive elements, assembly errors).  
- Reads with low MAPQ often discarded.  

### b) Duplicate Removal
- Duplicates come from PCR amplification.  
- They don’t add information, but inflate coverage.  
- Can create false positives in variant calling.  
- Tools: **Picard** for duplicate marking/removal.  
- PCR-free library preparation avoids this issue (requires more input DNA).  

## 8. Key Takeaways
- **SAM/BAM** are core alignment formats.  
- **FLAG** encodes critical information (mapped/unmapped, duplicates, secondary alignments).  
- **CIGAR strings** describe alignment operations (match, insertion, deletion, clipping).  
- **Unmapped reads** can be leveraged in metagenomics & One Health research.  
- Alignment QC (MAPQ filtering, duplicate removal) is essential before variant calling.  


