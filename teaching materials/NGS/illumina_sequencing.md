# Illumina Sequencing (Sequencing by Synthesis, SBS)

## Overview
Illumina is the **leading NGS platform** in genomics today.  
It is based on **Sequencing by Synthesis (SBS)**, where nucleotides are incorporated **one at a time**, detected by fluorescence, and then reset for the next cycle.  
- Produces **short reads (100–500 bp)**  
- Extremely **high accuracy (Q30 ~ 99.9%)**  
- Scalable with different machines and **flow cells**  

## Workflow

### 1. Library Preparation
- **DNA fragmentation**:  
  - Physical (sonication) or enzymatic methods  
- **Adapters** are added to DNA fragments:  
  - Enable binding to flow cell oligos  
  - Contain **barcodes (indexes)** for multiplexing  
  - Provide primer binding sites  

### 2. Cluster Generation (Bridge Amplification)
- Performed on a **flow cell** (glass slide coated with oligonucleotides).  
- Each fragment binds to the surface and forms a **bridge**.  
- PCR amplification occurs, creating **thousands of clonal copies** of each fragment.  
- Each **cluster = one DNA fragment amplified**.  
- **Ordered clusters** in modern flow cells → higher accuracy and resolution.  

### 3. Sequencing by Synthesis
- **Reversible terminator nucleotides**:  
  - Each base has a fluorescent label + chemical blocking group.  
  - Only **one nucleotide is incorporated per cycle**.  
- Workflow per cycle:  
  1. Add 4 fluorescently labeled nucleotides (A, T, C, G).  
  2. DNA polymerase incorporates the complementary base.  
  3. Imaging system captures the **fluorescent color** of each cluster.  
  4. Blocking group is removed → synthesis can continue.  
  5. Cycle repeats.  

- Output: series of fluorescence signals → translated into a **read sequence**.  

## Chemistry & Improvements
- **4-channel SBS**: classic method → 4 fluorochromes (one per nucleotide).  
- **2-channel SBS**: uses only 2 dyes for 4 bases → reduced cost/time.  
- **1-channel SBS**: uses one dye with chemical tricks (on/off states) to distinguish nucleotides.  

Advantages of SBS chemistry:  
- Prevents **homopolymer errors** (unlike Ion Torrent).  
- High precision because **reaction is stopped and read at each cycle**.  

Trade-off:  
- Chemistry is **more expensive** due to modified nucleotides.  
- Sequencing is **slower** because of stop–read–reset cycles.  

## Accuracy & Read Length
- **Read length**: 100–500 bp (depending on chemistry and machine).  
- **Error rate**: extremely low, typically Q30 (1 error every 1000 bases).  
- Gold standard for:  
  - Whole-genome sequencing (WGS)  
  - Exome sequencing  
  - RNA-seq  
  - Small variant detection (SNPs, indels)  

## Advantages
- Very high accuracy  
- Wide range of applications  
- Scalable throughput (different flow cells and instruments)  
- Multiplexing via barcodes  

## Limitations
- More expensive chemistry (modified nucleotides)  
- Short reads compared to long-read technologies (PacBio, Nanopore)  
- Slower per cycle (due to imaging and chemical reset steps)  

