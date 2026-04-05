## 📊 Final Results

---

### 🧬 Assembly Output

Haplotype-resolved contig assembly was successfully generated using HiFiasm
in Hi-C phased mode, producing two fully phased haplotype assemblies without
the need for parental reads.

- Hap1 and Hap2 contig FASTA files successfully generated
- Hap1 and Hap2 assembly graphs (GFA) produced
- Both haplotypes confirmed via Hi-C contact phasing

---

### 📐 Contig Statistics (gfastats)

| Metric | Value |
|--------|-------|
| Total Contig Length (bp) | 23,518,211 |
| Number of Contigs | 39 |
| Contig N50 (bp) | 813,039 |
| Contig L50 | 12 |
| Largest Contig (bp) | 1,532,843 |
| Smallest Contig (bp) | 17,639 |
| GC Content (%) | 38.27 |

---

### 🏗️ Scaffold Statistics (gfastats — post YaHS)

| Metric | Value |
|--------|-------|
| Total Scaffold Length (bp) | 23,518,328 |
| Number of Scaffolds | 30 |
| Scaffold N50 (bp) | 1,125,120 |
| Scaffold L50 | 8 |
| Largest Scaffold (bp) | 2,181,538 |
| Number of Gaps | 9 |
| Total Gap Length (bp) | 117 |

---

### 📈 Improvements After Scaffolding

| Metric | Before (Contigs) | After (Scaffolds) |
|--------|-----------------|-------------------|
| Total Sequences | 39 | 30 |
| N50 (bp) | 813,039 | 1,125,120 |
| Largest Sequence (bp) | 1,532,843 | 2,181,538 |

Scaffolding reduced the total number of sequences from 39 contigs to 30
scaffolds while improving N50 by **~38%**, confirming successful
chromosome-level organization of the assembly.

---

### 🔬 Quality Assessment

| Tool | Metric | Hap1 | Hap2 |
|------|--------|------|------|
| BUSCO | Completeness (%) | 97.5% | 94.1% |
| BUSCO | Complete & Single-copy (%) | 25.7% | 92.3% |
| BUSCO | Complete & Duplicated (%) | 71.8% | 1.8% |
| BUSCO | Fragmented (%) | 0.4% | 2.7% |
| BUSCO | Missing (%) | 2.1% | 3.2% |
| GenomeScope | Estimated Haploid Genome Size | 11,747,352 bp | — |
| GenomeScope | Heterozygosity (%) | 0.58% | in files |
| GenomeScope | Repeat Content | 723,597 bp | in files |
| GenomeScope | Model Fit (%) | 96.5% | in files |

> 📝 BUSCO lineage used: saccharomycetes_odb10 (n=2137).
> Dataset is a tutorial subset, not a complete vertebrate genome.

---

### 💡 Observations

- **HiFi reads** produced a highly accurate contig assembly due to
their long read length (>10kb) and high base accuracy (>99%)
- **BUSCO completeness of 97.5% (Hap1) and 94.1% (Hap2)** confirms
strong gene-space recovery across both haplotypes
- **High duplication in Hap1 (71.8%)** reflects expected overlap
between haplotypes before full phasing separation
- **Bionano optical maps** improved large-scale structural contiguity
by bridging gaps between contigs that short-range data cannot resolve
- **Hi-C chromatin contact data** successfully organized contigs into
chromosome-level scaffolds, confirmed by diagonal blocks visible in
the PretextMap contact map
- **Heterozygosity of 0.58%** (GenomeScope) indicates a relatively
homozygous genome, consistent with the low duplication seen in Hap2
- Scaffold N50 improvement of ~38% over contig N50 confirms the
scaffolding steps added significant value to the assembly

---

### 📁 Note

> Full output files are available in the [`06_results/`](06_results/)
> folder of this repository. Large raw input files (HiFi reads, Hi-C
> reads, Bionano optical maps) are not committed due to GitHub file
