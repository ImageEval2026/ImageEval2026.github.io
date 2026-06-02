---
title: "Task 1: Ayn-VQA"
layout: content
permalink: /task1/
description: Culturally grounded Arabic visual question answering and image-grounded hallucination detection.
bodyClass: page-task1
---

## Task 1: Culturally Grounded Arabic Visual Question Answering and Hallucination Detection


Ayn-VQA is built on OASIS, a large-scale multimodal dataset spanning 18 MENA countries with approximately 0.92 million images, 14.8 million QA pairs, and 3.7 million spoken questions in Modern Standard Arabic, Egyptian Arabic, and Levantine Arabic. The task is organized into three tracks covering spoken question answering, textual question answering, and image-grounded hallucination detection.

### Subtask 1A: Spoken MCQ Visual Question Answering

**Objective:** Given an image and a spoken Arabic question about its content, participants predict the correct answer from multiple-choice options. The track evaluates semantic understanding under speech recognition and dialectal variation.

**Dataset:** This track uses an OASIS subset with approximately 50,000 to 100,000 images selected to preserve diversity across language variety, country, and topic. Participants receive training, development, dev-test, and hidden test splits.

**Submission format:** Submit a TSV file with one prediction per line:

- `id`
- `label` - predicted answer option: A, B, C, or D

**Evaluation:** The official metric is accuracy. F1-score is reported as a secondary metric.


### Subtask 1B: Image-Grounded Hallucination Detection

**Objective:** Systems distinguish image-supported statements from culturally plausible but visually unsupported alternatives. Each instance presents an image with one grounded true statement and two counterfactual statements.

**Dataset:** This contrastive subset of OASIS structures each example as a triplet: one grounded true statement and two plausible but visually unsupported counterfactuals.

**Submission format:** Submit a TSV file with one prediction per line:

- `id`
- `data` - True or False

**Evaluation:** The official metric is Contrastive Instability (CI), which measures whether a system resolves each triplet consistently rather than individual statements in isolation.

`CI = 1 - N_consistent / N_partial`

Lower CI is better. Per-statement accuracy is also reported as a secondary metric.
