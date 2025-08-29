## ATAC-Seq (Assay for Transposase-Accessible Chromatin using sequencing)

## Introduction
- **Goal**: study **chromatin accessibility** to identify open regions of the genome.
- Provides insights into **regulatory elements** (promoters, enhancers) and **nucleosome positioning**.
- Uses **Tn5 transposase**, which simultaneously fragments DNA and inserts sequencing adapters.

## Standard ATAC-Seq Workflow
1. **Cell/Nuclei Preparation**
   - Intact nuclei are isolated from fresh or frozen samples.
   - Reduces background from free DNA or damaged cells.

2. **Tagmentation**
   - Tn5 transposase inserts sequencing adapters into open chromatin.
   - DNA is fragmented and tagged in a single step.

3. **Library Preparation & Sequencing**
   - Tagged DNA fragments are PCR-amplified.
   - Sequenced on high-throughput platforms (e.g., Illumina).

4. **Data Analysis**
   - Reads aligned to the reference genome (e.g., Bowtie2, BWA).
   - Accessible regions identified as **peaks** using tools such as MACS2.
   - Fragment size distribution indicates nucleosome positioning:
     - <100 bp → nucleosome-free regions
     - ~200 bp → mono-nucleosomes
     - >400 bp → multiple nucleosomes

## Variants of ATAC-Seq
- **Single-cell ATAC-seq**: chromatin accessibility at single-cell resolution.
- **Omni-ATAC**: improved protocol with reduced background.
- **scMultiome (RNA+ATAC)**: integrates chromatin accessibility with gene expression.

## Applications
- Identification of **regulatory elements** (enhancers, promoters).
- Analysis of **transcription factor binding motifs**.
- Comparison of chromatin accessibility across conditions or cell types.
- Integration with RNA-seq or ChIP-seq for multi-omics studies.

## Output
- **Aligned reads (BAM files)**: sequencing data mapped to genome.
- **Peak files (BED/GFF)**: accessible chromatin regions.
- **BigWig tracks**: for genome browser visualization.
- **Motif enrichment**: transcription factors associated with open regions.

## Summary
- ATAC-seq is a rapid and sensitive method to study chromatin accessibility.
- Key steps: nuclei isolation → tagmentation → sequencing → peak calling.
- Variants extend the method to single-cell and multi-omics applications.
- Results reveal the **regulatory landscape** of the genome across conditions.
