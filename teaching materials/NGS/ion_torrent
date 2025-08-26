# Ion Torrent Sequencing System

## Overview
Ion Torrent (now Thermo Fisher **Ion S5 System**) is a **short-read NGS technology** based on **semiconductor sequencing**.  
- Instead of using fluorescence or optics, the system detects **pH changes** caused by nucleotide incorporation.  
- Sequencing occurs in **tiny wells on a silicon chip**, each acting as an independent reaction chamber.  
- Each well = one DNA fragment × thousands of clonal copies (to amplify signal).  

## Technology
### Chips
- The **chip** is the core of the Ion Torrent system.  
- About the size of a **2€ coin**, containing **millions of wells**.  
- Each well = one sequencing reaction, with a **pH sensor** to detect ions.  
- DNA fragments are loaded into wells and sequenced in parallel.  
- Different chip models = different throughput (scalability).  
  - Example: Chip 510 → **2.5 Gb output (~2.3 million reads)**.  

### Sequencing Principle
1. DNA fragments are engineered with **universal primer sites**.  
2. One nucleotide type (A, T, C, or G) is flowed across the chip at a time.  
3. If complementary, the polymerase adds it to the DNA strand, releasing:  
   - **H⁺ ions** (detected as a pH change)  
   - **Pyrophosphate**  
4. Each pH change = incorporation event → converted into digital signal.  
5. Signal intensity is proportional to the number of identical nucleotides added (homopolymers).  

## Library & Template Preparation
- **DNA fragmentation**:  
  - Sonication (physical)  
  - Enzymatic digestion  
- **Library preparation**: fragments engineered with adapters + universal primer sites.  
- **Barcoding**:  
  - Allows multiplexing (samples from multiple individuals).  
  - >300 barcodes possible.  
- **Clonal amplification**:  
  - Performed by **emulsion PCR** (one DNA fragment per micro-droplet).  
  - Creates thousands of copies of the same DNA fragment.  
  - Goal: 1 DNA fragment per sphere → avoids **polyclonals** (mixed signals).  

## Flow & Sequencing
- Sequencing occurs by **programmed flows** of nucleotides (e.g., TACG).  
- Homopolymer regions (AAA… or TTT…) → **signal proportionality problem** → higher error rate.  
- Output is displayed in **ionograms**, similar to electropherograms.  

## Strengths
- **Fast** and relatively **cheap** (no fluorescently modified nucleotides).  
- Simple chemistry → low reagent cost.  
- Highly scalable with different chips.  
- Supports barcoding → cost-efficient multiplexing.  

## Weaknesses
- **Error-prone in homopolymer regions** (cannot always distinguish 3 vs 4 identical bases).  
- Requires careful **DNA quantification** to avoid:  
  - **Polyclonals** (multiple templates per sphere)  
  - **Empty wells** (no template loaded)  
- Chips are **single-use** and relatively expensive.  
- Read length limited (~300–400 bp).  

## Workflow Summary
1. **DNA fragmentation** → sonication or enzymatic  
2. **Library prep** → adapters + barcodes  
3. **Emulsion PCR** → clonal amplification  
4. **Chip loading** → DNA-loaded beads into wells  
5. **Sequencing** → ion detection via pH sensors  
6. **Data output** → Torrent Suite software for quality control & read statistics  

## Data & Analysis
- **Reads**: short fragments (≤400 bp).  
- **Data filtering** is essential:  
  - Remove low-quality or polyclonal reads  
  - Check percentage of duplicated reads  
  - Monitor well usage efficiency  
- **Torrent Suite** software provides:  
  - Average read length  
  - Quality statistics  
  - % of usable wells  
  - Error diagnostics  
