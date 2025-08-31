# Copy Number Variation (CNV) Detection Methods

Structural variants such as **Copy Number Variations (CNVs)** can be detected using different computational approaches applied to **Next-Generation Sequencing (NGS)** data.  
There is no single universal method: in practice, most pipelines combine multiple approaches to improve sensitivity and specificity.

The main strategies include:

- **Read Pair (RP)**
- **Split Read (SR)**
- **Read Depth (RD)**
- **Assembly (AS)**

## 1. Read Pair (RP) Approach

Read Pair methods compare the **insert size** (distance between paired-end reads) with the expected insert size from the reference genome.

- In paired-end sequencing, DNA fragments are expected to follow a defined distribution around an average insert size.  
- **Deletions** → result in **shorter insert sizes** than expected.  
- **Insertions** → result in **longer insert sizes** than expected.  

Thus, discordance between mapped paired-reads can be used to identify CNVs.

**Strengths**
- Effective for detecting **medium-sized insertions and deletions**.  
- Can localize CNVs by comparing observed vs. expected insert distances.

**Limitations**
- Insensitive to very small indels (difficult to distinguish from background variability).  
- Requires high-quality paired-end data.

## 2. Split Read (SR) Approach

Split Read methods rely on the fact that sometimes only **one part of a read maps reliably** to the reference genome, while the other part does not.

- A read may be **“split”** across a structural variant breakpoint (e.g., deletion, insertion).  
- For example: one half of a read maps far from the other half, or only part of the read aligns correctly.  
- The unmapped part suggests the presence of a structural variant at that location.

**Key point**: SR can capture the **exact breakpoint** of a CNV.  
However, **multiple overlapping reads** are needed for confirmation, since single-read evidence might be due to sequencing artifacts or chimeric sequences.

## 3. Read Depth (RD) Approach

Read Depth methods are based on the **correlation between sequencing coverage and copy number**:  

- Regions with **higher coverage** than expected → likely **copy number gain**.  
- Regions with **lower coverage** → likely **copy number loss**.

### Strategies
- **Single Sample**:  
  Copy number is estimated directly from coverage. Gains appear as local increases, losses as decreases.  
Repetitive regions must be excluded since they bias coverage.

- **Paired Case/Control Samples**:  
  Coverage in a test sample is compared with a control.  
Sequencing depth must be consistent across samples; biases affect all samples similarly.

- **Large Population of Samples**:  
  Uses the **average read depth** across many individuals to identify CNVs.

### Technical details
- The genome is divided into windows (e.g., 1 Mb).  
- Read counts are normalized for biases (e.g., GC content, repeats).  
- Segmentation algorithms identify contiguous regions of altered copy number.  
- Statistical filtering ensures significance of CNV calls.

**Strengths**
- Good at detecting large CNVs.  
- Straightforward to apply with NGS.

**Limitations**
- Resolution depends on sequencing depth and window size.  
- Sensitive to biases in short-read sequencing.  
- Long-read sequencing can overcome many of these problems.

## 4. Assembly (AS) Approach

Assembly-based methods reconstruct **contigs/scaffolds** from sequencing reads, which are then compared with the reference genome.

- In principle, any genetic variation (including CNVs) can be detected if reads are long and accurate enough.  
- Structural variations are revealed when contigs differ from the reference.

**Limitations**
- Extremely demanding in terms of computational resources.  
- Less accurate in **repetitive or duplicated regions**, which are abundant in eukaryotic genomes.  
- Poor performance in complex regions and heterozygous variants (typically only homozygous CNVs are detected).

## 5. SNP Array-Based CNV Detection (PennCNV Example)

Besides sequencing, **SNP array data** can also be used for CNV detection.

- **PennCNV** is a widely used free tool for Illumina and Affymetrix platforms.  
- It works by analyzing **signal intensity data** (not just genotype calls), similar to **aCGH**.  
- Uses **Hidden Markov Models (HMMs)** to call CNVs.  

### Key aspects
- At least **5 contiguous SNPs/probes** with concordant signal are required to detect a CNV.  
- The resolution depends on probe density (e.g., 1 probe every 30 kb → minimum CNV size ≈ 150 kb).  
- Whole-genome sequencing provides higher resolution but at higher cost.

### Validation
- CNVs called with PennCNV are often validated with **qPCR** (quantitative PCR).  
- qPCR quantifies copy number by comparing amplification cycles with reference loci.  

## Summary

| Method | Detects | Strengths | Limitations |
|--------|---------|-----------|-------------|
| **Read Pair (RP)** | Medium-sized insertions/deletions | Uses paired-end data, relatively simple | Misses small events |
| **Split Read (SR)** | Exact breakpoints | High resolution at breakpoints | Needs multiple overlapping reads |
| **Read Depth (RD)** | Gains/losses of large regions | Scales to populations, simple coverage-based | Affected by sequencing biases |
| **Assembly (AS)** | All forms of SVs (theoretically) | Can detect novel and complex variants | Computationally heavy, poor in repeats |
| **SNP Array (PennCNV)** | CNVs via probe signal intensity | Cost-effective, widely used | Limited by probe density |

---

## Final Note

No single method is perfect.  
**Robust CNV detection pipelines combine multiple approaches** (e.g., RD + RP + SR) to minimize biases and maximize detection accuracy.
