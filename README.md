# vgp-genome-assembly-pipeline

##  Overview

This repository contains the complete workflow, results, and documentation 
for a **chromosome-level, haplotype-resolved vertebrate genome assembly** 
executed using the [Vertebrate Genomes Project (VGP)](https://vertebrategenomesproject.org/) 
pipeline on the **Galaxy platform (usegalaxy.eu)**.

The pipeline integrates three complementary sequencing technologies to produce 
a high-quality diploid genome assembly:

| Technology | Tool | Purpose |
|------------|------|---------|
| PacBio HiFi | HiFiasm | High-accuracy long-read contig assembly |
| Bionano Optical Maps | Bionano Solve | Large-scale structural scaffolding |
| Illumina Hi-C | YaHS | Chromosome-level scaffolding & phasing |

---


##  Pipeline Steps

### 1.  Data Import
- HiFi reads, Hi-C reads, and Bionano optical map imported from 
**Zenodo** via the GTN tutorial
- All datasets uploaded directly into a Galaxy history on usegalaxy.eu

---

### 2.  Preprocessing
**Tool:** Cutadapt
- Adapter sequences trimmed from PacBio HiFi reads
- Hi-C forward (R1) and reverse (R2) reads independently trimmed
- Clean reads collapsed into a collection for downstream assembly

---

### 3.  Genome Profiling
**Tools:** Meryl → GenomeScope2

- K-mer frequencies counted at k=21 from trimmed HiFi reads using **Meryl**
- K-mer histogram modelled by **GenomeScope2** to estimate:
  - Genome size
  - Heterozygosity rate
  - Repeat content
- Haploid coverage estimate passed directly into HiFiasm

---

### 4.  Contig Assembly
**Tool:** HiFiasm (Hi-C phased mode)

- HiFi reads and Hi-C pairs assembled simultaneously into two 
phased haplotypes
- Outputs:
  - Hap1 contigs (FASTA + GFA graph)
  - Hap2 contigs (FASTA + GFA graph)

---

### 5.  Assembly QC
**Tools:** gfastats, BUSCO, Merqury

- **gfastats** — computed N50, L50, contig count, total assembly length
- **BUSCO** — assessed gene-space completeness against vertebrata_odb10
- **Merqury** — computed reference-free QV score and k-mer completeness 
for both haplotypes

---

### 6.  Scaffolding
**Tools:** Bionano Solve → YaHS

- **Bionano Solve** — integrated optical map data with Hap1 contigs 
to produce a hybrid scaffold
- **YaHS** — used Hi-C chromatin contact frequencies to order and 
orient scaffolds into chromosome-level pseudomolecules
- **PretextMap + PretextSnapshot** — generated Hi-C contact maps 
to visually confirm correct chromosome-level scaffolding

---

### 7.  Final Evaluation
**Tools:** gfastats, BUSCO (rerun on final scaffolds)

- Scaffold-level statistics computed and compared against contig-level metrics
- BUSCO completeness confirmed on final scaffolded assembly
- Hi-C contact map inspected for clean diagonal chromosome blocks
---

##  Key Results

| Metric | Value |
|--------|-------|
| Total Scaffold Length (bp) | 23,518,328 |
| Number of Scaffolds | 30 |
| Scaffold N50 (bp) | 1,125,120 |
| Scaffold L50 | 8 |
| Largest Scaffold (bp) | 2,181,538 |
| Total Contig Length (bp) | 23,518,211 |
| Number of Contigs | 39 |
| Contig N50 (bp) | 813,039 |
| Contig L50 | 12 |
---

##  Tools Used

| Tool | Purpose |
|------|---------|
| **Cutadapt** | Adapter trimming of HiFi and Hi-C reads |
| **Meryl** | K-mer counting (k=21) |
| **GenomeScope2** | Genome size & heterozygosity estimation |
| **HiFiasm** | HiFi + Hi-C phased contig assembly |
| **gfastats** | Assembly statistics (N50, L50, total length) |
| **BUSCO** | Gene-space completeness assessment |
| **Merqury** | Reference-free QV score & k-mer completeness |
| **Bionano Solve** | Optical map hybrid scaffolding |
| **YaHS** | Hi-C chromosome-level scaffolding |
| **PretextMap** | Hi-C contact map generation |
| **PretextSnapshot** | Contact map image export |

---
---
##  Documentation

Detailed documentation for each pipeline stage is available in the `docs/` folder:

- [Workflow](/workflow.md) — Complete step-by-step pipeline
- [Preprocessing](/preprocessing.md) — Read trimming details
- [Genome Profiling](/genome_profiling.md) — K-mer analysis & genome estimation
- [Assembly](/assembly.md) — HiFiasm contig assembly
- [Scaffolding](/scaffolding.md) — Bionano & YaHS scaffolding
- [Results](results/) — All major output files from each pipeline stage

---
##  Screenshots
(see images folder)

---
## 👤 Author

**SYEDA MOMINA ASSAD**
*
NUST  

Specail topics in bioinfomatics*

*5TH , APRIL'26*

Supervisor: *Sir Tanveer*

---
##  Reference
Galaxy Training Tutorial:
https://training.galaxyproject.org/training-material/topics/assembly/tutorials/vgp_genome_assembly/tutorial.html
