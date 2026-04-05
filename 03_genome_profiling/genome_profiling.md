## Genome Profiling

Prior to assembly, a genome profile was generated from the trimmed HiFi reads to characterize the genome and inform all downstream assembly parameters. This stage corresponds to the first major section of the GTN Vertebrate Genome Assembly pipeline.

Tools: Meryl, GenomeScope2  

- Performed k-mer counting  
- Estimated genome size  
- Estimated heterozygosity  


#### Meryl:
Counted k-mer frequencies (k=21) across all trimmed HiFi reads to build a k-mer database, which was then used to generate a frequency histogram and passed into GenomeScope2 for modelling
#### GenomeScope2:
Modelled the k-mer histogram to produce reference-free estimates of genome size, heterozygosity rate, and repeat content; the estimated haploid coverage was then directly fed into HiFiasm to guide contig assembly
#### Merqury:
Used the Meryl k-mer database post-assembly to compute a QV (quality value) score and k-mer completeness for both haplotypes, providing a reference-free accuracy estimate of the final assembly
