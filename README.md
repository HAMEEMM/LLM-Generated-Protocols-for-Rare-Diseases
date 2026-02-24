# Evaluating LLMs for Clinical Trial Protocol Generation in Rare Diseases

**Author:** Dr. Hameem Mahdi
**Published:** February 2026
**Paper:** `Evaluating_LLMs_for_Clinical_Trial_Protocol_Generation_in_Rare_Diseases_Mahdi_2026.pdf`

---

## Overview

This repository contains the complete research pipeline for evaluating Large Language Models (LLMs) in generating clinical trial protocols for rare diseases. Using **Mistral 7B** (open-source, 7B parameters), the study generates and systematically assesses 15 protocols across 5 rare diseases using a 4-dimensional quality framework.

**Core finding:** LLMs achieve 4.73/5.0 medical accuracy and 3.81/5.0 overall quality, establishing them as viable drafting assistants for rare disease research while identifying structural gaps requiring targeted improvement.

---

## Research Question

> Can Large Language Models generate high-quality, expert-ready clinical trial protocols for rare diseases using structured prompt engineering?

---

## Diseases Studied

| Disease | Prevalence | System |
|---|---|---|
| Fabry Disease | 1 in 40,000–117,000 | Cardiovascular / Neurological |
| Dravet Syndrome | 1 in 20,000–40,000 | Neurological |
| Autoimmune Encephalitis | 1 in 1,000,000 | Immune / Neurological |
| Pediatric DIPG | ~100–150 new cases/year (US) | Oncological |
| Autism with Microbiome Dysbiosis | 1 in 36–38 children | Gut-Brain Axis |

---

## Repository Structure

```
LLM-Generated Protocols for Rare Diseases/
│
├── Phase 1 - Literature Review/
│   └── 1.pdf – 5.pdf                         # Background literature
│
├── Phase 2 - LLM & Prompt Engineering/
│   ├── PHASE_2_LLM_BASED_PROTOCOL_GENERATION.ipynb
│   └── Results/
│       └── rare_disease_protocols.csv         # 15 generated protocols
│
├── Phase 3 - Protocol Generation/
│   ├── PHASE_3_PROTOCOL_GENERATION_&_QUALITY_ASSESSMENT.ipynb
│   ├── Quality Assessment/
│   │   └── protocol_quality_assessment.csv    # 4-dimensional scores
│   ├── Reports/
│   │   ├── Phase3_Quality_Assessment_Report_20260221.md
│   │   └── Phase3_Quality_Assessment_Report_20260221.html
│   ├── Deliverables/
│   │   ├── Phase3_Completion_Certificate.md
│   │   ├── Phase3_Final_Deliverables_Summary.md
│   │   └── phase3_issue_log.md
│   └── Final_Protocols/
│       └── phase3_final_protocols.csv         # Quality-assessed final protocols
│
├── Phase 4 - Real-World Benchmark/
│   ├── PHASE_4_BENCHMARK_ANALYSIS.ipynb
│   └── Results/
│       ├── benchmark_results.csv              # Protocol-level metrics
│       ├── section_analysis.csv               # 16-section performance
│       ├── disease_performance.csv            # Per-disease aggregates
│       └── protocol_section_matrix.csv        # 15×16 binary presence matrix
│
├── Phase 5 - Comparative Analysis/
│   ├── PHASE_5_COMPREHENSIVE_BENCHMARK_ANALYSIS.ipynb
│   ├── Figures/
│   │   ├── comparative_analysis_diseases.png
│   │   └── section_level_analysis.png
│   └── Reports/
│       ├── PHASE_5_COMPARATIVE_ANALYSIS_REPORT.txt
│       └── phase5_summary_metrics.csv
│
├── Evaluating_LLMs_for_Clinical_Trial_Protocol_Generation_in_Rare_Diseases_Mahdi_2026.pdf
├── Evaluating_LLMs_for_Clinical_Trial_Protocol_Generation_in_Rare_Diseases_Mahdi_2026.docx
└── README.md
```

---

## Methodology

### Model
- **Mistral 7B** — open-source, reproducible, no external API dependency
- **Hardware:** Google Colab Pro + NVIDIA RTX PRO 6000 GPU

### Protocol Generation (Phase 2)
Each of 5 diseases received 3 protocol variants using a structured prompt template enforcing 8 mandatory sections:

1. Disease Understanding
2. Research Endpoints
3. Study Design
4. Sample Size & Population
5. Adaptive Design & Modern Methods
6. Cross-System Biomarker Integration
7. Safety Monitoring
8. Quality & Feasibility

**Output:** 15 protocols — 20,626 total words — avg. 1,375 words/protocol — avg. 34.7 sec/protocol

### Quality Assessment Framework (Phase 3)
Protocols scored on a 4-dimension 0–5.0 scale:

| Dimension | Criteria |
|---|---|
| Medical Accuracy | No hallucinated drugs/biomarkers; realistic treatments |
| Structural Completeness | Presence of 16 formal protocol sections |
| Biomarker Integration | Cross-system biomarker justification quality |
| Consistency & Professionalism | Formatting, tone, internal coherence |

### Benchmarking & Comparative Analysis (Phases 4–5)
- Section-level presence/quality matrix (15 protocols × 16 sections)
- Disease-level aggregation with standard deviations
- Statistical tests: Kruskal-Wallis (disease comparison), Mann-Whitney U (organ system comparison)

---

## Key Results

### Quality Scores

| Dimension | Score | Rating |
|---|---|---|
| Medical Accuracy | 4.73 / 5.0 | Excellent |
| Biomarker Integration | 4.47 / 5.0 | Good |
| Consistency & Professionalism | 5.00 / 5.0 | Perfect |
| Structural Completeness | 1.13 / 5.0 | Weak |
| **Overall** | **3.81 / 5.0** | |

### Benchmark Metrics

| Metric | Value |
|---|---|
| Overall Completeness | 71.7% |
| Overall Quality | 87.8% |
| Average Sections Present | 13 / 16 |
| Expert Review Readiness | 100% (15/15) |
| Critical Issues | 0 |

### Statistical Findings
- **Kruskal-Wallis (disease comparison):** p = 0.2311 — no significant difference between diseases
- **Mann-Whitney U (organ systems):** p = 0.1876 — no organ system bias

### Section-Level Gaps (Critical — < 50% Presence)

| Missing Section | Presence Rate |
|---|---|
| Title & Abstract | 0% |
| Statistical Analysis Plan | 0% |
| References / Citations | 0% |
| Data Management & Quality Control | 27% |

---

## How to Run

### Prerequisites
- Python 3.9+
- Jupyter Notebook / Google Colab
- GPU recommended (NVIDIA CUDA-compatible)

```bash
pip install transformers torch pandas numpy scipy matplotlib seaborn
```

### Execution Order

```
Phase 2  →  Phase 3  →  Phase 4  →  Phase 5
```

1. **Phase 2** — `PHASE_2_LLM_BASED_PROTOCOL_GENERATION.ipynb`
   Generates 15 protocols → outputs `rare_disease_protocols.csv`

2. **Phase 3** — `PHASE_3_PROTOCOL_GENERATION_&_QUALITY_ASSESSMENT.ipynb`
   Scores all protocols → outputs quality CSVs and reports

3. **Phase 4** — `PHASE_4_BENCHMARK_ANALYSIS.ipynb`
   Computes benchmark metrics → outputs section/disease/protocol matrices

4. **Phase 5** — `PHASE_5_COMPREHENSIVE_BENCHMARK_ANALYSIS.ipynb`
   Runs statistical analysis and generates figures → outputs comparative reports

---

## Strengths and Limitations

### Strengths
- High medical accuracy with no hallucinated drug/biomarker references
- Consistent structural output from structured prompt engineering
- Rapid generation scale (under 35 seconds per protocol)
- Generalizes uniformly across 5 diseases and organ systems

### Limitations
- Missing 3 critical formal sections by default (Title/Abstract, Statistical Analysis Plan, References)
- No self-correction or critical appraisal capability
- Requires targeted prompt engineering for full formal compliance
- Human expert oversight necessary before clinical use

---

## Citation

```bibtex
@article{mahdi2026llm,
  title   = {Evaluating Large Language Models for Clinical Trial Protocol Generation
             in Rare Diseases: A Multi-Dimensional Quality Assessment},
  author  = {Mahdi, Hameem},
  year    = {2026},
  month   = {February}
}
```
