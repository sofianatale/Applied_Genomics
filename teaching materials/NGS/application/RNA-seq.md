# RNA-Seq

## Introduction
- **RNA-Seq** = sequencing of the complete set of transcripts in a cell (the transcriptome).  
- Can include:  
  - mRNAs  
  - non-coding RNAs  
  - small RNAs  
- Applications:  
  1. Catalogue all species of transcripts.  
  2. Determine transcriptional structure of genes (start/end sites, splicing, post-transcriptional modifications).  
  3. Quantify expression levels across conditions or developmental stages.  

## Typical RNA-Seq Workflow
1. Extract RNA.  
2. Convert RNA to **cDNA libraries** (fragmentation + adaptor ligation).  
3. (Optional) Amplification.  
4. Sequence fragments with NGS (Illumina, Ion, etc.).  
5. Reads are aligned either to:  
   - Reference genome  
   - Reference transcriptome  
   - Or assembled **de novo** (if no reference available).  

- Typical read length: **30–400 bp**.  
- Reads can be:  
  - **Exonic reads**  
  - **Junction reads** (span exon–exon boundaries)  
  - **Poly(A)-end reads**  

## Data Analysis
- Align reads to reference or assemble de novo.  
- Count reads overlapping each transcript → expression quantification.  
- Highly expressed transcripts = many mapped reads.  

### Expression Metrics
To normalize for sequencing depth and gene length:  
- **RPKM** = Reads Per Kilobase of transcript per Million mapped reads.  
- **FPKM** = Fragments Per Kilobase of transcript per Million mapped reads.  
- **TPM** = Transcripts Per Kilobase of transcript per Million mapped reads.  

## Strategies for Transcript Reconstruction
Two main approaches:  

1. **Align-then-assemble**  
   - Reads are first aligned to reference genome.  
   - Transcripts reconstructed from splice junctions and alignments.  

2. **Assemble-then-align**  
   - Reads are first assembled **de novo** into transcripts.  
   - Assembled transcripts are then mapped back to genome.  
   - Works better for abundant transcripts.  

## RNA-Seq for Gene Expression Analysis
- Assumption: transcript abundance is proportional to number of reads mapped.  
- Pipeline:  
  1. Map reads to genome.  
  2. Count reads per gene (counting matrix).  
  3. Normalize data.  

Different normalization methods may lead to different results.

## Summary
- RNA-Seq enables **quantification and discovery of transcripts** (mRNA, ncRNA, small RNAs).  
- Two main strategies for transcript reconstruction: **align-then-assemble** and **assemble-then-align**.  
- Read counts reflect expression level → normalized using **RPKM, FPKM, TPM**.  
- Provides powerful insights into **gene expression regulation**, splicing, and transcriptome complexity.  
