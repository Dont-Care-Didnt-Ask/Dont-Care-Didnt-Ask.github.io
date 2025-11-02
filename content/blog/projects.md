---
title: "Project ideas"
date: 2025-11-02
draft: false
description: "Some of my project ideas, which I did not implement yet."
summary: "Some of my project ideas, which I did not implement yet."
tags: ["research"]
---

## Connection between super-weights and grokking
[The Super Weight in Large Language Models](https://arxiv.org/abs/2411.07191) — a small fraction of Large Language Model (LLM) parameter outliers are disproportionately important to the quality of the model.
[Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets](https://arxiv.org/abs/2201.02177) — prolonged training beyond 0 training loss leads to sudden generalization.

Is there any connection?

To read more recent papers about grokking, check this [presentation](https://docs.google.com/presentation/d/1y14x8oQq2QDqp4mr75IxgJ8A_ZbChJqf5LSNXATGW1g/edit?usp=sharing) for links.

## Decomposition of LLMs latent space into semantic and surface-level/lexical subspaces for uncertainty quantification

Motivation: will allow to decouple surface-level uncertainty (e.g. what synonym to use) vs sematic (e.g. what cognitive technique to use) in uncertainty quantification.

Key question: Is decomposition into semantic / non-semantic subspaces useful for reducing errors?
Minor question: What methods to use to estimate semantic uncertainty
as baselines?
as methods which we enhance with semantic/non-semantic decomposition?

Test set: 1000 questions, open-ended. We evaluate answers manually or by a strong LLM as a Judge.

Experiment:
- LLM with no uncertainty: has to answer all questions, we measure accuracy == A1.
- LLM with usual uncertainty, answer only top-500 questions where LLM is most sure. Measure accuracy == A2.
- LLM with semantic uncertainty, answer only top-500 questions where LLM is most sure. Measure accuracy == A3.

Goal: have a table with three numbers: A1, A2, A3 and all code needed to reproduce this.

Important related work: [Semantic Entropy Probes: Robust and Cheap Hallucination Detection in LLMs](https://arxiv.org/abs/2406.15927).

## Self-interpretation of attention maps
Hypothesis: maybe a language model can explain some parts of its behavior better than external methods like probes/SAEs?

Self-interpretations of attention maps with vision-language models (like Gemma 3).
- Take a prompt.
- Pass through model, collect all attention maps.
- Ask the model to analyze the attention map.

Alternatives: do not use images of attention maps directly, but make a textual description. For example, for each token put top-5 tokens it attends to with their weights.

To identify each attention head function, we might need to run this on multiple prompts, to check whether there are consistent patterns. 
