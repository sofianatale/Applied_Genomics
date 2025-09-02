Long-Read Sequencing Technologies: Nanopore & PacBio

## Overview
While Illumina dominates **short-read sequencing**, two main technologies provide **long reads** (up to tens of kb or more):  
- **Oxford Nanopore Technologies (ONT)**  
- **PacBio (Pacific Biosciences)**  

Long-read sequencing helps resolve:  
- **Repetitive regions**  
- **Structural variations**  
- **Complex genome assemblies**  
- **Phasing of haplotypes**  

## Nanopore Sequencing

### Principle
- Sequencing **native DNA/RNA strands** (no synthesis step).  
- A single-stranded DNA (or RNA) passes through a **nanopore** embedded in a membrane.  
- Electric current runs across the pore; each nucleotide (or combination of bases) causes a specific **voltage disruption**.  
- Voltage shifts are translated into base calls.  

### Features
- **Read length**: up to ~10–20 kb in practice, **theoretical maximum >1 Mb**.  
- **Portability**: devices like MinION are **small, USB-powered**, and usable in the field.  
- **Direct sequencing of RNA** (no cDNA needed).  

### Pros
- Very cheap instrument (~€1000)  
- Portable, usable **on-site** (field genomics, clinical, environmental)  
- Ultra-long reads possible  
- Sequencing of RNA directly  

### Cons
- High error rate (~5%; historically ~20%)  
- Throughput less stable  
- Library prep still required  
- Not suitable for degraded samples (e.g., ancient DNA)  

## PacBio Sequencing (SMRT – Single Molecule Real-Time)

### Principle
- A **single DNA molecule** is immobilized in a well (Zero-Mode Waveguide, ZMW).  
- DNA polymerase incorporates **fluorescently labeled nucleotides**.  
- Each incorporation event emits light, captured by a camera.  
- **Interpulse duration** (time between signals) helps determine the base.  

### Circular Consensus Sequencing (CCS)
- DNA fragments are circularized (SMRTbell templates).  
- Sequenced multiple times as polymerase loops around the circle.  
- Errors are **random** → corrected by overlapping multiple passes.  

### Features
- **Read length**: typically 10–25 kb; can reach 50 kb.  
- **Error correction**: high accuracy with CCS (HiFi reads).  
- **Bias reduction**: no issues with GC-rich regions.  
- **Phasing**: can separate **maternal and paternal haplotypes**.  

### Pros
- Accurate long reads (HiFi reads with Q30+)  
- Excellent for **structural variants & complex genomes**  
- No GC-bias  
- Phasing of alleles possible  

### Cons
- High cost (3–4× Illumina per genome)  
- Lower throughput than short-read systems  
- Library prep is complex; requires **high-quality, non-degraded DNA**  
- Larger, lab-based instruments  

## Nanopore vs PacBio – Quick Comparison

| Feature              | Nanopore (ONT)                       | PacBio (SMRT)                         |
|----------------------|---------------------------------------|---------------------------------------|
| Principle            | Voltage disruptions across nanopores | Fluorescence from nucleotide incorporation |
| Read type            | Native DNA/RNA                       | Synthesized DNA (real-time)            |
| Read length          | 10–20 kb (up to 1 Mb possible)       | 10–25 kb (up to 50 kb)                 |
| Accuracy             | Moderate (~95%, improving)           | High (HiFi reads Q30+)                 |
| Error type           | Basecalling errors (homopolymers)    | Random errors (correctable by CCS)     |
| Device size          | Portable (MinION, GridION)           | Large lab machines                     |
| Cost (instrument)    | Low (~€1000 for MinION)              | High (hundreds of thousands)           |
| Best use cases       | Field sequencing, metagenomics, rapid testing | De novo genome assembly, clinical genomics, structural variants |

## Applications of Long-Read Sequencing
- **De novo genome assembly**  
- **Gap filling** in reference genomes  
- **Structural variation detection** (translocations, inversions, indels)  
- **Resolving repetitive regions**  
- **Haplotype phasing** (maternal vs paternal alleles)  
- **Full-length transcript sequencing**  

## Key Takeaways
- **Nanopore** → portable, cheap, ultra-long reads, but with higher error rates.  
- **PacBio** → highly accurate long reads (HiFi), excellent for structural variants, but expensive and lab-bound.  
- Both technologies complement short-read sequencing by resolving **complex regions and structural variation**.  
