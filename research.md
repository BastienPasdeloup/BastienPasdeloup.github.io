---
layout: default
title: Research
---

<div class="page-header">
  <h1>Research</h1>
  <p class="subtitle">Publications, projects, and supervisions</p>
</div>

## Research Overview

My research focuses on modern AI technologies, from fundamental model development to healthcare applications. I identify major AI trends and adapt them for domains underserved by major industry players, particularly in health.

<div class="highlight-box">
  <p>🎯 <strong>Current focus:</strong> Developing a <em>flexible multimodal foundation model for healthcare</em>, capable of integrating diverse medical data (imaging, time series, clinical notes, genomics) while handling missing modalities.</p>
</div>

## Publications

<div class="card" style="margin: 1.5rem 0; padding: 0; overflow: hidden;">
  <iframe 
    src="https://scholar.google.com/citations?user=dKOgoG4AAAAJ&hl=en" 
    style="width: 100%; height: 500px; border: none;"
    title="Google Scholar Profile">
  </iframe>
</div>

<p style="text-align: center;">
  <a href="https://scholar.google.com/citations?user=dKOgoG4AAAAJ" target="_blank" class="publication-link" style="display: inline-flex;">
    <i class="fas fa-external-link-alt"></i> Open in Google Scholar
  </a>
</p>

## Research Themes

### 🌱 Few-Shot Learning & Diversity (ANR JCJC ENDIVE)

I lead the ANR JCJC project **ENDIVE** (2024-2028, ~294k€) exploring how **diversity** can improve learning with limited data:

- **Data axis**: Quantifying dataset similarity, optimal sample selection, identifying relevant data portions
- **Embedding axis**: Selecting informative representations, multi-context embeddings, model ensemble selection

Using **Determinantal Point Processes (DPPs)** to enable diversity-aware sampling with mathematical guarantees.

<div class="publication-links">
  <a href="https://anr.fr/Projet-ANR-23-CE23-0030" class="publication-link" target="_blank">
    <i class="fas fa-external-link-alt"></i> ANR Project Page
  </a>
</div>

### 🧠 Foundation Models

**REVE: A Foundation Model for EEG** (NeurIPS 2025)
- Largest EEG corpus to date: **60,000+ hours**, **25,000+ subjects**, **92 datasets**
- State-of-the-art on **10 tasks** with minimal or no adaptation
- Challenges the need for task-specific models in BCI

<div class="publication-links">
  <a href="https://github.com/brain-bzh/REVE" class="publication-link" target="_blank">
    <i class="fab fa-github"></i> Code
  </a>
</div>

**Large Language Models**
- Diffusion-based LLMs for faster generation and parallel demasking
- Diversity integration during response generation
- 3 ongoing PhD projects on LLM architectures and reasoning

### 🏥 AI for Healthcare

Collaborations with medical specialists on real clinical problems:

**Cardiology** (CHU Brest, CHU Paris)
- TAVI pacemaker implantation prediction using multimodal imaging [J5]
- Intensive care unit risk scoring with ML [J10]
- Coronary syndrome analysis via AI-assisted vascular segmentation [J8]
- CTEPH early prediction from blood flow data [J9]

**Neurology** (CHU Brest, Horizon Europe STRATIFY)
- 30-day mortality prediction after stroke [T2]
- Stroke recurrence risk prediction
- Long-term resilience diagnosis

**Oncology** (EPFL/CHUV)
- Optimal transport distances for patient similarity based on lymphocyte distribution in tumors [C12]
- Precision medicine approaches

### 📊 Graph Signal Processing

My PhD work extended signal processing to irregular domains modeled by graphs:
- **Graph inference** from diffused signals [J1]
- **Uncertainty principle** on graphs [B1]
- **Translation operators** for Graph CNNs [C4, C7]
- Applications to **fMRI** and **EEG** data [C8, C18, C19]

## Funded Projects (PI/co-PI)

| Project | Funding | Period | Amount |
|---------|---------|--------|--------|
| **ENDIVE** — Encouraging Diversity in Few-Shot Learning | ANR JCJC | 2024-2028 | ~294k€ |
| **Sony Research Partnership** | Private | 2022-2026 | ~240k€ |
| **Autonomous Pack** — AI for Logistics | ADEME | 2023-2026 | ~260k€ |
| **ASTRID** — AI for Heterogeneous Component Fusion | ANR | 2022-2023 | ~142k€ |
| **Few-Shot Learning for BCI** | Région Bretagne + ANR | 2021-2024 | ~106k€ |
| **Futur & Ruptures** — Few-Shot Labeling | Fondation Mines-Télécom | 2021-2024 | ~108k€ |

## Supervisions

### PhD Students

| Student | Topic | Period | Status |
|---------|-------|--------|--------|
| Maryam Karimi-Mamaghan | Hybridizing Metaheuristics with ML | 2019-2022 | ✅ Defended |
| Fred Michael Gonsalves | ML for Cruise Ship Energy Efficiency | 2020-2023 | ✅ Defended |
| Yassir Bendou | Few-Shot Image Classification | 2021-2024 | ✅ Defended |
| Yassine El Ouahidi | Deep Learning for BCI | 2022-2025 | ✅ Defended |
| Dubon Rodrigue | AI for District Heating Networks | 2022-2025 | ✅ Defended |
| Jonathan Lys | LLMs & Diversity | 2024-2027 | 🔄 Ongoing |
| Joshua Chaz Rivera | Diffusion-Based LLMs | 2025-2028 | 🔄 Ongoing |
| Nolan Sisouphanthong | Diffusion Models for Language | 2025-2028 | 🆕 Starting |

### Medical Doctorates (MD)

| Student | Topic | Status |
|---------|-------|--------|
| Victor Quéré | Stroke Mortality Prediction | ✅ 2021 |
| Amine El Ouahidi | TAVI Pacemaker Prediction | ✅ 2023 |
| Yahia Bellouche | Cardiology & CTEPH | 🔄 2026 |

### Post-Docs & Research Engineers

- **4 Post-Docs** supervised (2020-2027)
- **2 Research Engineers** (2021-2025)
- **23+ Interns** (Master & Bachelor level)

## Open Source

All publication code is available on GitHub:

<div class="card-grid">
  <div class="card">
    <h3><i class="fab fa-github"></i> REVE</h3>
    <p>Foundation model for EEG (NeurIPS 2025)</p>
    <a href="https://github.com/brain-bzh/REVE">View Repository →</a>
  </div>
  
  <div class="card">
    <h3><i class="fab fa-github"></i> EASY</h3>
    <p>State-of-the-art Few-Shot Classification</p>
    <a href="https://github.com/ybendou/easy">View Repository →</a>
  </div>
  
  <div class="card">
    <h3><i class="fab fa-github"></i> Graph Translations</h3>
    <p>Translation operators on graphs</p>
    <a href="https://github.com/BastienPasdeloup/graph_translations">View Repository →</a>
  </div>
</div>

## Academic Service

**Reviewing**: IEEE TSP, IEEE SPL, IEEE TSIPN, Elsevier Signal Processing, EURASIP, GRETSI, ACM Sigmetrics, Oxford Bioinformatics, ANR JCJC committee

**Event Organization**: GSP Workshop (2018), GdR ISIS Day (2019), Foundation Day (2024), Few-Shot Learning Workshop (2024)

**Invited Talks**: EPFL, ENS Lyon, CRIStAL, GIPSA-Lab, Inria, Université de Nantes
