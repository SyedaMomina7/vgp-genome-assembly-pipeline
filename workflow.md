## Workflow Explanation

---

###  Step-by-Step Pipeline

---

#### Step 1  Data Import
- Imported all raw input datasets from **Zenodo** via the GTN tutorial links
- Datasets included: PacBio HiFi reads, Hi-C paired-end reads (R1 + R2), 
and Bionano optical map (`.cmap`)
- All data was imported directly into a Galaxy history on usegalaxy.eu

---

#### Step 2  Preprocessing (Cutadapt)
- Adapter sequences were trimmed from HiFi reads using **Cutadapt**
- Hi-C forward and reverse reads were independently trimmed
- Trimmed HiFi reads were collapsed into a clean collection for downstream use

---

#### Step 3  Genome Profiling (Meryl + GenomeScope2)
- K-mer frequencies (k=21) were counted from trimmed HiFi reads using **Meryl**
- A k-mer histogram was generated and modelled by **GenomeScope2**
- Outputs: estimated genome size, heterozygosity rate, repeat content
- Haploid coverage estimate was passed directly into HiFiasm

---

#### Step 4  Contig Assembly (HiFiasm)
- **HiFiasm** was run in Hi-C phased mode using trimmed HiFi reads and 
Hi-C read pairs
- Produced fully phased Hap1 and Hap2 contig assemblies
- Output: Hap1 FASTA, Hap2 FASTA, Hap1 GFA graph, Hap2 GFA graph

---

#### Step 5 Assembly Quality Assessment
- **gfastats** computed contig-level statistics (N50, L50, total length)
- **BUSCO** assessed gene-space completeness against the vertebrata_odb10 lineage
- **Merqury** computed reference-free QV score and k-mer completeness 
for both haplotypes

---

#### Step 6 Bionano Hybrid Scaffolding (Bionano Solve)
- Hap1 contigs were scaffolded with Bionano optical map data using 
**Bionano Solve**
- Outputs: hybrid scaffold FASTA, AGP coordinate file, conflict report

---

#### Step 7  Hi-C Scaffolding (YaHS)
- The Bionano-scaffolded assembly was further scaffolded using **YaHS**
- Hi-C chromatin contact frequencies were used to order and orient scaffolds 
into chromosome-level pseudomolecules
- Outputs: final scaffold FASTA, AGP file, scaffolding result files

---

#### Step 8  Contact Map Visualization (PretextMap)
- Hi-C reads were aligned to the final scaffold assembly
- **PretextMap** generated a Hi-C contact map
- **PretextSnapshot** exported high-resolution PNG images for visual inspection
- Clear diagonal blocks in the contact map confirm successful 
chromosome-level scaffolding

---

#### Step 9 — Final Quality Assessment
- **gfastats** rerun on final scaffolds to compute scaffold-level statistics
- **BUSCO** rerun on final scaffolds to confirm gene completeness was maintained
- Results compared against pre-scaffolding metrics to verify improvement
