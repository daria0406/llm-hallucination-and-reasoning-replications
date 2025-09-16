# Replications of LLM Fact-Checking Papers

This repository contains replication studies of two recent papers at the intersection of large language models (LLMs), hallucinations, and misinformation detection. Both replications are conducted as part of a predoctoral research project, applying methods on PolitiFact and LIAR datasets.

## Part 1 — MiniCheck: Is LLM Hallucination Usable?
Reference: Chen, C., Feng, Z., Zhang, Z., Qiang, J., Xu, G., & Li, Y. (2024). Is LLMs Hallucination Usable?. arXiv preprint arXiv:2404.10774. 

- Objective of the paper: The MiniCheck framework investigates whether LLM hallucinations—often treated as noise—can be decomposed into useful, verifiable sub-claims that assist fact-checking.
- Replication notebook: minicheck/MiniCheck_Method.ipynb
- Replication Methodology
  1. Claim Decomposition: Each claim is broken into atomic sub-claims with an LLM.
  2. Sub-Claim Verification: For each sub-claim, the model outputs reasoning and a verdict (Supported, Contradicted, Not Enough Information) relative to provided evidence.
  3. MiniCheck Verdict: Aggregation of sub-claim verdicts yields a final binary prediction (True / False).
  4. Evaluation: Model outputs compared with PolitiFact ground truth. Metrics include accuracy, classification reports, and confusion matrices.
- Replication Goals
  1. Test robustness of decomposition and verification stages.
  2. Compare MiniCheck verdicts against original dataset labels.
  3. Assess the usability of hallucinated decompositions in fact-checking tasks.

## Part 2 — LLM-Based Negative Reasoning for Fake News Detection (NRFE)
Reference: Wu, X., Li, J., Xu, C., & others. (2023). LLM-based Negative Reasoning for Fake News Detection. arXiv preprint arXiv:2503.09153

- Objective of the paper: This paper introduces the Negative Reasoning with Fake News Examples (NRFE) approach, where LLMs generate not only supportive rationales but also negative reasoning—why a claim might be false—leveraging these for improved detection.
- Replication notebook: NRFE/LLMBasedNegativeReasoningForFakeNewsDetection_NRFE.ipynb
- Replication Methodology
    1. Dataset: PolitiFact JSON dataset split into train/validation/test subsets.
    2. Data Augmentation: Each claim expanded with positive and negative prompts, generating synthetic rationales.
    3. Teacher Model: Fine-tuning of a large model (unsloth/llama-3.2-1b) on augmented claims.
    4. Soft Labels: Teacher generates probability distributions (soft targets).
    5. Student Model: A smaller model (distilbert-base-uncased) distilled from teacher outputs using knowledge distillation (hard + soft label losses).
    6. Evaluation: Performance measured on validation/test splits for fake news detection.

## Datasets
- LIAR: Short political statements with labels (True, Mostly True, False, etc.).
- PolitiFact: Fact-check dataset with rich claim–evidence pairs.

## Purpose
This repository is part of a predoctoral research project, aiming to replicate and evaluate cutting-edge approaches in LLM reasoning, hallucination usability, and fake news detection.