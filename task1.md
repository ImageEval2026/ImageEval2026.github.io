---
title: "Task 1: Ayn-VQA"
layout: content
permalink: /task1/
description: Culturally grounded Arabic spoken visual question answering and image-grounded hallucination detection.
bodyClass: page-task1
---

## Overview

**Ayn-VQA** is a culturally grounded Arabic multimodal benchmark spanning **18 Arab
countries**. It asks how well vision–language models *see* Arab cultural content and
how reliably they tell what is actually in an image from what merely sounds plausible.

The task has two subtasks, each run in two independent language tracks —
**English (EN)** and **Modern Standard Arabic (MSA)** — for **four leaderboards** in
total:

- **Subtask 1a — Spoken VQA:** answer a *spoken* question about an image.
- **Subtask 1c — Hallucination Detection:** decide which statements about an image are real.

You may enter any track of either subtask, independently.

**Quick links:** [Dataset (HuggingFace)](https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA)
· [Starter kit (GitHub)](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1)
· [Register](https://docs.google.com/forms/d/e/1FAIpQLSd1QKF4rXD_gbLJlDykLvB0DGMIogwhraeOtWRiQiotucK0zA/viewform)
· Leaderboards on Codabench (see [Submission](#submission))

---

## Subtask 1a — Spoken VQA

**Goal.** Given an **image** and a **spoken Arabic question** with three spoken
answer options (all in the audio), predict the index of the correct option.

There is no question text — the question and its options are *only* in the audio, so
systems must combine speech understanding with image understanding.

**Input** — one JSONL record per item (the `image` / `audio` paths resolve against the
HuggingFace dataset):

```json
{
  "id": "4a405ef6...d10de6a0",
  "image": "images/4a405ef6...d10de6a0.jpg",
  "audio": "audio/en/4a405ef6...d10de6a0.wav",
  "country": "Algeria",
  "category": "Objects, Materials & Clothing",
  "label": 0
}
```

The audio says, e.g. *"What is shown in this image? Option 0 … Option 1 … Option 2 …"*.
`label` (the correct option index, `0`/`1`/`2`) is provided for `train`/`dev` and
hidden for the test split.

**Output** — a CSV with one row per item: the predicted option index.

```csv
id,prediction
4a405ef6...d10de6a0,0
9b1c2d3e...77aa01ff,2
```

**Evaluation**

| metric | role | meaning |
|---|---|---|
| **accuracy** | **official ranking** | fraction of questions answered correctly |
| balanced accuracy | reported | mean per-class recall over the three option positions |
| macro-F1 | reported | macro-averaged F1 over the three option positions |

---

## Subtask 1c — Hallucination Detection

**Goal.** Given an **image** and **three statements** about it, label each statement
**True** (grounded in the image) or **False** (hallucinated). In every item **exactly
one** statement is grounded; the other two are culturally plausible but not supported
by the image.

**Input** — one JSONL record per item:

```json
{
  "id": "4a405ef6...d10de6a0",
  "image": "images/4a405ef6...d10de6a0.jpg",
  "statements": [
    "Islamic art is prominently featured in this image. True or False?",
    "Abstract art is prominently featured in this image. True or False?",
    "Renaissance art is prominently featured in this image. True or False?"
  ],
  "country": "Algeria",
  "category": "Objects, Materials & Clothing",
  "labels": [true, false, false]
}
```

`labels` is provided for `train`/`dev` and hidden for the test split.

**Output** — a CSV with **three rows per item** (one per statement), each labelled
`true` or `false`:

```csv
id,statement_index,prediction
4a405ef6...d10de6a0,0,true
4a405ef6...d10de6a0,1,false
4a405ef6...d10de6a0,2,false
```

**Evaluation.** The grounded statement is called **Q+**, the two hallucinated ones
**Q−**.

| metric | role | meaning |
|---|---|---|
| **combined accuracy** | **official ranking** | items where **all three** labels are correct |
| hallucination rate | reported | drop from Q+ accuracy to combined accuracy (lower is better) |
| conditional hallucination rate (CFHR-2) | reported | of items whose grounded statement was found, the share that still affirmed a hallucination (lower is better) |
| CFHR-3 | reported | of items with ≥1 correct, the share not fully correct (lower is better) |
| Q+ / Q− / Q− both accuracy | reported | accuracy on the grounded statement, on hallucinated statements, and on getting *both* hallucinations right |

Exact formulas are in the [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/scorer).

---

## Dataset

The data is released on HuggingFace:
**[QCRI/ImageEval2026-Task1-AynVQA](https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA)**.
Each subtask × track ships `train`, `dev`, and `devtest` splits during development; a
blind `test` split is released for the evaluation window. The JSONL files hold the
labels and metadata; **images and audio live in the dataset repo** and are referenced
by the relative `image` / `audio` paths.

Items are tagged with **country** (18 Arab countries) and a cultural
**category**, so you can analyse where your system is strong or weak.

---

## Baselines

The [starter kit](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/baselines)
includes ready-to-run **Colab notebooks** that download the data, run a model, and
write a submission-ready file — open them, flip the `LANG` flag (`en`/`msa`), and run.

| subtask | baseline | reference (devtest) |
|---|---|---|
| 1a | Qwen2.5-Omni-3B (image + audio) | EN accuracy **0.664** · MSA **0.398** |
| 1a | Fanar cascade: speech→text → image LLM (no GPU) | — |
| 1c | Qwen2.5-VL-3B (True/False per statement) | EN combined acc **0.684** · MSA **0.508** |

These are references only — you are free to use any models, prompts, and pipelines.

---

## Submission

1. Produce your predictions in the CSV format shown above.
2. Validate them with the
   [format checker](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/format_checker),
   and optionally score yourself on a labelled split with the
   [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/scorer).
3. Zip the CSV as `prediction.zip` and upload it to the matching Codabench
   competition. Each track is a separate leaderboard:

| subtask | track | Codabench |
|---|---|---|
| 1a — Spoken VQA | English | [competition 17002](https://www.codabench.org/competitions/17002/) |
| 1a — Spoken VQA | MSA | [competition 17001](https://www.codabench.org/competitions/17001/) |
| 1c — Hallucination | English | [competition 17000](https://www.codabench.org/competitions/17000/) |
| 1c — Hallucination | MSA | [competition 16999](https://www.codabench.org/competitions/16999/) |

---

## Getting Started

1. **[Register](https://docs.google.com/forms/d/e/1FAIpQLSd1QKF4rXD_gbLJlDykLvB0DGMIogwhraeOtWRiQiotucK0zA/viewform)** for the shared task.
2. Get the data from **[HuggingFace](https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA)**.
3. Open a **[baseline notebook](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/baselines)**, run it, and submit on **Codabench**.

Questions? See the [FAQ]({{ '/faq/' | relative_url }}) or email
[imageeval2026@gmail.com](mailto:imageeval2026@gmail.com). The dataset is released for
research use under **CC BY-NC 4.0**.
