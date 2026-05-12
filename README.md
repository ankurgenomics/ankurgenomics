<div align="center">

# Ankur Sharma, PhD

### Senior ML & Agentic AI Engineer

Building production multi-agent systems and reasoning-traceable AI for science.

[![Email](https://img.shields.io/badge/Email-ankurs103%40gmail.com-blue?style=flat-square&logo=gmail)](mailto:ankurs103@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ankurit-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/ankurit/)
[![Portfolio](https://img.shields.io/badge/Portfolio-View-00FFC6?style=flat-square)](https://ankurgenomics.github.io/agentic-genomics/)
[![Google Scholar](https://img.shields.io/badge/Scholar-Publications-4285F4?style=flat-square&logo=google-scholar)](https://doi.org/10.32657/10356/155390)

---

**8+ years** production ML & bioinformatics | **PhD** NTU Singapore | **Singapore (PR)**

LangGraph · Claude API · Multi-Agent Systems · AWS · Nextflow · Clinical Genomics

</div>

---

## 🤖 Featured Agentic AI Projects

### 🦠 [outbreak-agent](https://github.com/ankurgenomics/outbreak-agent) — Infectious Disease Triage Pipeline
**New** | LangGraph · Python · matplotlib · ReportLab

4-node LangGraph state machine for infectious disease outbreak triage. Built around the April 2026 MV Hondius / Andes virus event -- the first confirmed human-to-human hantavirus transmission on a cruise ship. Self-correcting critic loop re-evaluates when outputs are inconsistent.

**Tech:** LangGraph 0.6, LangChain, matplotlib, ReportLab, pytest
```bash
git clone https://github.com/ankurgenomics/outbreak-agent
cd outbreak-agent && pip install -r requirements.txt
python demo.py --case hondius   # CRITICAL 98/100, under 2 seconds, no API key
```

- 33 tests passing, completely free to run (no API key required)
- Generates 3-panel risk dashboard (PNG) + structured PDF triage report automatically
- Blog: [When an AI Agent Boards a Cruise Ship](https://ankurgenomics.github.io/2026/05/09/hantavirus-cruise-ship-agentic-ai.html)

---

### 🧬 [agentic-genomics](https://github.com/ankurgenomics/agentic-genomics) — GenomicsCopilot
**Flagship open-source project** | LangGraph · Claude · Python

Reasoning-traceable agent for variant interpretation. 7 deterministic nodes (VCF ingest → gnomAD/ClinVar lookup → ACMG-lite classification → HPO phenotype scoring) + LLM synthesizer + critic for fact-checking. Every call leaves a full audit trail.

**Tech:** LangGraph, Claude/Anthropic API, Pydantic v2, pysam, Streamlit, Typer CLI
```bash
pip install agentic-genomics
genomics-copilot analyze variants.vcf --phenotypes HPO:0001250
```

- 📖 [Why agentic AI for genomics?](https://github.com/ankurgenomics/agentic-genomics/blob/main/docs/why-agentic.md)
- 🏗️ [System architecture](https://github.com/ankurgenomics/agentic-genomics/blob/main/docs/architecture.md)
- ⚠️ [Limitations & prior art](https://github.com/ankurgenomics/agentic-genomics/blob/main/LIMITATIONS.md)

---

### 🛠️ [genomics-skills](https://github.com/ankurgenomics/genomics-skills) — Agent-Callable Skill Library
**8 production-quality genomics skills** | Python · Claude Haiku · REST APIs

The downstream skill layer for agentic-genomics. Each skill is agent-discoverable with a SKILL.md contract, CLI entrypoint, and deterministic outputs (TSV + PNG/SVG). LLM-powered routing via Claude Haiku maps natural-language queries to the right skill.

**Skills:** TCGA pan-cancer expression (9,479 real samples) · Kaplan-Meier survival (Cox PH) · GO/KEGG enrichment · PubMed search · Protein variant mapper · 3D structure viewer · Volcano plots

**Tech:** Python, Claude Haiku (LLM routing), cBioPortal/MyVariant/NCBI/PDB APIs, Pandas, Matplotlib
```bash
genomics-skill suggest "show me survival data for BRCA1 in breast cancer"
genomics-skill run tcga-expression --gene TP53 --mode pan-cancer
```

---

### 🔧 GenomicsOps AI
**Personal side project** | Multi-agent orchestration · Claude API · RAG

5 specialized agents (Trigger → Log Fetcher → RAG → Classifier → JIRA Writer) built on weekends to explore autonomous diagnosis of genomic pipeline failures (DRAGEN, ICA, SGE/HPC).

**Tech:** Multi-agent orchestration, Claude API, RAG, Python, JIRA/Confluence APIs

---

### ☁️ Autonomous Genomic Pipelines
**Production cloud infrastructure** | AWS · Nextflow · Step Functions

Self-optimizing WGS/RNA-seq workflows on AWS with adaptive resource allocation and automated QC gating. Processed 6,000+ samples with minimal human intervention.

**Impact:**
- 40% ↓ compute costs
- 50% ↓ storage footprint
- 400 TB genomic data managed

**Tech:** Nextflow (DSL2), AWS Batch, Lambda, Step Functions, Docker, IaC

Related work: [gwas_nf](https://github.com/ankurgenomics/gwas_nf) — Nextflow pipeline for GWAS

---

## 📊 GitHub Stats

<div align="center">

![Ankur's GitHub stats](https://github-readme-stats.vercel.app/api?username=ankurgenomics&show_icons=true&theme=dark&hide_border=true&bg_color=0d1117&title_color=00FFC6&icon_color=05BFDB&text_color=F0F4F8)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=ankurgenomics&layout=compact&theme=dark&hide_border=true&bg_color=0d1117&title_color=00FFC6&text_color=F0F4F8)

</div>

---

## 🛠️ Technical Stack

### Agentic AI & LLMs
![LangGraph](https://img.shields.io/badge/LangGraph-Core-00FFC6?style=flat-square)
![Claude](https://img.shields.io/badge/Claude_API-Core-05BFDB?style=flat-square)
![Multi-Agent](https://img.shields.io/badge/Multi--Agent-Core-00FFC6?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-Frequent-05BFDB?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI-Frequent-05BFDB?style=flat-square)

### ML & Data Science
![Python](https://img.shields.io/badge/Python-Core-3776AB?style=flat-square&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Core-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-Frequent-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Core-150458?style=flat-square&logo=pandas&logoColor=white)

### Cloud & Infrastructure
![AWS](https://img.shields.io/badge/AWS-Core-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Core-2496ED?style=flat-square&logo=docker&logoColor=white)
![Nextflow](https://img.shields.io/badge/Nextflow-Core-00FFC6?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-Frequent-2088FF?style=flat-square&logo=github-actions&logoColor=white)

### Bioinformatics
![DRAGEN](https://img.shields.io/badge/DRAGEN-Core-00FFC6?style=flat-square)
![GATK](https://img.shields.io/badge/GATK-Core-05BFDB?style=flat-square)
![Bioconductor](https://img.shields.io/badge/Bioconductor-Frequent-276DC3?style=flat-square&logo=r&logoColor=white)
![NGS](https://img.shields.io/badge/NGS-Expert-00FFC6?style=flat-square)

---

## 📚 Publications & Research

**PhD Thesis** · NTU Singapore · 2021
[Age-dependent transcriptional and epigenetic alterations in mouse hepatocytes](https://doi.org/10.32657/10356/155390)

**Technical Writeup** · Open Source
[Why agentic AI for genomics? Designing reasoning-traceable variant interpretation](https://github.com/ankurgenomics/agentic-genomics/blob/main/docs/why-agentic.md)

**Blog Post** · May 2026
[When an AI Agent Boards a Cruise Ship: Hantavirus, LangGraph, and the Future of Outbreak Triage](https://ankurgenomics.github.io/2026/05/09/hantavirus-cruise-ship-agentic-ai.html)

**Conference Poster** · Cell Symposia, Chicago · 2019
Significance of hepatocyte polyploidization in liver physiology and pathology

**Peer-Reviewed** · Frontiers in Microbiology · 2018
[Antiproliferative and antioxidative bioactive compounds in marine-derived endophytic fungus](https://www.frontiersin.org/journals/microbiology)

---

## 🎯 What I'm Looking For

Senior / Staff ML Engineer · Agentic AI Engineer · Research Engineer · Applied Scientist . AI Manager > AI advisor 

Building autonomous reasoning systems that create real value in production — not just demos that impress on Twitter.

**Based in Singapore (PR)** — open to remote or relocation for the right team.

---

## 📫 Let's Connect

- 📧 **Email:** [ankurs103@gmail.com](mailto:ankurs103@gmail.com)
- 💼 **LinkedIn:** [linkedin.com/in/ankurit](https://www.linkedin.com/in/ankurit/)
- 🌐 **Portfolio:** [ankurgenomics.github.io](https://ankurgenomics.github.io/agentic-genomics/)
- 📄 **Resume:** [Download CV (PDF)](https://ankurgenomics.github.io/agentic-genomics/assets/Ankur_Sharma_Resume_2026.pdf)

---

<div align="center">

### 🔬 Building the future of AI-powered science, one traceable agent at a time.

![Profile Views](https://komarev.com/ghpvc/?username=ankurgenomics&color=00FFC6&style=flat-square)

</div>
