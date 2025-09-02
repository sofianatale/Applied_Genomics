# Raw Data Processing & File Formats

## From Raw Data to Reads
NGS produces **raw signal data** that must be converted into **reads with per-base quality scores**.  
Steps include:  
1. **Basecalling** → conversion of raw signals (light, voltage, pH) into nucleotides.  
2. **Read filtering** → remove poor-quality sequences.  
3. **Alignment** → mapping reads to a reference genome.  
4. **Variant calling** → identifying SNPs, indels, or structural variants.  

## Read Filtering
Not all reads are equally useful. Filtering is crucial:  
- Remove **polyclonal reads** (multiple DNA templates mixed in one well).  
- Discard **reads < 25 bases** → too short for reliable alignment.  
- Trim low-quality regions (sliding window / moving window).  
- Adjust parameters for **low-complexity libraries** (e.g., fusion primers, miRNA).  


## FASTA vs FASTQ
- **FASTA format** → plain text with nucleotide sequence (ACGT…) + identifier.  
  - No quality information.  
- **FASTQ format** → FASTA + **Phred quality scores** per base.  
  - Four lines per entry:  
    1. Sequence ID (header)  
    2. Nucleotide sequence  
    3. Separator (+)  
    4. Quality scores (ASCII symbols)  

### Quality Scores (Phred Scale)
\[
Q = -10 \cdot \log_{10}(e)
\]  
- **Q = quality score**  
- **e = probability of incorrect base call**  

Examples:  
- Q20 → 1 error in 100 bases (99% accuracy)  
- Q30 → 1 error in 1000 bases (99.9% accuracy)  

Ion Torrent error rates: ~Q20 (due to homopolymer issues), improving towards Q30.  

## Common File Formats in Genomics
1. **FASTQ**  
   - Fundamental text format with sequences + quality scores.  
   - Unaligned reads.  

2. **BAM (Binary Alignment Map)**  
   - Compressed binary format with both reads + alignment information.  
   - Requires index file; not human-readable.  

3. **VCF (Variant Call Format)**  
   - Text format for **variants**: SNPs, indels, structural differences.  
   - Standard in population and medical genomics.  

4. **BED (Browser Extensible Data)**  
   - Tab-delimited text format defining **genomic features**.  
   - Typically used to display tracks alongside reference genome in genome browsers.  

## Data Management
- Raw sequencing output can be **huge** (terabytes).  
- Filtering and compression reduce size dramatically:  
  - Example: **2.5 TB raw data** → ~**30 GB FASTQ**.  
- Efficient storage and file format choice are critical for downstream analysis.  
