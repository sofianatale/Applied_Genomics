# Illumina Paired-End Sequencing

## Overview
Illumina sequencing is usually **short-read sequencing** (100–500 bp per read).  
To overcome the limitation of sequencing only small fragments, **paired-end sequencing** allows reading **both ends** of a DNA fragment.

- Example:  
  - DNA fragment = 1000 bp  
  - Illumina read length = ~200 bp  
  - Paired-end → sequence **first 200 bp** + **last 200 bp**  
  - Middle 600 bp remain unsequenced directly, but are **physically linked**.  

## How It Works
1. **Library Preparation**  
   - DNA fragmented (e.g., ~1 kb)  
   - Adapters ligated at both ends  

2. **Sequencing**  
   - First sequencing run → one end of the fragment (~150–200 bp)  
   - Second sequencing run → opposite end (~150–200 bp)  

3. **Data Output**  
   - Two short reads separated by an **insert size** (unsequenced gap).  
   - Reads are stored in pairs and linked together computationally.  

## Applications
### 1. **Genome Assembly (De Novo & Resequencing)**
- Anchoring two ends allows bridging across unsequenced gaps.  
- Helps fill missing regions in draft genomes.  
- Provides better resolution in **repetitive regions**.  

### 2. **Structural Variation & Rearrangements**
- Reads that map far apart or on different chromosomes can reveal:  
  - Translocations  
  - Inversions  
  - Large insertions/deletions (indels)  
  - Gene fusions  

### 3. **Transcriptomics**
- Paired-end reads can capture **splicing events** and novel transcripts.  

## Advantages
- Provides **twice the number of reads** from the same DNA fragment.  
- More accurate **read alignment** to reference genomes.  
- Facilitates detection of **indels** and complex rearrangements.  
- Improves assembly in **de novo genome projects**.  

## Limitations
- Still limited by **short read length** (cannot directly span >500 bp).  
- Computationally more demanding than single-end.  
- Insert size must be carefully chosen (e.g., 300 bp vs 5 kb libraries).  

## Example: Gap Filling
- Reference genome has a **gap region**.  
- Paired-end sequencing provides two reads that flank the gap.  
- Since reads are physically linked, bioinformatic assembly can **anchor** the gap to surrounding regions.  
- Result: improved reconstruction of missing sequences.  
