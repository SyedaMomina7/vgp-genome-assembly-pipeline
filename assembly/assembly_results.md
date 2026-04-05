## Results

-## 🧬 Assembly

Haplotype-resolved contig assembly was performed using **HiFiasm** in Hi-C phasing mode, following the GTN Vertebrate Genome Assembly pipeline. HiFiasm simultaneously assembled and phased the two haplotypes using PacBio HiFi reads and Hi-C chromatin contact information, producing a fully diploid assembly without the need for parental reads.

---

### 🔧 Tool
**HiFiasm** (Hi-C phased mode)

---

### 📥 Inputs
- Trimmed PacBio HiFi reads (collapsed collection)
- Hi-C forward reads (R1) and reverse reads (R2)
- Homozygous coverage estimate from GenomeScope2


### 📊 Assembly Statistics

| Metric | Value |
|--------|-------|
| Total Length (bp) | 23,518,211 |
| Number of Contigs | 39 |
| Contig N50 (bp) | 813,039 |
| Contig L50 | 12 |
| Largest Contig (bp) | 1,532,843 |
