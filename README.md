<div align="center">

# Ankur Sharma, PhD

### Agentic AI · ML · Computational Biology

Building production multi-agent systems and reasoning-traceable AI for science.

<img width="2400" height="1792" alt="ai_ecosytem_upwork" src="https://github.com/user-attachments/assets/002e94f4-f8bd-4e49-9a15-d3e0c9267bd7" />
<img width="2400" height="1792" alt="work_type_skills_upwpork" src="https://github.com/user-attachments/assets/9e7793da-6728-4952-ab95-3788277d8781" />

<img width="2400" height="1792" alt="what_sets_this_project_aaprt_upwork" src="https://github.com/user-attachments/assets/4b1cfe6f-690a-47e3-b539-8793def5e3b3" />
<img width="2400" height="1792" alt="continue_imorivement_deployment_upwork" src="https://github.com/user-attachments/assets/b6543108-bee7-4cd6-905d-9a0c1eac000d" />






[![Email](https://img.shields.io/badge/Email-ankurs103%40gmail.com-blue?style=flat-square&logo=gmail)](mailto:ankurs103@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ankurit-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/ankurit/)
[![Portfolio](https://img.shields.io/badge/Portfolio-View-00FFC6?style=flat-square)](https://ankur-portfolio-v2-sandy.vercel.app/)
[![Google Scholar](https://img.shields.io/badge/Scholar-Publications-4285F4?style=flat-square&logo=google-scholar)](https://doi.org/10.32657/10356/155390)

---

**8+ years** production ML & bioinformatics | **PhD** NTU Singapore | **Singapore (PR)**

LangGraph · Claude API · Multi-Agent Systems · AWS · Nextflow · Clinical Genomics

</div>

---

## 🤖 Featured Projects

### 🧬 [genome-ft](https://github.com/ankurgenomics/genome-ft) — Fine-tuning a Genomic Foundation Model
**New** | PyTorch · Hugging Face Transformers · Nucleotide Transformer v2

Full weight-level fine-tuning of [Nucleotide Transformer v2 50M](https://huggingface.co/InstaDeepAI/nucleotide-transformer-v2-50m-multi-species) (InstaDeep, a genomic foundation model) on two GenomicBenchmarks DNA classification tasks. All 53.8M parameters are updated, not LoRA or a frozen head. The emphasis is the evaluation protocol rather than the headline number: a leakage-free train/validation/test split, the test set scored exactly once, three random seeds with reported variance, and the base model measured under the identical pipeline.

**Tech:** PyTorch (Apple MPS), Hugging Face Transformers, AdamW with warmup + cosine decay, reverse-complement augmentation, validation-based checkpoint selection
```bash
git clone https://github.com/ankurgenomics/genome-ft
cd genome-ft && pip install -r requirements.txt
python prepare_data.py && python train.py   # reproduces the fine-tune end-to-end
```

- Enhancers (`human_enhancers_cohn`, 3 seeds): accuracy 0.735, MCC 0.478 ± 0.003 (base model at chance, MCC −0.009)
- Promoters (`human_nontata_promoters`): accuracy 0.872, MCC 0.747
- Validation MCC peaked at epoch 1–2 then declined, so a low learning rate and validation-based selection matter more than longer training
- 🤗 Model card: [ankur0050/nucleotide-transformer-v2-50m-genomicbenchmarks-ft](https://huggingface.co/ankur0050/nucleotide-transformer-v2-50m-genomicbenchmarks-ft)

---

### 🩺 [Reviewer2](https://github.com/ankurgenomics/Reviewer2) — Autonomous ACMG Variant Second Reviewer
**New** | LangGraph · FastMCP · MCP Server · Pydantic v2 · Python

Clinical genomics has a consistency problem. Two trained analysts applying the same 28-criterion ACMG framework to the same variant routinely reach different calls. Reviewer2 acts as an autonomous second reviewer: feed it a variant and a proposed classification, and it independently re-derives the ACMG call from evidence using a 4-node LangGraph pipeline, then flags exactly where the two calls diverge. Every criterion that fires is backed by a specific evidence sentence. No evidence, no flag -- enforced at the Pydantic model level, not by convention.

**Tech:** LangGraph, FastMCP (Model Context Protocol), Pydantic v2, Ollama / Anthropic / OpenAI / Gemini, uv, ruff, mypy
```bash
git clone https://github.com/ankurgenomics/Reviewer2
cd Reviewer2 && uv sync
uv run reviewer2 demo   # 3 live cases, no API key needed with Ollama
```

- 21 tests passing, 86% action-band concordance vs expert-panel ClinVar classifications
- Pydantic v2 validators enforce at the model level: no criterion can fire without grounding evidence
- MCP server ready: any LLM agent that speaks Model Context Protocol can call it as a tool

---

### 🧫 [sentinel-amr](https://github.com/ankurgenomics/sentinel-amr) — Explainable AMR Classifier
**New** | XGBoost · SHAP · LangGraph · Python

Explainable, agentic antimicrobial resistance classifier for bacterial pathogen surveillance. Predicts resistance, names the genes that drove the call via SHAP TreeExplainer, detects organisms outside the training distribution, and escalates uncertainty to a human — with a full audit trail at every step.

**Tech:** XGBoost, SHAP TreeExplainer, LangGraph StateGraph, alignment-free k-NN novelty detection, BV-BRC / CARD / VFDB
```bash
git clone https://github.com/ankurgenomics/sentinel-amr
cd sentinel-amr && ./run.sh   # train + explain + novelty + demo, fully offline
make demo-novel               # shows the novel-organism escalation path
```

- ROC-AUC 0.894 on a group-aware holdout — related isolates never leak across the split
- Top drivers independently rediscovered: CTX-M-15, acrAB efflux pump, DNA topoisomerase IV
- Novel-organism gate explicitly blocks the automated call when the sample has no database match

---

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

- Validation MCC peaked at epoch 1–2 then declined, so a low learning rate and validation-based selection matter more than longer training
- 🤗 Model card: [ankur0050/nucleotide-transformer-v2-50m-genomicbenchmarks-ft](https://huggingface.co/ankur0050/nucleotide-transformer-v2-50m-genomicbenchmarks-ft)

---

### 🐝 [adaptive-research-swarm](https://github.com/ankurgenomics/adaptive-research-swarm) — Non-Linear Multi-Agent System
**New** | LangGraph · FastAPI · Docker

A supervisor-orchestrated system that plans its own agent roster at runtime instead of following a fixed pipeline. Three real graph cycles: a critic sends rejected work back to the exact agent for rework, a second cycle lets the critic decide the roster itself is missing a specialist and triggers a re-plan, and a human-rejection cycle routes free-text feedback through an LLM decision on how to respond. A code-enforced iteration/tool-call budget means a stuck run returns a typed `partial` result instead of looping forever.

**Tech:** LangGraph, FastAPI, Pydantic v2, multi-provider LLM fallback, Tavily/Exa, Langfuse, Docker
```bash
git clone https://github.com/ankurgenomics/adaptive-research-swarm
cd adaptive-research-swarm && cp .env.example .env && docker compose up --build
```

- 100% completeness (24/24 expected facts), 16.7% hallucination rate — Anthropic-judged, reproducible
- Same engine ships two presets (competitive intelligence, lead qualification) — proof it generalizes

---

### 🛡️ [enterprise-doc-intelligence](https://github.com/ankurgenomics/enterprise-doc-intelligence) — Guarded RAG with Injection Defense
**New** | FastAPI · Chroma · RAGAS

RAG for regulated documents (contracts, SOPs, financial reports): hybrid retrieval (BM25 + Chroma vector search, reciprocal rank fusion, cross-encoder reranking), span-grounded citations, and a groundedness guardrail that refuses to answer unsupported claims. Ships a live, reproducible prompt-injection defense test.

**Tech:** FastAPI, Pydantic v2, rank_bm25 + Chroma, sentence-transformers, RAGAS, Docker
```bash
git clone https://github.com/ankurgenomics/enterprise-doc-intelligence
cd enterprise-doc-intelligence && python scripts/generate_sample_docs.py && uvicorn app.main:app --reload
```

- RAGAS: 0.981 faithfulness, 1.000 context precision/recall
- `python -m adversarial.run_injection_test` — hidden and visible injection payloads both neutralized before indexing

---

### 🔐 [FedClinic](https://github.com/ankurgenomics/fedclinic) — Federated Clinical Analysis
**Daytona HackSprint Bronze** | FedSGD · Nosana GPU · MCP

Federated learning across real Daytona sandboxes so patient data never leaves institutional boundaries. Ran a real gradient-inversion attack on a Nosana RTX 3090, reconstructed a real patient's record, then fixed it with differential privacy and measured the cost. Validated on 123 real MIMIC-IV hospital admissions. Exposes an MCP server for direct agent tool-calling.

**Tech:** Python, FedSGD, PyTorch, Daytona, Nosana GPU, MCP

- Attack residual: 9.4e-5 (succeeds) → 2.69 (fails) after the DP fix; model loss cost only 0.505 → 0.510

---

### 🧪 [lab-agent](https://github.com/ankurgenomics/lab-agent) — Multi-Instrument Lab Orchestration
**Open source** | LLM function calling · LIMS · Ollama

Natural-language orchestration of microscope, liquid-handler, and flow-cytometer workflows, with a safety validator blocking invalid tool calls before any hardware call fires. Async job tracking, LIMS writing per-well results to SQLite, closed-loop planning across 3 LLM backends (Ollama, Anthropic, Groq). Tested on real HeLa cell images (Broad Institute BBBC020).

**Tech:** Python, LLM function calling, Ollama/Anthropic APIs, SQLite/SQLAlchemy, Micro-Manager, Opentrons API

---

### 🧬 [genome-arch](https://github.com/ankurgenomics/genome-arch) — From-Scratch Variant-Effect Architecture
**Open source** | PyTorch · Benchmarked vs. 7 baselines

Multi-scale block-convolution + dynamic sparse-attention + reverse-complement-equivariance architecture for cross-species non-coding variant prediction. Benchmarked with leakage-free, multi-seed evaluation against Enformer, Borzoi, DeepSEA, Sei, SpliceAI, BPNet, and ChromBPNet.

**Tech:** PyTorch, Hugging Face Transformers, GitHub Actions CI/CD

---

### 🔬 [protein-ft](https://github.com/ankurgenomics/protein-ft) — ESM2 Fine-Tuning vs. Frozen Baseline
**Open source** | PyTorch · FLIP benchmark

Full-parameter ESM2 fine-tuning measured directly against a frozen-embedding linear probe on protein fitness-landscape prediction (FLIP GB1) — quantifying when full fine-tuning is worth its cost. Tests verify the frozen-probe mode produces exactly zero gradient into the backbone.

**Tech:** PyTorch, Hugging Face Transformers, FLIP benchmark, GitHub Actions CI/CD

---

### ☁️ Autonomous Genomic Pipelines
**Production cloud infrastructure** | AWS · Nextflow · Step Functions

Self-optimizing WGS/RNA-seq workflows on AWS with adaptive resource allocation and automated QC gating. Processed 10,000+ samples with minimal human intervention.

**Impact:**
- 40% ↓ compute costs
- 50% ↓ storage footprint
- 1 PB genomic data managed

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

## 🏆 Hackathons, Talks & Recognition

**3rd Place** · Global AI Construct Multi-Agent AI Challenge · Microsoft / OGP / HTX · 2026
Architected a multi-agent system natively on Azure AI Foundry in a 3-hour build among ~100 engineers.

**Bronze** · Daytona HackSprint · SGInnovate · 2026
Solo entry. Built FedClinic, adversarially stress-tested with a real gradient-inversion attack and hardened with differential privacy.

**Winner** · Illumina Internal AI Hackathon · 2026
Built GWASplain, an AI-enabled interpretation tool for population genomics data.

**Invited Speaker** · Lorong AI Healthcare x AI Forum · Ministry of Digital Development and Information, Singapore · Aug 2026
Presented on clinical AI adoption, auditability, and evidence-based decision-making to VCs, researchers, and government stakeholders.

**Stage Speaker** · AWS ASEAN Summit · 2023
Invited talk to enterprise and government technology leaders across Southeast Asia, representing Mirxes.

---

## 📚 Publications & Research

**Newsletter** · "Slightly Intelligent" · LinkedIn · ongoing
750+ subscribers, 10,000+ weekly views, 16 issues on agentic AI, evaluation methodology, and foundation-model critique.
[Read on LinkedIn](https://www.linkedin.com/newsletters/slightly-intelligent-7460276303405985792)

**PhD Thesis** · NTU Singapore · 2021
[Age-dependent transcriptional and epigenetic alterations in mouse hepatocytes](https://doi.org/10.32657/10356/155390)

**Technical Writeup** · Open Source
[Why agentic AI for genomics? Designing reasoning-traceable variant interpretation](https://github.com/ankurgenomics/agentic-genomics/blob/main/docs/why-agentic.md)

**Open-source ML** · 2026
[genome-ft: full fine-tuning of Nucleotide Transformer v2 (50M) on GenomicBenchmarks](https://github.com/ankurgenomics/genome-ft) — leakage-free, multi-seed evaluation; [model card on Hugging Face](https://huggingface.co/ankur0050/nucleotide-transformer-v2-50m-genomicbenchmarks-ft)

**Technical Blog** · Amazon Web Services · 2025
[Using serverless for cross-organizations information exchange in genomic analysis](https://builder.aws.com/content/2yRrRdqamrcHxXj2oF1nJgtXoTU/using-serverless-for-cross-organizations-information-exchange-in-genomic-analysis)

**Blog Post** · May 2026
[When an AI Agent Boards a Cruise Ship: Hantavirus, LangGraph, and the Future of Outbreak Triage](https://ankurgenomics.github.io/2026/05/09/hantavirus-cruise-ship-agentic-ai.html)

**Conference Poster** · Cell Symposia, Chicago · 2019
Significance of hepatocyte polyploidization in liver physiology and pathology

**Peer-Reviewed** · Frontiers in Microbiology · 2018
[Antiproliferative and antioxidative bioactive compounds in marine-derived endophytic fungus](https://www.frontiersin.org/journals/microbiology)

---

## 🎯 Open to Relevant Opportunities

I am open to relevant roles globally — across industry, research, and startups — where agentic AI, ML, or computational biology intersects with real-world impact.

If you are working on something ambitious at the intersection of AI and science, I'd love to hear from you.

**Based in Singapore (PR)** — open to remote, hybrid, or relocation anywhere in the world.

---

## 📫 Let's Connect

- 📧 **Email:** [ankurs103@gmail.com](mailto:ankurs103@gmail.com)
- 💼 **LinkedIn:** [linkedin.com/in/ankurit](https://www.linkedin.com/in/ankurit/)
- 🌐 **Portfolio:** [ankur-portfolio-v2-sandy.vercel.app](https://ankur-portfolio-v2-sandy.vercel.app/)
- 📄 **Resume:** [Download CV (PDF)](https://ankur-portfolio-v2-sandy.vercel.app/Ankur_Sharma_Resume_2026.pdf)

---

<div align="center">

### 🔬 Building the future of AI-powered science, one traceable agent at a time.

![Profile Views](https://komarev.com/ghpvc/?username=ankurgenomics&color=00FFC6&style=flat-square)

</div>
