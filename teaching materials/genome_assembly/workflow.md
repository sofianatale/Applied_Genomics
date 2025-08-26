# Genome Assembly

## Introduction
After sequencing, **genome assembly** is required whenever no reference genome is available to perform alignments.  
Genome assembly can serve multiple purposes:
- Create a reference genome for a species that does not yet have one.
- Improve an existing reference genome that may be incomplete or low quality.

Genome assembly is closely related to **genome annotation**, since knowing where reads belong is fundamental to reconstruct the full genome.  
Because de novo genome assembly and annotation require a large amount of computational power and time, researchers must carefully evaluate whether a new assembly is needed or if an available reference can be used.

## Shotgun Sequencing
Shotgun sequencing is the first step in genome assembly:
1. DNA is extracted from the sample.
2. The DNA is fragmented to build a sequencing library.
3. Overlaps between fragments are detected to reconstruct long stretches of DNA.

### Hierarchical Shotgun Sequencing
- Historically used when no genomes had been sequenced before.
- Genome cut into **large fragments (contigs)** → cloned into **BAC libraries** (Bacterial Artificial Chromosomes).
- Each BAC subjected to shotgun sequencing and assembled separately.
- Final genome reconstructed by aligning BAC-derived assemblies.
- **Nowadays:** due to improved computational resources, hierarchical approaches are mostly abandoned in favor of direct whole-genome shotgun sequencing.

## Experimental Workflow
Before starting de novo assembly, researchers must ensure adequate **computational resources**.  
Steps include:
1. **Sample collection** → obtain representative tissue samples (some can be saved for RNA-seq, useful for annotation).
2. **DNA extraction** → choice of long-read vs short-read sequencing.
   - **Long reads** (PacBio, Nanopore): better assembly continuity.
   - **Short reads** (Illumina, ~150 bp): higher coverage but harder assembly.

## Ten Steps of Genome Assembly
1. **Gather information about the genome**  
   - Genome size (C-value, flow cytometry, or related species databases).  
   - Complexity: repeats, heterozygosity, ploidy.  
   - Alternative estimation: **k-mer frequency distribution**.

2. **Extract high-quality DNA**  
   - Long stretches (up to 20 kbp) for long-read sequencing.  
   - Short reads used if DNA is degraded.  
   - Minimize contamination (e.g., mitochondrial DNA, chloroplast DNA).

3. **Design the experimental workflow**  
   - Define goals, budget, sequencing depth (≥ 60x recommended).  
   - Choose library type: single-end, paired-end, mate-pair, PCR-free.  
   - Select between **de novo** vs **reference-guided** assembly.

4. **Choose sequencing technology & library preparation**  
   - Illumina: cheap, short reads, high throughput.  
   - PacBio / Nanopore: long reads, more expensive.  
   - Hybrid approaches combine both.  
   - Hi-C, BioNano, optical mapping used for scaffolding.

5. **Ensure adequate computational resources**  
   - Requirements depend on genome size and ploidy.  
   - Example: diploid genome (~1 Gb) → 96 CPUs, 1 TB RAM, 3 TB local + 10 TB shared storage.  
   - Cloud computing (e.g., AWS) is often used.

6. **Assemble the genome**  
   - Pre-process reads (QC, filtering).  
   - Choose assembly algorithms suited for data type.  
   - Produce first draft genome.

7. **Validate the assembly**  
   - Check for misassemblies.  
   - Aim: long contigs, minimal fragmentation, accurate scaffolds.

8. **Polish the assembly**  
   - Correct errors.  
   - Improve consensus sequence using additional reads.

9. **Scaffold and chromosome assembly**  
   - Combine contigs into scaffolds.  
   - Use Hi-C / BioNano data to reach chromosome-scale assembly.

10. **Genome annotation**  
   - Use RNA-seq and other functional data to map genes and regulatory elements.

## Challenges in Genome Assembly
- **Repeats** → cause misassembly (solved with long reads or flanking strategies).  
- **Heterozygosity** → increases mismatches, causes fragmented assemblies.  
- **Ploidy** → higher ploidy complicates assembly.  
- **GC content bias** → Illumina struggles with very high/low GC, PacBio/Nanopore handle better.  
- **Species-specific factors** → repetitive DNA, polymorphism levels, etc.


## Summary
Genome assembly is a multi-step, computationally demanding process requiring careful **experimental design**, **choice of sequencing technology**, and **bioinformatics strategies**.  
Modern pipelines integrate long-read sequencing, hybrid approaches, and advanced scaffolding technologies to achieve **chromosome-level assemblies**, followed by **annotation** to interpret genomic content.

