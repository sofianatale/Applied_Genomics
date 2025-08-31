# Fixation Index – F-statistics (F_ST)

**F_ST** is a population genetics parameter used at the **population genomics** level to quantify **genetic differentiation** between populations (defined by Fisher).

## Definition
For a locus (or genomic window),
\[
F_{ST}=\frac{H_T - H_S}{H_T}
\]
where:
- \(H_T\) = total (pooled) expected heterozygosity,
- \(H_S\) = average expected heterozygosity **within** populations.

## Interpretation
- **\(F_{ST}=1\)** → two populations are **completely different** (e.g., pop1 fixed for allele A, pop2 fixed for allele B).
- **\(F_{ST}=0\)** → populations are **identical** (same allele frequencies).
- **0 < \(F_{ST}\) < 1** → populations share alleles but with **different frequencies** (e.g., A more frequent in pop1, B more frequent in pop2).

## Window-based estimation and plotting
- Divide the genome into windows (e.g., **1 Mb**) and compute \(F_{ST}\) per window to reduce noise and capture **linkage disequilibrium** signals.
- Plot window \(F_{ST}\) values across chromosomes (Manhattan-style): **higher windows = greater differentiation**.

## Study designs and data types
- Works with **SNP chips** or **whole-genome sequencing**.
- With limited budgets, use **DNA pooling (Pool-Seq)** to estimate population allele frequencies:
  - Pool equal DNA amounts from each individual (**equimolar**).  
  - Keep the pool size moderate to minimize technical error in DNA quantification and allele-frequency estimation.

## Practical workflow (conceptual)
1. **Sequence/genotype** individuals or pools.
2. **Call variants** and **estimate allele frequencies** (depth-aware for Pool-Seq/WGS).
3. Compute **per-SNP \(F_{ST}\)**, then **average within windows** to obtain robust regional estimates.
4. Perform **pairwise comparisons** for all population pairs (breed vs breed), or **group contrasts** (e.g., all black-coat breeds vs others).
5. Visualize results (Manhattan plot), **interpret high-\(F_{ST}\)** windows, annotate genes, and generate **biological hypotheses** (e.g., local adaptation such as trypanosome resistance).

## Notes
- \(F_{ST}\) compares **genetic diversity between vs within** populations of the same species.
- When planning, define: number of individuals, number of comparisons, platform (SNP chip vs WGS), **coverage/depth**, and costs.
