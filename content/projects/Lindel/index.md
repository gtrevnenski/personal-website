---
title: "Lindel"
nav_label: "Lindel"
date: 2023-04-15
draft: false
description: "Reproducing, Evaluating and Interpreting the Lindel Model for CRISPR-Cas9 Repair Outcome Prediction"
tags: ["Bioinformatics", "Machine Learning", "Model Interpretation"]
github: "https://github.com/gtrevnenski/L1-Lindel"
---

<style>
.lindel-section {
  margin: 2rem 0;
}

.lindel-objective {
  background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
  border-left: 4px solid #3b82f6;
  padding: 1.5rem;
  border-radius: 8px;
  margin-bottom: 2rem;
}

.lindel-objective-title {
  font-weight: 700;
  font-size: 1.1rem;
  color: #1e40af;
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.lindel-objective-title::before {
  content: "🎯";
  font-size: 1.3rem;
}

.lindel-objective-text {
  color: #1e3a8a;
  line-height: 1.7;
}

.lindel-subtitle {
  font-weight: 700;
  font-size: 1.1rem;
  color: #1f2937;
  margin-bottom: 1.25rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e5e7eb;
}

.lindel-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.lindel-list li {
  position: relative;
  padding-left: 2rem;
  margin-bottom: 1.25rem;
  line-height: 1.7;
  color: #374151;
}

.lindel-list li::before {
  content: "▸";
  position: absolute;
  left: 0.5rem;
  color: #3b82f6;
  font-weight: 700;
  font-size: 1.2rem;
}

.lindel-results-section {
  background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
  border-left: 4px solid #10b981;
  padding: 1.5rem;
  border-radius: 8px;
  margin-top: 2rem;
}

.lindel-results-title {
  font-weight: 700;
  font-size: 1.1rem;
  color: #065f46;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.lindel-results-title::before {
  content: "✅";
  font-size: 1.3rem;
}

.lindel-results-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.lindel-results-list li {
  position: relative;
  padding-left: 2rem;
  margin-bottom: 1rem;
  line-height: 1.7;
  color: #064e3b;
}

.lindel-results-list li::before {
  content: "✓";
  position: absolute;
  left: 0.5rem;
  color: #10b981;
  font-weight: 700;
  font-size: 1.3rem;
}

.lindel-results-list li strong {
  color: #047857;
  font-weight: 600;
}
</style>

<div class="lindel-section">
<div class="lindel-objective">
<div class="lindel-objective-title">Objective</div>
<div class="lindel-objective-text">
In a collaborative academic project, our team reproduced and validated key findings from Chen et al.'s seminal work on predicting CRISPR-Cas9 DNA repair outcomes. My individual contribution centered on interpreting the model's internal logic to assess whether the logistic regression model used to predict the insertion–deletion (indel) ratio learns the same sequence context importance as reported in the original paper.
</div>
</div>

<div class="lindel-subtitle">Key Responsibilities & Actions</div>

<ul class="lindel-list">
<li>Successfully replicated the core functionality of the Lindel machine learning model, confirming both its superiority over a baseline model and the high reproducibility of mutational outcomes across experiments.</li>
<li>Performed learned weights analysis of the neural network to understand the model's decision-making process.</li>
<li>Applied SHAP (SHapley Additive exPlanations) to quantify feature importance and identify which sequence elements drive predictions.</li>
<li>Conducted Multiple Correspondence Analysis (MCA) to examine relationships in categorical sequence data and validate claimed dinucleotide patterns.</li>
<li>Critically evaluated the authors' claims regarding sequence context importance through complementary interpretability techniques.</li>
</ul>

<div class="lindel-results-section">
<div class="lindel-results-title">Key Results</div>

<ul class="lindel-results-list">
<li><strong>Confirmed</strong> the strong influence of a single nucleotide ('T') at the cut site (position 17), though its impact on model predictions differed from the paper's biochemical interpretation.</li>
<li><strong>Questioned</strong> the reported importance of specific dinucleotides (e.g., TG, CG, GA), as their effects were not consistently supported across interpretability analyses.</li>
<li><strong>Concluded</strong> that the model relies more heavily on single-nucleotide features than originally proposed, offering a more nuanced and critical understanding of the model's decision-making process.</li>
</ul>
</div>
</div>
