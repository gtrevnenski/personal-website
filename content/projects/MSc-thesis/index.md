---
title: "Master's Thesis - Modality fusion in enzyme interaction prediction"
nav_label: "MSc Thesis"
date: 2024-12-12
draft: false
description: "Modality-fusion strategies for a transformer predicting enzyme-substrate interactions"
tags: ["Bioinformatics", "Deep Learning", "Modality Fusion"]
github: "https://github.com/gtrevnenski/MuMoTEn"
---

<style>
.thesis-section {
  margin: 2rem 0;
}

.thesis-objective {
  background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
  border-left: 4px solid #3b82f6;
  padding: 1.5rem;
  border-radius: 8px;
  margin-bottom: 2rem;
}

.thesis-objective-title {
  font-weight: 700;
  font-size: 1.1rem;
  color: #1e40af;
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.thesis-objective-title::before {
  content: "🎯";
  font-size: 1.3rem;
}

.thesis-objective-text {
  color: #1e3a8a;
  line-height: 1.7;
}

.thesis-subtitle {
  font-weight: 700;
  font-size: 1.1rem;
  color: #1f2937;
  margin-bottom: 1.25rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e5e7eb;
}

.thesis-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.thesis-list li {
  position: relative;
  padding-left: 2rem;
  margin-bottom: 1.25rem;
  line-height: 1.7;
  color: #374151;
}

.thesis-list li::before {
  content: "▸";
  position: absolute;
  left: 0.5rem;
  color: #3b82f6;
  font-weight: 700;
  font-size: 1.2rem;
}

.results-section {
  background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
  border-left: 4px solid #10b981;
  padding: 1.5rem;
  border-radius: 8px;
  margin-top: 2rem;
}

.results-title {
  font-weight: 700;
  font-size: 1.1rem;
  color: #065f46;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.results-title::before {
  content: "✅";
  font-size: 1.3rem;
}

.results-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.results-list li {
  position: relative;
  padding-left: 2rem;
  margin-bottom: 1rem;
  line-height: 1.7;
  color: #064e3b;
}

.results-list li::before {
  content: "✓";
  position: absolute;
  left: 0.5rem;
  color: #10b981;
  font-weight: 700;
  font-size: 1.3rem;
}

.thesis-gallery-section {
  display: flex;
  flex-direction: column;
  gap: 3.5rem;
  align-items: center;
}

.thesis-figure {
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  width: 100%;
}

.thesis-figure figcaption {
  color: #6b7280;
  font-size: 0.9rem;
  text-align: center;
}

.thesis-lightbox-trigger {
  cursor: pointer;
  display: block;
  width: 100%;
  text-decoration: none;
}

.thesis-lightbox-trigger img {
  width: 100%;
  display: block;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.12);
}

.thesis-arch-preview {
  width: min(100%, 600px);
}

.thesis-mcc-preview {
  width: min(100%, 600px);
}

.thesis-arch-thumb {
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.12);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.5rem;
  padding: 0.5rem;
  background: #f8fafc;
  border: 2px solid #cbd5e1;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.thesis-arch-thumb:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 28px rgba(0,0,0,0.15);
}

.thesis-arch-thumb img {
  width: 100%;
  border-radius: 8px;
}

.thesis-pdf-preview {
  width: min(100%, 180px);
}

.thesis-pdf-thumb {
  width: 100%;
  aspect-ratio: 1 / 1.414;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.12);
  background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 1rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  border: 2px solid #cbd5e1;
}

.thesis-pdf-thumb:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 28px rgba(0,0,0,0.15);
}

.thesis-pdf-icon {
  font-size: 5rem;
  color: #64748b;
}

.thesis-pdf-text {
  text-align: center;
  color: #334155;
}

.thesis-pdf-title {
  font-weight: 700;
  font-size: 0.85rem;
  margin-bottom: 0.15rem;
}

.thesis-pdf-subtitle {
  font-size: 0.7rem;
  color: #64748b;
}

.thesis-lightbox {
  position: fixed;
  inset: 0;
  background: rgba(15, 23, 42, 0.75);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.2s ease;
  z-index: 9999;
}

.thesis-lightbox:target {
  opacity: 1;
  visibility: visible;
}

.thesis-lightbox-backdrop {
  position: absolute;
  inset: 0;
}

.thesis-lightbox-content {
  position: relative;
  max-width: min(95vw, 1400px);
  max-height: 95vh;
  background: #0f172a;
  border-radius: 16px;
  padding: 2.5rem 2rem 1rem 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.thesis-lightbox-media {
  max-width: 100%;
  max-height: 85vh;
  border-radius: 12px;
}

.thesis-lightbox-pdf {
  width: min(93vw, 1350px);
  height: 85vh;
  border: none;
  border-radius: 12px;
}

.thesis-lightbox-caption {
  color: #e2e8f0;
  font-size: 0.95rem;
}

.thesis-lightbox-close {
  position: absolute;
  top: 0.2rem;
  right: 0.75rem;
  background: transparent;
  border: none;
  color: #e2e8f0;
  font-size: 2rem;
  cursor: pointer;
  text-decoration: none;
}

.thesis-lightbox-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(15, 23, 42, 0.8);
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  width: 3rem;
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #e2e8f0;
  font-size: 1.5rem;
  cursor: pointer;
  text-decoration: none;
}

.thesis-lightbox-nav:hover {
  background: rgba(15, 23, 42, 1);
}

.thesis-lightbox-nav-left {
  left: 0.75rem;
}

.thesis-lightbox-nav-right {
  right: 0.75rem;
}

.thesis-lightbox-download {
  align-self: flex-start;
  color: #38bdf8;
  font-weight: 600;
  text-decoration: none;
}

.thesis-lightbox-download:hover {
  text-decoration: underline;
}
</style>

<div class="thesis-section">
<div class="thesis-objective">
<div class="thesis-objective-title">Objective</div>
<div class="thesis-objective-text">
Improved state-of-the-art prediction of protein-small molecule interactions by incorporating 3D protein structural data into a pre-trained multimodal transformer to enhance model generalizability and robustness.
</div>
</div>

<div class="thesis-subtitle">Key Responsibilities & Actions</div>

<ul class="thesis-list">
<li>Constructed a novel dataset of ~185,000 data points by mapping protein sequences to 3D structures from AlphaFold using the Graphein library.</li>
<li>Represented protein structures as graphs and generated node embeddings using the Node2Vec algorithm.</li>
<li>Designed & implemented novel modality fusion techniques (additive & multiplicative) to merge protein sequence and structural embeddings before feeding them into a pre-trained transformer, avoiding costly retraining from scratch.</li>
<li>Trained and evaluated model performance end-to-end, including a gradient boosting (XGBoost) ensemble step, across various data split scenarios (random, cold protein, cold SMILES).</li>
</ul>

<div class="results-section">
<div class="results-title">Key Results</div>

<ul class="results-list">
<li>Validated that the model maintains high performance (~97% accuracy) on standard random splits.</li>
<li>Demonstrated improved generalization, achieving a ~1% accuracy increase on challenging "cold start" splits with unseen small molecules—the primary failure mode of the original model.</li>
<li>Showcased significantly better performance (via MCC score) for rare, underrepresented substrates, highlighting the model's potential for novel discovery.</li>
</ul>
</div>

{{< dashboard >}}
<div class="thesis-gallery-section" id="thesis-gallery">
  <figure class="thesis-figure thesis-arch-preview">
    <a class="thesis-lightbox-trigger" href="#thesis-lightbox-arch-1">
      <div class="thesis-arch-thumb">
        <img src="/projects/msc-thesis/thesis_architecture1.png" alt="Architecture diagram 1" />
        <img src="/projects/msc-thesis/thesis_architecute2.png" alt="Architecture diagram 2" />
      </div>
    </a>
    <figcaption>Model architecture (2 phases)</figcaption>
  </figure>

  <figure class="thesis-figure thesis-mcc-preview">
    <a class="thesis-lightbox-trigger" href="#thesis-lightbox-mcc">
      <img src="/projects/msc-thesis/mcc_with_histogram_mutiplicative_normalized.png" alt="MCC performance analysis" />
    </a>
    <figcaption>The model consistently outperforms the baseline (ProSmith) in classifying data points with substrates that appear in the training set a limited number of times.</figcaption>
  </figure>

  <figure class="thesis-figure thesis-pdf-preview">
    <a class="thesis-lightbox-trigger" href="#thesis-lightbox-pdf">
      <div class="thesis-pdf-thumb">
        <div class="thesis-pdf-icon">📄</div>
        <div class="thesis-pdf-text">
          <div class="thesis-pdf-title">Master's Thesis</div>
          <div class="thesis-pdf-subtitle">Click to view PDF</div>
        </div>
      </div>
    </a>
    <figcaption>MSc Thesis Document</figcaption>
  </figure>
</div>
{{< /dashboard >}}
</div>

<div class="thesis-lightbox" id="thesis-lightbox-arch-1" aria-hidden="true">
  <a class="thesis-lightbox-backdrop" href="#thesis-gallery" aria-label="Close"></a>
  <div class="thesis-lightbox-content" role="dialog" aria-modal="true">
    <a class="thesis-lightbox-close" href="#thesis-gallery" aria-label="Close">×</a>
    <a class="thesis-lightbox-nav thesis-lightbox-nav-right" href="#thesis-lightbox-arch-2" aria-label="Next">›</a>
    <img class="thesis-lightbox-media" src="/projects/msc-thesis/thesis_architecture1.png" alt="Architecture diagram 1" />
    <div class="thesis-lightbox-caption">Architecture diagram - first training phase</div>
  </div>
</div>

<div class="thesis-lightbox" id="thesis-lightbox-arch-2" aria-hidden="true">
  <a class="thesis-lightbox-backdrop" href="#thesis-gallery" aria-label="Close"></a>
  <div class="thesis-lightbox-content" role="dialog" aria-modal="true">
    <a class="thesis-lightbox-close" href="#thesis-gallery" aria-label="Close">×</a>
    <a class="thesis-lightbox-nav thesis-lightbox-nav-left" href="#thesis-lightbox-arch-1" aria-label="Previous">‹</a>
    <img class="thesis-lightbox-media" src="/projects/msc-thesis/thesis_architecute2.png" alt="Architecture diagram 2" />
    <div class="thesis-lightbox-caption">Architecture diagram - final phase</div>
  </div>
</div>

<div class="thesis-lightbox" id="thesis-lightbox-mcc" aria-hidden="true">
  <a class="thesis-lightbox-backdrop" href="#thesis-gallery" aria-label="Close"></a>
  <div class="thesis-lightbox-content" role="dialog" aria-modal="true">
    <a class="thesis-lightbox-close" href="#thesis-gallery" aria-label="Close">×</a>
    <img class="thesis-lightbox-media" src="/projects/msc-thesis/mcc_with_histogram_mutiplicative_normalized.png" alt="MCC performance analysis" />
    <div class="thesis-lightbox-caption">The model consistently outperforms the baseline (ProSmith) in classifying data points with substrates that appear in the training set a limited number of times.</div>
  </div>
</div>

<div class="thesis-lightbox" id="thesis-lightbox-pdf" aria-hidden="true">
  <a class="thesis-lightbox-backdrop" href="#thesis-gallery" aria-label="Close"></a>
  <div class="thesis-lightbox-content" role="dialog" aria-modal="true">
    <a class="thesis-lightbox-close" href="#thesis-gallery" aria-label="Close">×</a>
    <iframe class="thesis-lightbox-pdf"
      src="/projects/msc-thesis/FinalMasterThesis.pdf#page=1&view=FitH&zoom=page-width&toolbar=0&navpanes=0&scrollbar=0"
      title="PDF preview"></iframe>
    <a class="thesis-lightbox-download" href="/projects/msc-thesis/FinalMasterThesis.pdf" download>Download PDF</a>
    <div class="thesis-lightbox-caption">Master's Thesis</div>
  </div>
</div>
