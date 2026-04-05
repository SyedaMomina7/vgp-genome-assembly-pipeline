# Scaffolding

Following contig assembly, two sequential scaffolding stages were performed to organize 
contigs into chromosome-level scaffolds. This corresponds to the third and fourth major 
stages of the GTN Vertebrate Genome Assembly pipeline.

---

### 🔧 Tools
- **Bionano Solve** — Hybrid scaffolding using optical map data
- **YaHS** — Chromosome-level scaffolding using Hi-C chromatin contact data

---

### Stage 1 — Bionano Hybrid Scaffolding

Bionano optical map data was integrated with the Hap1 contig assembly using 
**Bionano Solve** to produce a hybrid scaffold. Optical maps provide long-range 
structural information that bridges gaps between contigs which Hi-C alone cannot resolve.

**Inputs:**
- Hap1 contig FASTA
- Bionano optical map (`.cmap`)

**Outputs:**

| Output | Description |
|--------|-------------|
| `hybrid_scaffold.fasta` | Bionano scaffolded assembly |
| `hybrid_scaffold.agp` | Scaffold-to-contig coordinate map |
| `conflicts.txt` | Optical map conflict report |

---

### Stage 2 — YaHS Hi-C Scaffolding

The Bionano-scaffolded assembly was further scaffolded using **YaHS**, which uses 
Hi-C chromatin contact frequencies to determine the correct order and orientation 
of scaffolds, producing final chromosome-level pseudomolecules.

**Inputs:**
- Bionano hybrid scaffold FASTA
- Hi-C forward reads (R1) and reverse reads (R2)

**Outputs:**

| Output | Description |
|--------|-------------|
| `yahs_scaffolds.fasta` | Final chromosome-level scaffold assembly |
| `yahs_scaffolds.agp` | Final scaffold coordinate map |
| `scaffolding_results` | YaHS scaffolding result files |
| `break_files` | Scaffold break-point files |

---

###  Scaffold Statistics (gfastats)

| Metric | Value |
|--------|-------|
| Total Scaffold Length (bp) | 23,518,328 |
| Number of Scaffolds | 30 |
| Scaffold N50 (bp) | 1,125,120 |
| Scaffold L50 | 8 |
| Largest Scaffold (bp) | 2,181,538 |

---

### Hi-C Contact Map (PretextMap)

After YaHS scaffolding, Hi-C reads were aligned to the final scaffold assembly 
and visualized using **PretextMap** and **PretextSnapshot**. The contact map 
confirms correct scaffold ordering — well-assembled chromosomes appear as 
distinct diagonal blocks along the matrix.

| Output | Description |
|--------|-------------|
| `pretext_map.pretext` | Hi-C contact map file |
| `pretext_snapshot.png` | Contact map image — post scaffolding |

---

###  Why Two Scaffolding Stages?

Bionano optical maps resolve large structural gaps using enzyme-labelled 
long-range physical maps, while Hi-C data uses chromatin interaction frequencies 
to order and orient scaffolds at the chromosome scale. Together they are 
complementary — Bionano improves local contiguity while Hi-C provides 
global chromosome-level organization.

---

### 🔗 Reference
[GTN Vertebrate Genome Assembly Tutorial](https://training.galaxyproject.org/training-material/topics/assembly/tutorials/vgp_genome_assembly/tutorial.html)
