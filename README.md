# News-Based Systematic Strategies: Evidence from Accessible Providers with Point-In-Time Language Models

> **Confidentiality Note:** The source code and raw data for this project were developed in collaboration with a hedge fund and are proprietary. This repository contains the final Master's Thesis document and a high-level analytical overview of the methodologies and findings.

## Context & Objective
Large language models (LLMs) can extract predictive signals for equity returns from financial news. However, the existing literature relies almost entirely on premium, institutional newswires (e.g., Dow Jones, Reuters). This thesis investigates whether accessible news carries a genuine predictive signal, and whether the "pure news anomaly" of Didisheim et al. (2026) holds when applied to it.

## Data & Methodology
The study runs on 1.6 million single-stock articles provided by Benzinga (distributed via Massive), spanning from 2009 to 2025. The backtest evaluates performance out-of-sample (2014–2025) across two universes: the Nasdaq-100 and a broad universe of >2,000 firms.

The pipeline combines two core methodologies from the recent literature:

* **Point-in-Time LLMs:** Leveraged chronologically consistent models (Kelly et al., 2026) to prevent look-ahead bias from the training corpus. The implementation resolves discrepancies between the published paper and its reference codebase (e.g., token padding, shrinkage penalty scaling), formally acknowledged by the authors.

* **Pure News Residualization:** Orthogonalized news embeddings across an increasing residualization ladder. Ranging from a cross-sectional demean up to 130 JKP characteristics (Didisheim et al., 2026), to isolate novel information and capture delayed market reactions.

## Key Findings

1. **The "Pure News Anomaly" Does Not Replicate on Accessible Data**  
Unlike on premium newswires, the one consistent gain of the residualization ladder is the cross-sectional demean. Beyond it, purging firm characteristics adds little value at best, and degrades performance at the deepest levels. This suggests that the orthogonal component of accessible news either lacks the re-valuing information found in premium feeds, or that the market absorbs it without delay.

2. **Quantification of the "Premium Gap"**  
Accessible news is cheaper, but the price is paid in performance. The research quantifies this trade-off as the Premium Gap: under methodological configurations aligned with the literature, the gap is positive wherever a benchmark reference exists. Corroborated by two distinct premium providers (Dow Jones and Reuters), the accessible feed retains ~60% of the premium Sharpe ratio at shallow residualization, but drops to 10-25% at the deepest purges.

3. **Signal Concentration: Headlines vs. Body**  
On the broad universe, the predictive signal is concentrated in the article headlines, while the body text dilutes it. Restricting the input to headlines strengthens alphas across all benchmarks, achieving significance against factor models as demanding as the 13 theme portfolios of Jensen et al. (2023) while retaining a statistically significant market alpha net of transaction costs.

This stronger input is also the cheapest to embed computationally, a finding particularly relevant to the audience an accessible provider might serve.

## Repository Contents
* `Master_Thesis_Rocco_Ventruto.pdf`: The full research document detailing the mathematical framework, factor exposures, robustness checks, and replication notes regarding reference papers.
