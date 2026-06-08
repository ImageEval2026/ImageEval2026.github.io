---
title: "Task 1"
layout: content
permalink: /task1/
description: Culturally grounded Arabic spoken visual question answering and image-grounded hallucination detection.
bodyClass: page-task1
---

<div class="task1-intro" markdown="1">
**Task 1** is a culturally grounded Arabic multimodal benchmark covering **18 Arab countries**. It tests how well vision-language models understand Arab cultural imagery, and how reliably they tell what is really in an image apart from what only sounds right.
</div>

<div class="quick-links">
  <a href="https://huggingface.co/datasets/QCRI/AynVQA">📦 Dataset</a>
  <a class="secondary" href="https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1">🧰 Starter kit</a>
  <a class="secondary" href="https://docs.google.com/forms/d/e/1FAIpQLSd1QKF4rXD_gbLJlDykLvB0DGMIogwhraeOtWRiQiotucK0zA/viewform">📝 Register</a>
  <a class="secondary" href="#submission">🏆 Leaderboards</a>
</div>

## Overview

Task 1 has **two subtasks**, each offered in **two language tracks** (English and Modern Standard Arabic). That makes **four separate leaderboards**, and you may enter any of them independently.

<div class="pills">
  <span>Spoken VQA (1a)</span>
  <span>Hallucination Detection (1b)</span>
  <span>English track</span>
  <span>MSA track</span>
</div>

| Subtask | What you are given | What you predict |
|---|---|---|
| **1a. Spoken VQA** | an image and a spoken question with three spoken options | the index of the correct option (`0`, `1`, or `2`) |
| **1b. Hallucination Detection** | an image and three statements | True or False for each statement (exactly one is true) |

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

## Subtask 1b: Hallucination Detection

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

The data for **Task 1** is on available HuggingFace: [ImageEval2026 Task1 data](https://huggingface.co/datasets/QCRI/AynVQA).

The **images and audio live there**; the JSONL records reference them by relative `image` and `audio` paths. Labels and metadata are included for `train` and `dev` only; `devtest` and the blind `test` split are released without labels.

| Split | Labels | Items | Use |
|---|---|---|---|
| `train` | yes | 3,000 | training and fine-tuning |
| `dev` | yes | 500 | local validation (run the scorer here) |
| `devtest` | no | 500 | development-phase leaderboard |
<!-- | `test` | no | 1,000 | blind final ranking | -->

The `train` and `dev` records also carry `country` (one of 18 Arab countries) and a cultural `category`, so you can break results down by region and topic.

For Subtask 1a, the `train`, `dev`, and `devtest` audio is synthetic (voice cloning); the blind `test` audio is human-recorded, so expect a shift in speaker and recording conditions.

## Starter Kit

The [starter kit](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/baselines) ships three ready-to-run **Colab notebooks** that download the data, run a model, and write a submission-ready file. Set the `LANG` flag (`en` or `msa`) and run. Each link below opens the notebook straight in Colab, with no need to browse the repository.

The first two are **reference baselines** with published scores. The third is a no-GPU **cascaded example** that shows an alternative system design (speech-to-text into an image model).

| Subtask | Notebook | Score (devtest) | Colab |
|---|---|---|---|
| 1a | Qwen2.5-Omni-3B baseline (image + audio) | accuracy: EN `0.664`, MSA `0.398` | [Open in Colab](https://colab.research.google.com/github/ImageEval2026/ImageEval2026-tasks/blob/main/task1/baselines/baseline_task1a_colab.ipynb) |
| 1b | Qwen2.5-VL-3B baseline (True/False per statement) | combined accuracy: EN `0.684`, MSA `0.508` | [Open in Colab](https://colab.research.google.com/github/ImageEval2026/ImageEval2026-tasks/blob/main/task1/baselines/baseline_task1b_colab.ipynb) |
| 1a | Fanar cascade example (no GPU) | not scored | [Open in Colab](https://colab.research.google.com/github/ImageEval2026/ImageEval2026-tasks/blob/main/task1/baselines/baseline_task1a_fanar_cascade_colab.ipynb) |

## Participation

You may use **any model and any pipeline**, cascaded or end to end. For Subtask 1a, you might transcribe the audio and pass the text to a vision-language model, or use a single multimodal model that reads the audio and image directly. We encourage creative approaches: data augmentation, model merging, new cascade designs (for example, speech recognition then translation then reasoning), and novel prompting are all welcome.

**Open and closed models are both allowed.** We especially encourage open models, since they suit low-resource settings and make results easier to reproduce.

**Please take part in good faith and run each track end to end in its own language.** Because the English and MSA tracks share the same images and answers (the questions are translations of each other), it is technically possible to copy one track's predictions onto the other. Please do not. Build a system that actually processes each track's own audio and statements. A pipeline that goes through translation is welcome, as long as it consumes the track's real inputs.

Every registered team is expected to submit a short **system description paper**. See the [submission guidelines]({{ '/submission/' | relative_url }}) and the [FAQ]({{ '/faq/' | relative_url }}).

## Submission

1. Produce predictions in the CSV format shown above.
2. Validate them with the [format checker](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/format_checker), and check your score locally on a labelled split with the [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/scorer).
3. Zip the CSV as `prediction.zip` and upload it to the matching Codabench leaderboard.

| Subtask | Track | Leaderboard |
|---|---|---|
| Spoken VQA (1a) | English | [Codabench 17002](https://www.codabench.org/competitions/17002/) |
| Spoken VQA (1a) | MSA | [Codabench 17001](https://www.codabench.org/competitions/17001/) |
| Hallucination (1b) | English | [Codabench 17000](https://www.codabench.org/competitions/17000/) |
| Hallucination (1b) | MSA | [Codabench 16999](https://www.codabench.org/competitions/16999/) |

## Questions

See the [FAQ]({{ '/faq/' | relative_url }}) or email [imageeval2026@gmail.com](mailto:imageeval2026@gmail.com). The dataset is released for research use under CC BY-NC 4.0.
