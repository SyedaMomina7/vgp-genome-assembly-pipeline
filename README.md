# vgp-genome-assembly-pipeline
# Vertebrate Genome Assembly Pipeline (VGP)

## 📌 Overview
This project implements the VGP genome assembly pipeline using Galaxy.

The goal is to assemble a genome using:
- HiFi reads
- Hi-C data
- Multiple quality control steps

---

## ⚙️ Pipeline Steps

### 1. Data Upload
- Uploaded HiFi reads from Zenodo
- Uploaded Hi-C reads

### 2. Preprocessing
Tool: Cutadapt  
- Trimmed adapters from HiFi reads

### 3. Genome Profiling
Tools:
- Meryl (k-mer counting)
- GenomeScope2

Output:
- Genome size estimation
- Heterozygosity

### 4. Assembly
Tool: Hifiasm  
Mode: Hi-C phased

Outputs:
- Hap1 contigs
- Hap2 contigs

### 5. Purging
Tool: purge_dups  
- Removed duplicate contigs

### 6. Scaffolding
- Hi-C scaffolding performed

### 7. Evaluation
- Checked assembly quality

---

## 📊 Results
- Genome size: 
- N50:
- Observations: 

---

## 🧪 Tools Used
- Galaxy Platform
- Cutadapt
- Meryl
- GenomeScope2
- Hifiasm
- purge_dups

---

## 📷 Screenshots
(see images folder)

---

## 📚 Reference
Galaxy Training Tutorial:
https://training.galaxyproject.org/training-material/topics/assembly/tutorials/vgp_genome_assembly/tutorial.html
