---
title: "Tranformer-based Lane Detection"
nav_label: "Lane Detection"
date: 2023-11-12
draft: false
description: "Transformer-based lane detection that leverages spatiotemporal information from sequential video frames to robustly dynamic road conditions"
tags: ["Computer Vision", "Deep Learning", "Transformers"]
---

<style>
.lane-section {
  margin: 2rem 0;
}

.lane-objective {
  background: linear-gradient(135deg, #fdf4ff 0%, #fae8ff 100%);
  border-left: 4px solid #a855f7;
  padding: 1.5rem;
  border-radius: 8px;
  margin-bottom: 2rem;
}

.lane-objective-title {
  font-weight: 700;
  font-size: 1.1rem;
  color: #7e22ce;
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.lane-objective-title::before {
  content: "🎯";
  font-size: 1.3rem;
}

.lane-objective-text {
  color: #6b21a8;
  line-height: 1.7;
}

.lane-subtitle {
  font-weight: 700;
  font-size: 1.1rem;
  color: #1f2937;
  margin-bottom: 1.25rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e5e7eb;
}

.lane-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.lane-list li {
  position: relative;
  padding-left: 2rem;
  margin-bottom: 1.25rem;
  line-height: 1.7;
  color: #374151;
}

.lane-list li::before {
  content: "▸";
  position: absolute;
  left: 0.5rem;
  color: #a855f7;
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

.lane-gallery-section {
  display: flex;
  flex-direction: column;
  gap: 3.5rem;
  align-items: center;
}

.lane-figure {
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  width: 100%;
}

.lane-figure figcaption {
  color: #6b7280;
  font-size: 0.9rem;
}

.lane-lightbox-trigger {
  cursor: pointer;
  display: block;
  width: 100%;
  text-decoration: none;
}

.lane-lightbox-trigger img,
.lane-lightbox-trigger object {
  width: 100%;
  display: block;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.12);
}

.lane-architecture {
  width: min(100%, 720px);
}

.lane-thumb-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
  justify-items: center;
  max-width: 720px;
  width: 100%;
  margin: 0 auto;
}

.lane-thumb {
  width: 120px;
  aspect-ratio: 1 / 1;
}

.lane-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
}

.lane-pdf-preview {
  width: min(100%, 180px);
}

.lane-pdf-thumb {
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

.lane-pdf-thumb:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 28px rgba(0,0,0,0.15);
}

.lane-pdf-icon {
  font-size: 5rem;
  color: #64748b;
}

.lane-pdf-text {
  text-align: center;
  color: #334155;
}

.lane-pdf-title {
  font-weight: 700;
  font-size: 0.85rem;
  margin-bottom: 0.15rem;
}

.lane-pdf-subtitle {
  font-size: 0.7rem;
  color: #64748b;
}

.lane-lightbox {
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

.lane-lightbox:target {
  opacity: 1;
  visibility: visible;
}

.lane-lightbox-backdrop {
  position: absolute;
  inset: 0;
}

.lane-lightbox-content {
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

.lane-lightbox-media {
  max-width: 100%;
  max-height: 85vh;
  border-radius: 12px;
}

.lane-lightbox-pdf {
  width: min(93vw, 1350px);
  height: 85vh;
  border: none;
  border-radius: 12px;
}

.lane-lightbox-caption {
  color: #e2e8f0;
  font-size: 0.95rem;
}

.lane-lightbox-close {
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

.lane-lightbox-download {
  align-self: flex-start;
  color: #38bdf8;
  font-weight: 600;
  text-decoration: none;
}

.lane-lightbox-download:hover {
  text-decoration: underline;
}

.lane-lightbox-nav {
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

.lane-lightbox-nav:hover {
  background: rgba(15, 23, 42, 1);
}

.lane-lightbox-nav-left {
  left: 0.75rem;
}

.lane-lightbox-nav-right {
  right: 0.75rem;
}
</style>

<div class="lane-section">
<div class="lane-objective">
<div class="lane-objective-title">Objective</div>
<div class="lane-objective-text">
Improve robustness of lane detection through leveraging spatiotemporal context from video sequences by using Transormer-based architecture.
</div>
</div>

<div class="lane-subtitle">Personal Responsibilities & Actions</div>

<ul class="lane-list">
<li>Curated and preprocessed large-scale driving datasets (CULane: 55h / 133k frames, TuSimple), converting lane point annotations into segmentation masks.</li>
<li>Designed and applied a data augmentation pipeline (random flips, rotations ±30°, crops, and normalization) to improve robustness to camera pose changes, occlusions, and viewpoint shifts.</li>
<li>Built a transformer-based segmentation pipeline that leverages temporal information across video frames to improve lane detection consistency.</li>
<li>Evaluated and replaced a ResNet34 backbone with a self-supervised MAE-ViT, validating superior lane-specific feature extraction via custom image-reconstruction experiments.</li>
</ul>

<div class="results-section">
<div class="results-title">Key Results</div>

<ul class="results-list">
<li>Demonstrated MAE-ViT's advantage over CNN backbones for capturing long, thin, and partially occluded lane structures.</li>
<li>Showed that temporal modeling with transformers stabilizes training and improves qualitative lane predictions under challenging conditions.</li>
<li>Delivered a validated proof-of-concept under strict hardware constraints.</li>
</ul>
</div>

{{< dashboard >}}
<div class="lane-gallery-section" id="lane-gallery">
  <figure class="lane-figure lane-architecture">
    <a class="lane-lightbox-trigger" href="#lane-lightbox-architecture">
      <img src="/projects/lane-detection/model_architecture.jpg" alt="Transformer-based lane detection architecture" />
    </a>
    <figcaption>Model Architecture</figcaption>
  </figure>

  <figure class="lane-figure">
    <div class="lane-thumb-grid">
      <div class="lane-thumb">
        <a class="lane-lightbox-trigger" href="#lane-lightbox-sample-1">
          <img src="/projects/lane-detection/lane_1.png" alt="Lane detection sample 1" />
        </a>
      </div>
      <div class="lane-thumb">
        <a class="lane-lightbox-trigger" href="#lane-lightbox-sample-2">
          <img src="/projects/lane-detection/lane_2.png" alt="Lane detection sample 2" />
        </a>
      </div>
      <div class="lane-thumb">
        <a class="lane-lightbox-trigger" href="#lane-lightbox-sample-3">
          <img src="/projects/lane-detection/lane_3.png" alt="Lane detection sample 3" />
        </a>
      </div>
      <div class="lane-thumb">
        <a class="lane-lightbox-trigger" href="#lane-lightbox-sample-4">
          <img src="/projects/lane-detection/lane_4.png" alt="Lane detection sample 4" />
        </a>
      </div>
    </div>
    <figcaption style="text-align: center;">Predicted segmentation masks with ground-truth lanes overlayed</figcaption>
  </figure>

  <figure class="lane-figure lane-pdf-preview">
    <a class="lane-lightbox-trigger" href="#lane-lightbox-pdf">
      <div class="lane-pdf-thumb">
        <div class="lane-pdf-icon">📄</div>
        <div class="lane-pdf-text">
          <div class="lane-pdf-title">Project Report</div>
          <div class="lane-pdf-subtitle">Click to view PDF</div>
        </div>
      </div>
    </a>
    <figcaption>Robust Lane Detection Report</figcaption>
  </figure>
</div>
{{< /dashboard >}}
</div>

<div class="lane-lightbox" id="lane-lightbox-architecture" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <img class="lane-lightbox-media" src="/projects/lane-detection/model_architecture.jpg" alt="Transformer-based lane detection architecture" />
    <div class="lane-lightbox-caption">Model Architecture</div>
  </div>
</div>

<div class="lane-lightbox" id="lane-lightbox-sample-1" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-right" href="#lane-lightbox-sample-2" aria-label="Next">›</a>
    <img class="lane-lightbox-media" src="/projects/lane-detection/lane_1.png" alt="Lane detection sample 1" />
    <div class="lane-lightbox-caption">Lane prediction sample 1</div>
  </div>
</div>

<div class="lane-lightbox" id="lane-lightbox-sample-2" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-left" href="#lane-lightbox-sample-1" aria-label="Previous">‹</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-right" href="#lane-lightbox-sample-3" aria-label="Next">›</a>
    <img class="lane-lightbox-media" src="/projects/lane-detection/lane_2.png" alt="Lane detection sample 2" />
    <div class="lane-lightbox-caption">Lane prediction sample 2</div>
  </div>
</div>

<div class="lane-lightbox" id="lane-lightbox-sample-3" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-left" href="#lane-lightbox-sample-2" aria-label="Previous">‹</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-right" href="#lane-lightbox-sample-4" aria-label="Next">›</a>
    <img class="lane-lightbox-media" src="/projects/lane-detection/lane_3.png" alt="Lane detection sample 3" />
    <div class="lane-lightbox-caption">Lane prediction sample 3</div>
  </div>
</div>

<div class="lane-lightbox" id="lane-lightbox-sample-4" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <a class="lane-lightbox-nav lane-lightbox-nav-left" href="#lane-lightbox-sample-3" aria-label="Previous">‹</a>
    <img class="lane-lightbox-media" src="/projects/lane-detection/lane_4.png" alt="Lane detection sample 4" />
    <div class="lane-lightbox-caption">Lane prediction sample 4</div>
  </div>
</div>

<div class="lane-lightbox" id="lane-lightbox-pdf" aria-hidden="true">
  <a class="lane-lightbox-backdrop" href="#lane-gallery" aria-label="Close"></a>
  <div class="lane-lightbox-content" role="dialog" aria-modal="true">
    <a class="lane-lightbox-close" href="#lane-gallery" aria-label="Close">×</a>
    <iframe class="lane-lightbox-pdf"
      src="/projects/lane-detection/_IAAIP____Robust_Lane_Detection.pdf#page=1&view=FitH&zoom=page-width&toolbar=0&navpanes=0&scrollbar=0"
      title="PDF preview"></iframe>
    <a class="lane-lightbox-download" href="/projects/lane-detection/_IAAIP____Robust_Lane_Detection.pdf" download>Download PDF</a>
    <div class="lane-lightbox-caption">Project Report</div>
  </div>
</div>
