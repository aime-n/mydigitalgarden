---
{"dg-publish":true,"permalink":"/training-objectives/"}
---


Training Objectives — Organized Visual Cheat Sheet

Think in 4 layers:
1) Prediction type
2) What must be optimized
3) Metric used to evaluate
4) Loss used to train

==================================================
1️⃣ CLASSIFICATION OBJECTIVES
==================================================

A. Standard Classification
- Optimize: overall correctness
- Metric: Accuracy
- Train with: Cross-Entropy
- Use when: classes balanced, mistakes equally costly

--------------------------------------------------

B. Precision-Critical Classification
- Optimize: minimize False Positives
- Metric: Precision
- Train with:
  - weighted cross-entropy
  - focal loss
- Use when: false alarms expensive

Examples:
- fraud confirmation
- legal accusation models
- high-precision medical tests

--------------------------------------------------

C. Recall-Critical Classification
- Optimize: minimize False Negatives
- Metric: Recall / Sensitivity
- Train with:
  - class weighting
  - focal loss
- Use when: missing positives dangerous

Examples:
- cancer screening
- intrusion detection
- safety alerts

--------------------------------------------------

D. Balanced Precision-Recall
- Optimize: trade-off FP vs FN
- Metric:
  - F1 score
  - Fβ score
- Train with:
  - cross-entropy + threshold tuning
  - cost-sensitive loss
- Use when: both types of errors matter

--------------------------------------------------

E. Imbalanced Classification (rare events)
- Optimize: ranking of positives above negatives
- Metric:
  - PR-AUC (best)
  - ROC-AUC
- Train with:
  - focal loss
  - weighted CE
  - sampling strategies
- Use when: positives very rare

==================================================
2️⃣ REGRESSION OBJECTIVES
==================================================

A. Squared Error Focus
- Optimize: penalize large errors strongly
- Metric: RMSE / MSE
- Train with: MSE
- Use when: big mistakes very bad

--------------------------------------------------

B. Robust Error Focus
- Optimize: stable predictions with outliers
- Metric: MAE
- Train with: MAE
- Use when: noisy targets

--------------------------------------------------

C. Balanced Regression
- Optimize: mix of stability + sensitivity
- Metric: RMSE or MAE
- Train with: Huber Loss
- Use when: moderate outliers

==================================================
3️⃣ RANKING / ORDERING OBJECTIVES
==================================================

A. Pairwise Ranking
- Optimize: positives ranked above negatives
- Metric:
  - AUC
  - NDCG
- Train with:
  - pairwise loss
  - hinge ranking loss
- Use when: order matters more than label

Examples:
- search engines
- recommendation feeds
- ads ranking

--------------------------------------------------

B. Top-K Ranking
- Optimize: best results at top
- Metric:
  - NDCG@K
  - Recall@K
- Train with:
  - listwise ranking loss
- Use when: only first results matter

==================================================
4️⃣ PROBABILITY / GENERATIVE OBJECTIVES
==================================================

A. Likelihood Maximization
- Optimize: probability of observed data
- Metric: Log-Likelihood / Perplexity
- Train with:
  - Negative Log Likelihood
- Use when: predicting distributions

Examples:
- language models
- sequence models
- probabilistic classifiers

--------------------------------------------------

B. Distribution Matching
- Optimize: similarity between distributions
- Metric: KL divergence
- Train with:
  - KL loss
  - variational objectives
- Use when: generative modeling

Examples:
- VAEs
- Bayesian learning
- distillation

==================================================
5️⃣ REPRESENTATION LEARNING OBJECTIVES
==================================================

A. Similarity Learning
- Optimize: similar items close in embedding space
- Metric:
  - cosine similarity
  - retrieval accuracy
- Train with:
  - contrastive loss
  - InfoNCE
- Use when: embeddings needed

Examples:
- semantic search
- sentence embeddings
- image retrieval

--------------------------------------------------

B. Identity / Instance Separation
- Optimize: same item closer than others
- Train with:
  - triplet loss
- Use when: identity discrimination needed

Examples:
- face recognition
- speaker recognition
- product matching

==================================================
FAST SELECTION MAP
==================================================

If predicting labels → Cross-Entropy  
If rare positives → PR-AUC mindset  
If predicting numbers → MSE / Huber  
If ordering results → Ranking loss  
If learning embeddings → Contrastive loss  
If modeling probability → NLL / KL  

FAST SELECTION MAP — TRAINING OBJECTIVES (EXTENDED)

Use this when choosing:
- loss
- evaluation metric
- optimization goal

==================================================
1️⃣ IF PREDICTING CLASSES
==================================================

Balanced classes + equal mistake cost
→ Train: Cross-Entropy
→ Evaluate: Accuracy

--------------------------------------------------

False Positives are costly
→ Optimize: Precision
→ Evaluate: Precision curve
→ Train: weighted CE / focal loss
→ Typical: fraud confirmation, legal flags

--------------------------------------------------

False Negatives are dangerous
→ Optimize: Recall (Sensitivity)
→ Evaluate: Recall curve
→ Train: class weighting / focal loss
→ Typical: disease detection, safety alerts

--------------------------------------------------

Both FP and FN matter
→ Optimize: F1 score
→ Evaluate: F1
→ Train: CE + threshold tuning
→ Typical: document classification, search filters

--------------------------------------------------

Classes highly imbalanced (rare positives)
→ Optimize: PR-AUC  ⭐ best choice
→ Evaluate: Precision-Recall curve
→ Train: focal loss / reweighting / resampling
→ Typical: fraud, anomaly detection, medical screening

--------------------------------------------------

Need threshold-independent ranking quality
→ Optimize: ROC-AUC
→ Evaluate: ROC curve
→ Train: CE or ranking-aware losses
→ Typical: credit scoring, click prediction

==================================================
2️⃣ IF PREDICTING NUMBERS (REGRESSION)
==================================================

Large errors very bad
→ Train: MSE
→ Evaluate: RMSE

Outliers present
→ Train: MAE
→ Evaluate: MAE

Need balance of both
→ Train: Huber
→ Evaluate: RMSE + MAE

Need probabilistic outputs
→ Train: Gaussian NLL
→ Evaluate: log-likelihood

==================================================
3️⃣ IF ORDER MATTERS MORE THAN LABELS
==================================================

Need good global ranking
→ Optimize: AUC
→ Train: pairwise ranking loss

Only top results matter
→ Optimize: NDCG@K / Recall@K
→ Train: listwise ranking loss

Binary relevance but ranking critical
→ Optimize: PR-AUC or ROC-AUC
→ Train: CE or ranking-aware loss

==================================================
4️⃣ IF LEARNING EMBEDDINGS / SIMILARITY
==================================================

Need semantic similarity
→ Train: contrastive / InfoNCE
→ Evaluate: retrieval accuracy

Need identity discrimination
→ Train: triplet loss
→ Evaluate: verification accuracy

Need clustering-friendly space
→ Train: contrastive + temperature scaling
→ Evaluate: silhouette / retrieval metrics

==================================================
5️⃣ IF MODEL OUTPUTS PROBABILITIES
==================================================

Need calibrated probabilities
→ Train: Cross-Entropy / NLL
→ Evaluate: Brier score / log loss

Need distribution matching
→ Train: KL divergence
→ Evaluate: KL / likelihood

Need generative modeling
→ Train: NLL / variational loss
→ Evaluate: perplexity / likelihood

==================================================
MENTAL SHORTCUTS (ENGINEER VERSION)
==================================================

Accuracy failing on rare events?
→ switch to PR-AUC mindset

Too many false alarms?
→ optimize Precision or Fβ (β < 1)

Missing important positives?
→ optimize Recall or Fβ (β > 1)

Need single balanced score?
→ use F1

Need threshold-free comparison?
→ use ROC-AUC

Rare positives + decision thresholds important?
→ PR curve > ROC curve

Need ordering quality?
→ ranking loss / AUC / NDCG

Predicting continuous values?
→ MSE unless outliers → Huber

Learning embeddings?
→ contrastive / triplet

==================================================

==================================================