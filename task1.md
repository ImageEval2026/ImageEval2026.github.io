---
title: "Task 1: Ayn-VQA"
layout: content
permalink: /task1/
description: Culturally grounded Arabic spoken visual question answering and image-grounded hallucination detection.
bodyClass: page-task1
---

<div class="task1-intro" markdown="1">
**Ayn-VQA** is a culturally grounded Arabic multimodal benchmark covering **18 Arab countries**. It tests how well vision-language models understand Arab cultural imagery, and how reliably they tell what is really in an image apart from what only sounds right.
</div>

<div class="quick-links">
  <a href="https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA">📦 Dataset</a>
  <a class="secondary" href="https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1">🧰 Starter kit</a>
  <a class="secondary" href="https://docs.google.com/forms/d/e/1FAIpQLSd1QKF4rXD_gbLJlDykLvB0DGMIogwhraeOtWRiQiotucK0zA/viewform">📝 Register</a>
  <a class="secondary" href="#submission">🏆 Leaderboards</a>
</div>

## Overview

Task 1 has **two subtasks**, each offered in **two language tracks** (English and Modern Standard Arabic). That makes **four separate leaderboards**, and you may enter any of them independently.

<div class="pills">
  <span>Spoken VQA (1a)</span>
  <span>Hallucination Detection (1c)</span>
  <span>English track</span>
  <span>MSA track</span>
</div>

| Subtask | What you are given | What you predict |
|---|---|---|
| **1a. Spoken VQA** | an image and a spoken question with three spoken options | the index of the correct option (`0`, `1`, or `2`) |
| **1c. Hallucination Detection** | an image and three statements | True or False for each statement (exactly one is true) |

## Subtask 1a: Spoken VQA

Given an image and a **spoken** Arabic question with three spoken answer options, predict which option is correct. The question and the options live **only in the audio**, so a system has to listen and look at the same time.

<p class="lead-label">Input</p>

One JSON record per item. The `image` and `audio` paths resolve inside the HuggingFace dataset.

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

The audio says something like *"What is shown in this image? Option 0 ... Option 1 ... Option 2 ..."*. The correct index `label` (`0`, `1`, or `2`) is provided for `train` and `dev`, and withheld for `test`.

<p class="lead-label">Output</p>

A CSV with one row per item: the predicted option index.

```csv
id,prediction
4a405ef6...d10de6a0,0
9b1c2d3e...77aa01ff,2
```

<p class="lead-label">Evaluation</p>

| Metric | Role | What it measures |
|---|---|---|
| **accuracy** | official ranking | share of questions answered correctly |
| balanced accuracy | secondary | mean per-class recall across the three option positions |
| macro-F1 | secondary | macro-averaged F1 across the three option positions |

## Subtask 1c: Hallucination Detection

Given an image and **three statements** about it, label each statement **True** (grounded in the image) or **False** (hallucinated). In every item, exactly one statement is grounded; the other two are culturally plausible but not supported by the image.

<p class="lead-label">Input</p>

One JSON record per item.

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

The `labels` list is provided for `train` and `dev`, and withheld for `test`.

<p class="lead-label">Output</p>

A CSV with three rows per item, one per statement.

```csv
id,statement_index,prediction
4a405ef6...d10de6a0,0,true
4a405ef6...d10de6a0,1,false
4a405ef6...d10de6a0,2,false
```

<p class="lead-label">Evaluation</p>

The grounded statement is called **Q+**; the two hallucinated ones are **Q−**.

| Metric | Role | What it measures |
|---|---|---|
| **combined accuracy** | official ranking | items where all three labels are correct |
| Q+ accuracy | secondary | the grounded statement correctly marked true |
| Q− accuracy | secondary | hallucinated statements correctly marked false |
| both-Q− accuracy | secondary | both hallucinations marked false in the same item |
| hallucination rate | secondary | gap between Q+ accuracy and combined accuracy (lower is better) |
| conditional rate (CFHR-2) | secondary | of items whose true statement was found, the share that still affirmed a hallucination (lower is better) |
| CFHR-3 | secondary | of items with at least one correct label, the share not fully correct (lower is better) |

Exact formulas live in the [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/scorer).

## Dataset

The data is on HuggingFace: [QCRI/ImageEval2026-Task1-AynVQA](https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA).

Every subtask and track ships `train`, `dev`, and `devtest` splits during development. A blind `test` split is released for the evaluation window. The JSONL files hold the labels and metadata; the **images and audio live in the dataset repo** and are referenced by the relative `image` and `audio` paths. Items are tagged with their **country** (18 Arab countries) and a cultural **category**, so you can see where your system is strong or weak.

## Baselines

The [starter kit](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/baselines) ships ready-to-run **Colab notebooks** that download the data, run a model, and write a submission-ready file. Open one, set the `LANG` flag (`en` or `msa`), and run.

| Subtask | Baseline | Reference score (devtest) |
|---|---|---|
| 1a | Qwen2.5-Omni-3B (image + audio) | accuracy: EN `0.664`, MSA `0.398` |
| 1a | Fanar cascade (speech to text, then image LLM) | runs without a GPU |
| 1c | Qwen2.5-VL-3B (True/False per statement) | combined accuracy: EN `0.684`, MSA `0.508` |

These are starting points only. You are free to use any models, prompts, and pipelines.

## Submission

1. Produce predictions in the CSV format shown above.
2. Validate them with the [format checker](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/format_checker), and check your score locally on a labelled split with the [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/scorer).
3. Zip the CSV as `prediction.zip` and upload it to the matching Codabench leaderboard.

| Subtask | Track | Leaderboard |
|---|---|---|
| Spoken VQA (1a) | English | [Codabench 17002](https://www.codabench.org/competitions/17002/) |
| Spoken VQA (1a) | MSA | [Codabench 17001](https://www.codabench.org/competitions/17001/) |
| Hallucination (1c) | English | [Codabench 17000](https://www.codabench.org/competitions/17000/) |
| Hallucination (1c) | MSA | [Codabench 16999](https://www.codabench.org/competitions/16999/) |

## Getting Started

1. [Register](https://docs.google.com/forms/d/e/1FAIpQLSd1QKF4rXD_gbLJlDykLvB0DGMIogwhraeOtWRiQiotucK0zA/viewform) for the shared task.
2. Get the data from [HuggingFace](https://huggingface.co/datasets/QCRI/ImageEval2026-Task1-AynVQA).
3. Open a [baseline notebook](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/baselines), run it, and submit on Codabench.

Questions? See the [FAQ]({{ '/faq/' | relative_url }}) or email [imageeval2026@gmail.com](mailto:imageeval2026@gmail.com). The dataset is released for research use under CC BY-NC 4.0.
