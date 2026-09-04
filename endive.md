---
layout: default
title: ENDIVE
description: ENDIVE — ENcouraging DIVErsity in Few-Shot Learning. An ANR JCJC project (2024-2028) led by Bastien Pasdeloup at IMT Atlantique, exploring what diversity of data and of representations can bring to modern AI.
permalink: /endive/
---

<div class="page-header">
  <h1>ENDIVE</h1>
  <p class="subtitle"><strong>EN</strong>couraging <strong>DIVE</strong>rsity in Few-Shot Learning</p>
</div>

<div class="project-hero">
  <div class="project-hero-header">
    <div class="project-hero-mark"><img src="{{ '/assets/img/endive/endive.svg' | relative_url }}" alt="A Belgian endive"></div>
    <div class="project-hero-title">
      <h3>ANR JCJC — ANR-24-CE23-7365</h3>
      <p class="project-hero-tagline">What can diversity bring to artificial intelligence?</p>
    </div>
  </div>

  <div class="project-facts">
    <div class="project-fact">
      <span class="fact-label">Period</span>
      <span class="fact-value">2024 — 2028</span>
      <span class="fact-note">48 months, ongoing</span>
    </div>
    <div class="project-fact">
      <span class="fact-label">Role</span>
      <span class="fact-value">Principal Investigator</span>
      <span class="fact-note">Scientific coordinator</span>
    </div>
    <div class="project-fact">
      <span class="fact-label">Funding</span>
      <span class="fact-value">≈ 294 k€</span>
      <span class="fact-note">ANR &mdash; "JCJC" grant</span>
    </div>
    <div class="project-fact">
      <span class="fact-label">Host</span>
      <span class="fact-value">IMT Atlantique</span>
      <span class="fact-note">Lab-STICC, BRAIN team</span>
    </div>
  </div>

  <div class="project-hero-footer">
    <div class="project-links">
      <a href="https://bastienpasdeloup.github.io/r/?eaf" target="_blank" class="project-btn primary"><i class="fas fa-external-link-alt"></i> ANR project page</a>
      <a href="{{ '/hdr/files/pasdeloup_endive.pdf' | relative_url }}" target="_blank" class="project-btn"><i class="fas fa-file-pdf"></i> Project description</a>
      <a href="{{ '/hdr/files/pasdeloup_2024_endive_slides.pdf' | relative_url }}" target="_blank" class="project-btn"><i class="fas fa-display"></i> Kick-off (2024)</a>
    </div>
  </div>
</div>

## In a Nutshell

Modern AI is trained on massive amounts of data, and scaling laws tell us that more data generally means better models. But *more* is not the only axis that matters: what a new example adds depends on how different it is from the ones already seen. ENDIVE takes that observation seriously and asks a simple question — **when the budget is on the number of examples rather than on the amount of compute, how much can be gained by choosing examples, features, or models that are diverse rather than merely individually good?**

The technical entry point of the project is *random sampling procedures with diversity-encouraging properties*, and in particular **Determinantal Point Processes** (DPPs). A DPP accounts both for the relevance of the points it samples and for their similarity, which yields a diverse form of importance sampling: it covers the underlying distribution better, and estimates its statistics with lower variance than independent uniform sampling.

<div class="highlight-box">
  <p><strong>A note on scope.</strong> ENDIVE was written for <em>few-shot learning</em>, at a time when learning from a handful of labeled examples was a research field of its own. Three years later, few-shot learning has largely become one regime of <em>foundation model adaptation</em>. This does not change the objectives of the project, but it did lead me to reorient it, giving considerably more space to large language models — and especially to discrete diffusion ones — still under the prism of diversity.</p>
</div>

## Why Diversity? A Picture

The figure below contrasts a DPP draw with a uniform draw of the same size, on the same point cloud. Ten points (colored) are sampled among five hundred (gray); the diamonds mark the mean of the sampled points against the mean of the full cloud.

<div class="figure-block">
  <div class="figure-grid">
    <div class="figure-panel">
      <img src="{{ '/assets/img/endive/dpp_sampling.png' | relative_url }}" alt="Ten points sampled with a determinantal point process among five hundred">
      <p class="panel-caption"><strong>DPP sampling.</strong> The ten sampled points repel one another and spread over the support of the cloud.</p>
    </div>
    <div class="figure-panel">
      <img src="{{ '/assets/img/endive/uniform_sampling.png' | relative_url }}" alt="Ten points sampled uniformly among five hundred">
      <p class="panel-caption"><strong>Uniform i.i.d. sampling.</strong> Nothing prevents the ten points from clustering in the dense region.</p>
    </div>
    <div class="figure-panel">
      <img src="{{ '/assets/img/endive/dpp_interpoint.png' | relative_url }}" alt="Distribution of the average inter-point distance for both sampling procedures">
      <p class="panel-caption"><strong>Diversity.</strong> Average inter-point distance over 9,000 draws: the DPP distribution sits clearly to the right.</p>
    </div>
    <div class="figure-panel">
      <img src="{{ '/assets/img/endive/dpp_mean.png' | relative_url }}" alt="Distribution of the distance between the mean of the sampled points and the mean of the cloud">
      <p class="panel-caption"><strong>Estimation.</strong> Distance between the sample mean and the true mean: the DPP estimator concentrates better.</p>
    </div>
  </div>
  <p class="figure-caption">A Gaussian kernel makes similarity a decreasing function of the Euclidean distance; in a real application, that kernel is where the desired notion of diversity is encoded. Figures taken from the <a href="{{ '/hdr/files/pasdeloup_endive.pdf' | relative_url }}" target="_blank">project description</a>.</p>
</div>

## Research Axes

The revised project explores the benefits of diversity along two complementary axes.

<div class="card-grid">
  <div class="course-card">
    <h3><i class="fas fa-database"></i> Diversity in the Data</h3>
    <div class="course-info">Curation &amp; data efficiency</div>
    <p>Selecting training examples on individual quality or importance alone produces highly redundant subsets. Combining quality with diversity is known to let carefully curated subsets match — or beat — much larger ones.</p>
    <ul>
      <li>How can diversity-aware curation make the training of <strong>diffusion LLMs</strong> more data-efficient? A criterion designed for next-token prediction scores an example by what it teaches about the continuation of a prefix, whereas masked denoising supervises every position at once, across corruption levels: what makes an example informative is not the same quantity.</li>
      <li>How does data diversity <strong>shape the behavior</strong> of these models — their decoding trajectories, and the internal mechanisms they give rise to?</li>
    </ul>
  </div>

  <div class="course-card">
    <h3><i class="fas fa-diagram-project"></i> Diversity in the Representations</h3>
    <div class="course-info">Features, contexts &amp; models</div>
    <p>Foundation models encode a great variety of concepts, many of them irrelevant to any particular downstream task. Diversity offers a criterion for deciding what to keep, what to ask, and whom to ask.</p>
    <ul>
      <li>Which <strong>features</strong> are relevant? Highly correlated features add little; diverse task-relevant ones may cover the information the model holds far more compactly.</li>
      <li>How can diversity of <strong>context</strong> be exploited? Prompting and retrieval produce several representations of the same input — complementary interpretations rather than one optimal context.</li>
      <li>Can diversity guide the <strong>selection and combination</strong> of foundation models, identifying complementary ones rather than the individually strongest?</li>
    </ul>
  </div>
</div>

Mechanistic interpretability has become the natural tool for the second axis: sparse autoencoders decompose representations into features whose overlap across models trained on different data diets is, in itself, a measurable notion of diversity.

## Publications

Each card names what the paper does and, more to the point, where it meets the project — as a direct contribution, or as an input to one of the two axes above.

<div class="card-grid pub-grid">
  <div class="course-card">
    <h3><a href="https://arxiv.org/abs/2603.19146" target="_blank">D5P4</a></h3>
    <div class="course-info">NeurIPS 2026 &bull; Under review</div>
    <p class="pub-fulltitle">Partition Determinantal Point Process for Diversity in Parallel Discrete Diffusion Decoding</p>
    <p class="pub-people">Lys, Gripon, Marmoret, Mauch, Cardinaux, Boukli-Hacene, <strong>Pasdeloup</strong></p>
    <p class="pub-does">Generalizes beam search to discrete diffusion models by choosing each step's candidate set with a partitioned DPP.</p>
    <div class="pub-connection">
      <span class="pub-connection-label"><i class="fas fa-star"></i> Core contribution</span>
      <p>ENDIVE's central bet, tested end to end: that a set chosen for relevance <em>and</em> mutual dissimilarity beats one chosen for individual quality. The k-DPP the proposal reserved for picking training examples here picks candidate sequences instead, and the partition constraint is what stops the diversity from collapsing. It also leaves the project a working diversity kernel built from a model's own hidden states — the object the representation axis needs.</p>
    </div>
    <div class="pub-links">
      <a href="https://arxiv.org/abs/2603.19146" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
    </div>
  </div>

  <div class="course-card">
    <h3><a href="https://proceedings.neurips.cc/paper_files/paper/2025/hash/20a917f77773ac0fa8bea2bdd6606b66-Abstract-Conference.html" target="_blank">REVE</a></h3>
    <div class="course-info">NeurIPS 2025</div>
    <p class="pub-fulltitle">A Foundation Model for EEG — Adapting to Any Setup with Large-Scale Pretraining on 25,000 Subjects</p>
    <p class="pub-people">El Ouahidi, Lys, Thölke, Farrugia, <strong>Pasdeloup</strong>, Gripon, Jerbi, Lioi</p>
    <p class="pub-does">An EEG foundation model whose 4D positional encoding makes the electrode layout an input, pretrained on 92 datasets.</p>
    <div class="pub-connection">
      <span class="pub-connection-label"><i class="fas fa-database"></i> Data axis</span>
      <p>Where the project's reorientation became concrete. Few-shot learning, as the proposal framed it, has become adaptation of a pretrained representation — and REVE is where that shift happened in our own hands. It also handed the project a concrete curation problem: assembling 92 heterogeneous corpora forced choices about which recordings add information rather than merely hours, which is the quality-versus-diversity trade-off of the data axis, on a corpus we control end to end.</p>
    </div>
    <div class="pub-links">
      <a href="https://proceedings.neurips.cc/paper_files/paper/2025/hash/20a917f77773ac0fa8bea2bdd6606b66-Abstract-Conference.html" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Paper</a>
      <a href="https://brain-bzh.github.io/reve/" target="_blank" class="publication-link"><i class="fas fa-code"></i> Code</a>
      <a href="{{ '/hdr/files/elouahidi_2025_reve_poster.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-image"></i> Poster</a>
      <a href="https://recorder-v3.slideslive.com/?share=106682&amp;s=3ee3f699-040c-423f-9a66-6fb508ea544b" target="_blank" class="publication-link"><i class="fas fa-video"></i> Video</a>
    </div>
  </div>

  <div class="course-card">
    <h3><a href="https://arxiv.org/abs/2602.14759" target="_blank">Inner Loop Inference</a></h3>
    <div class="course-info">EUSIPCO 2026</div>
    <p class="pub-fulltitle">Unlocking Latent Capabilities of Pretrained Transformers Without Training</p>
    <p class="pub-people">Lys, Gripon, <strong>Pasdeloup</strong>, Marmoret, Mauch, Cardinaux, Boukli-Hacene</p>
    <p class="pub-does">Adds refinement steps to a frozen transformer by re-applying a range of its own blocks, kept on-manifold by a light regularization.</p>
    <div class="pub-connection">
      <span class="pub-connection-label"><i class="fas fa-diagram-project"></i> Representation axis</span>
      <p>A measurement of what depth alone can recover. The project asks whether a pretrained representation already holds what a task needs, and how to reach it without labels or retraining; the answer here is <em>a little, and not uniformly across models</em> — naive looping even hurts. That the fix is interpolating looped with non-looped states says the useful signal is a direction in representation space rather than a new computation, which is what a diversity criterion over features must be defined on.</p>
    </div>
    <div class="pub-links">
      <a href="https://arxiv.org/abs/2602.14759" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
      <a href="{{ '/hdr/files/lys_2026_inner_slides.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-display"></i> Slides</a>
    </div>
  </div>

  <div class="course-card">
    <h3><a href="https://arxiv.org/abs/2602.14760" target="_blank">The Causal Shift</a></h3>
    <div class="course-info">EUSIPCO 2026</div>
    <p class="pub-fulltitle">Residual Connections and the Causal Shift: Uncovering a Structural Misalignment in Transformers</p>
    <p class="pub-people">Lys, Gripon, <strong>Pasdeloup</strong>, Marmoret, Mauch, Cardinaux, Boukli-Hacene</p>
    <p class="pub-does">Locates the depth at which hidden states stop encoding the current token and start encoding the next, then attenuates the residual branch there.</p>
    <div class="pub-connection">
      <span class="pub-connection-label"><i class="fas fa-diagram-project"></i> Representation axis</span>
      <p>It gives the representation axis a coordinate it was missing. Asking which features are relevant presumes a place to read features from, and this shows there is no canonical one: the same hidden state decodes to the input early, to nothing interpretable mid-network, and to the prediction late. Any diversity criterion over features therefore has to declare its depth — and D5P4's kernel, reading diversity off hidden states, is exactly such a choice.</p>
    </div>
    <div class="pub-links">
      <a href="https://arxiv.org/abs/2602.14760" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
      <a href="{{ '/hdr/files/lys_2026_residual_poster.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-image"></i> Poster</a>
    </div>
  </div>
</div>

## Team &amp; Collaborations

The project is coordinated by **Bastien Pasdeloup** at IMT Atlantique (Lab-STICC, BRAIN team), with the support of **Vincent Gripon**, **Nicolas Farrugia** and **Alexandre Reiffers-Masson**. Expertise on determinantal point processes is brought by **Nicolas Tremblay** (Gipsa-lab, Grenoble) and **Rémi Bardenet** (CRIStAL, Lille).

ENDIVE allowed me to hire the following researchers:

<div class="card-grid">
  <div class="course-card">
    <h3>Jonathan Lys</h3>
    <div class="course-info">PhD student &bull; 2024 — 2027</div>
    <p>Diversity in few-shot learning, then discrete diffusion LLMs. Author of the three publications above on decoding diversity and on pretrained transformers.</p>
    <a href="https://scholar.google.com/citations?user=heUq7WEAAAAJ" target="_blank">Google Scholar &rarr;</a>
  </div>
  <div class="course-card">
    <h3>Post-doctoral researcher</h3>
    <div class="course-info">18 months &bull; from 2027</div>
    <p>To be recruited, primarily on mechanistic interpretability and the diversity of the features and mechanisms models acquire.</p>
    <a href="{{ '/contact' | relative_url }}">Contact me &rarr;</a>
  </div>
  <div class="course-card">
    <h3>Master 2 intern</h3>
    <div class="course-info">6 months</div>
    <p>To be recruited. Get in touch if diversity-aware curation or interpretability of diffusion LLMs sounds like your kind of problem.</p>
    <a href="{{ '/contact' | relative_url }}">Contact me &rarr;</a>
  </div>
</div>

<p style="text-align: center; margin-top: 2.5rem;">
  <a href="{{ '/research' | relative_url }}" class="back-link"><i class="fas fa-arrow-left"></i> Back to Research</a>
</p>
