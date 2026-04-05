## Preprocessing

Tool: Cutadapt  

- Removed adapter sequences from HiFi reads  
- Generated clean reads for assembly

Raw input reads were quality-filtered and adapter-trimmed prior to assembly using Cutadapt on the Galaxy platform (usegalaxy.eu), as part of the GTN Vertebrate Genome Assembly pipeline.

### HiFi reads:
Adapter sequences were removed from PacBio HiFi reads and collapsed into a clean collection, which was then passed directly into k-mer counting (Meryl) and contig assembly (HiFiasm)
### Hi-C reads:
Forward (R1) and reverse (R2) Illumina Hi-C read pairs were independently trimmed; cleaned pairs were used for both haplotype phasing in HiFiasm and chromosome-level scaffolding in YaHS
### Bionano data:
Optical map data (.cmap) required no preprocessing and was used directly in the hybrid scaffolding step with Bionano Solve

Trimmed HiFi reads served as input to both the genome profiling stage (GenomeScope + Meryl) and the Hi-C phased assembly stage (HiFiasm), making this a critical quality-determining step for all downstream analyses.
