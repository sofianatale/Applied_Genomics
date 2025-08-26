# Lecture – DNA Quality Assessment & Sequencing Coverage

## 1. Quality Assessment of DNA
Before starting **NGS library preparation**, DNA quality must be carefully evaluated.  
DNA purity and integrity affect downstream steps such as library prep, amplification, and sequencing efficiency.

### Purity Ratios (Spectrophotometry)
- **A260/280 ratio**  
  - Expected: ~1.8  
  - High values → RNA contamination  
  - Low values → protein contamination, residual phenol, or very low DNA concentration (<10 ng/µl)  
  - Influenced by pH (acidic solution ↓ ratio; basic solution ↑ ratio)  

- **A260/230 ratio**  
  - Expected: 2.0 – 2.2  
  - Low values → carbohydrate carryover (plants), residual phenol, guanidine, glycogen  
  - High values → improper blank solution  

### DNA Integrity
- Checked by **agarose gel electrophoresis**:  
  - **High-quality DNA** → sharp band, high molecular weight (upper gel region)  
  - **Degraded DNA** → smeared band or lower fragments  
- Low integrity does not prevent sequencing, but **long-read sequencing (Nanopore, PacBio)** requires intact long fragments.  

## 2. Sample Requirements for NGS
Companies providing sequencing services usually require:

- **Condition**: genomic DNA  
- **Quantity**:  
  - ≥ 1 µg (small fragment library)  
  - > 1.5 µg (PCR-free library)  
- **Concentration**: ≥ 12.5 ng/µl  
- **Purity**: A260/280 between 1.8 – 2.0  

If requirements fail, sequencing may still be possible, but with **increased risk of poor results**.

## 3. Sequencing Coverage

### Definitions
- **Coverage (breadth)** → % of target bases sequenced at least “X” times.  
- **Depth of coverage** → average number of times each base is sequenced.  

\[
\text{Depth of Coverage} = \frac{L \times N}{G}
\]

Where:  
- **L** = read length  
- **N** = number of reads  
- **G** = haploid genome length  

Expressed as “X-fold” (e.g., 10x, 20x, 40x).  

### Examples
- **5x coverage** → each base sequenced ~5 times (low reliability, missing variants).  
- **20x coverage** → sufficient for **variant discovery (SNPs/indels)**.  
- **40x coverage** → high-quality genome resequencing (each base seen ≥40 times).  
- **Genome assembly** → requires **much higher depth** and often long-read technologies.  

## 4. Why Coverage Matters
- **Variant discovery** → ≥20x needed for reliable SNP/indel detection.  
- **Clinical genomics** → high coverage required to avoid missing pathogenic variants.  
- **De novo assembly** → high depth + long reads needed to resolve repeats and structural variants.  

## Key Takeaways
- DNA purity (A260/280, A260/230) and integrity are **critical QC steps** for NGS.  
- Poor quality samples reduce yield and accuracy, especially in **long-read sequencing**.  
- Coverage = both **breadth (% bases covered)** and **depth (times each base is read)**.  
- **20x coverage** is standard for variant discovery, while **higher depth** is required for assembly and complex genomes.  
