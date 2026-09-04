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

<div class="pub-list">
  <article class="pub-card">
    <div class="pub-card-head">
      <span class="pub-venue">NeurIPS 2026</span>
      <span class="pub-status">Under review</span>
    </div>
    <h3 class="pub-card-title"><a href="https://arxiv.org/abs/2603.19146" target="_blank">D5P4: Partition Determinantal Point Process for Diversity in Parallel Discrete Diffusion Decoding</a></h3>
    <p class="pub-card-authors">Jonathan Lys, Vincent Gripon, Axel Marmoret, Lukas Mauch, Fabien Cardinaux, Ghouthi Boukli-Hacene, and <strong>Bastien Pasdeloup</strong></p>
    <p class="pub-card-summary">A decoding framework that generalizes beam search to discrete diffusion language models, which refine whole sequences in parallel instead of extending a prefix. Candidate selection at each diffusion step is cast as MAP inference over a <em>partitioned</em> DPP, whose kernel combines the quality signal carried by the logits with a diversity signal read from the model's own hidden states — so the procedure stays model-internal, with no external verifier. The partition constraint prevents hypotheses from collapsing onto the same trajectory, and the greedy solver's overhead is more than offset by a ~40% cut in peak memory.</p>
    <div class="pub-endive-note">
      <i class="fas fa-link"></i>
      <span>The most direct ENDIVE contribution to date: the project's DPP machinery becomes a decoding rule, and diversity is measured in the model's own representation space.</span>
    </div>
    <div class="pub-card-links">
      <a href="https://arxiv.org/abs/2603.19146" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
    </div>
  </article>

  <article class="pub-card">
    <div class="pub-card-head">
      <span class="pub-venue">NeurIPS 2025</span>
    </div>
    <h3 class="pub-card-title"><a href="https://proceedings.neurips.cc/paper_files/paper/2025/hash/20a917f77773ac0fa8bea2bdd6606b66-Abstract-Conference.html" target="_blank">REVE: A Foundation Model for EEG — Adapting to Any Setup with Large-Scale Pretraining on 25,000 Subjects</a></h3>
    <p class="pub-card-authors">Yassine El Ouahidi, Jonathan Lys, Philipp Thölke, Nicolas Farrugia, <strong>Bastien Pasdeloup</strong>, Vincent Gripon, Karim Jerbi, and Giulia Lioi</p>
    <p class="pub-card-summary">A foundation model built to absorb the heterogeneity of EEG recordings across electrode layouts, devices, protocols and subjects. A 4D positional encoding represents jointly the 3D location of each electrode and the temporal position of each signal patch, which makes the electrode layout part of the model's input rather than something recordings must be projected onto. Pretrained by masked autoencoding on 60,000+ hours from 92 datasets and ~25,000 subjects, it reaches state-of-the-art results on ten downstream tasks, including under linear probing.</p>
    <div class="pub-endive-note">
      <i class="fas fa-link"></i>
      <span>The concrete setting in which few-shot learning became foundation model adaptation, and the reason the project reoriented. Assembling 92 heterogeneous datasets also turned data curation into a research question of its own — feeding directly into the data-diversity axis.</span>
    </div>
    <div class="pub-card-links">
      <a href="https://proceedings.neurips.cc/paper_files/paper/2025/hash/20a917f77773ac0fa8bea2bdd6606b66-Abstract-Conference.html" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Paper</a>
      <a href="https://brain-bzh.github.io/reve/" target="_blank" class="publication-link"><i class="fas fa-code"></i> Code &amp; weights</a>
      <a href="{{ '/hdr/files/elouahidi_2025_reve_poster.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-image"></i> Poster</a>
      <a href="https://recorder-v3.slideslive.com/?share=106682&amp;s=3ee3f699-040c-423f-9a66-6fb508ea544b" target="_blank" class="publication-link"><i class="fas fa-video"></i> Video</a>
    </div>
  </article>

  <article class="pub-card">
    <div class="pub-card-head">
      <span class="pub-venue">EUSIPCO 2026</span>
    </div>
    <h3 class="pub-card-title"><a href="https://arxiv.org/abs/2602.14759" target="_blank">Inner Loop Inference for Pretrained Transformers: Unlocking Latent Capabilities Without Training</a></h3>
    <p class="pub-card-authors">Jonathan Lys, Vincent Gripon, <strong>Bastien Pasdeloup</strong>, Axel Marmoret, Lukas Mauch, Fabien Cardinaux, and Ghouthi Boukli-Hacene</p>
    <p class="pub-card-summary">A training-free way of spending extra computation at inference time in a frozen transformer, by re-applying a selected range of blocks to the propagated hidden state. Naive looping degrades accuracy — re-executing layers pushes activations off the manifold seen during standard inference — so the contribution is a lightweight regularization interpolating looped states with their non-looped counterparts. With the loop region chosen once, and consistently found at 40–60% of relative depth, the gains are modest but consistent on the Gemma-2 models; pre-norm Llama-3-8B responds more variably.</p>
    <div class="pub-endive-note">
      <i class="fas fa-link"></i>
      <span>Representation axis: it probes how much usable capability already sits latent in a frozen model's residual stream, and can be recovered without touching a single parameter.</span>
    </div>
    <div class="pub-card-links">
      <a href="https://arxiv.org/abs/2602.14759" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
      <a href="{{ '/hdr/files/lys_2026_inner_slides.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-display"></i> Slides</a>
    </div>
  </article>

  <article class="pub-card">
    <div class="pub-card-head">
      <span class="pub-venue">EUSIPCO 2026</span>
    </div>
    <h3 class="pub-card-title"><a href="https://arxiv.org/abs/2602.14760" target="_blank">Residual Connections and the Causal Shift: Uncovering a Structural Misalignment in Transformers</a></h3>
    <p class="pub-card-authors">Jonathan Lys, Vincent Gripon, <strong>Bastien Pasdeloup</strong>, Axel Marmoret, Lukas Mauch, Fabien Cardinaux, and Ghouthi Boukli-Hacene</p>
    <p class="pub-card-summary">A structural tension in autoregressive transformers: the hidden state at a position is initialized from the <em>current</em> token and carried along by the residual connections, while the supervision target is the <em>next</em> one. Decoding intermediate states through the tied embedding matrix reveals three regimes — early layers decoding to the input sequence, intermediate layers to nothing interpretable, late layers to the one-token-shifted sequence — with the transition deep in the network (around layer 17 of 26 for Gemma-2-2B). A learned gate attenuating the residual branch concentrates on the final layer and outperforms fixed single-layer cuts, which are themselves very sensitive to the chosen layer.</p>
    <div class="pub-endive-note">
      <i class="fas fa-link"></i>
      <span>Representation axis, from the interpretability side: before one can ask which features are worth keeping, one has to know <em>where</em> in the network a representation stops describing the input and starts describing the prediction.</span>
    </div>
    <div class="pub-card-links">
      <a href="https://arxiv.org/abs/2602.14760" target="_blank" class="publication-link"><i class="fas fa-file-lines"></i> Preprint</a>
      <a href="{{ '/hdr/files/lys_2026_residual_poster.pdf' | relative_url }}" target="_blank" class="publication-link"><i class="fas fa-image"></i> Poster</a>
    </div>
  </article>
</div>

## Team &amp; Collaborations

The project is coordinated by **Bastien Pasdeloup** at IMT Atlantique (Lab-STICC, BRAIN team), with the support of **Vincent Gripon**, **Nicolas Farrugia** and **Alexandre Reiffers-Masson**. Expertise on determinantal point processes is brought by **Nicolas Tremblay** (Gipsa-lab, Grenoble) and **Rémi Bardenet** (CRIStAL, Lille).

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
