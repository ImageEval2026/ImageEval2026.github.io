---
title: "Task 2: CRAI-Bench"
layout: content
permalink: /task2/
description: Cultural accuracy evaluation for Arabic text-to-image generation.
bodyClass: page-task2
---

<div class="task2-intro" markdown="1">
**Task 2: CRAI-Bench** is the first shared task targeting cultural accuracy in Arabic text-to-image generation. It evaluates whether AI-generated images faithfully represent Qatari and Arab cultural scenes using the **Cultural Representation Accuracy Index (CRAI)** — a five-dimensional scoring framework validated against human annotation.
</div>

<div class="quick-links">
  <a href="https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task2">🧰 Starter kit</a>
  <a class="secondary" href="https://drive.google.com/drive/u/1/folders/1aCU3O9TgggLTGwJWtAN5SNIfydL4mKrS?usp=sharing">📦 Dataset</a>
  <a class="secondary" href="https://join.slack.com/t/mm-eval/shared_invite/zt-41j09ml4j-WMn0NzhqAgT9ZK6e1L8eBA">💬 Join Slack</a>
  <a class="secondary" href="#submission">🏆 Leaderboard</a>
</div>

## Overview

Given a **reference image** of an authentic Qatari cultural scene, an **image caption**, and an **AI-generated image** produced from that caption, participants develop systems that predict CRAI scores across five cultural accuracy dimensions. Systems are ranked by Spearman correlation against human-annotated gold scores.

The core challenge: our pilot study showed that GPT-4 as a judge achieves a Spearman correlation of **0.6250** against human annotators, with near-zero correlation on hallucination detection. Can you build a system that better aligns with human cultural judgment?

<div class="pills">
  <span>Cultural Accuracy Evaluation</span>
  <span>Qatari Culture</span>
  <span>LLM-as-a-Judge</span>
</div>

| Input | Output |
|---|---|
| Reference image + caption + AI-generated image | CRAI scores across 5 dimensions (0–1) |

## Task Description

Given three elements per instance — a **reference image**, a **caption**, and an **AI-generated image** produced from that caption — participants predict CRAI scores across five dimensions.

<p class="lead-label">Input</p>

One row per instance in `captions.tsv`:

```
id              image_id    version    caption
img_001_v1      img_001     v1         Generate an image of a Qatari man wearing a white thobe...
img_001_v2      img_001     v2         A man wearing traditional Gulf attire...
```

Each instance also has two associated images: a reference image (`ref/img_001.jpg`) and a generated image (`generated/img_001_v1.png`).

<p class="lead-label">Output</p>

A TSV file with one row per instance:

```
id            CRAI_CEA  CRAI_CC  CRAI_CS  CRAI_CI  CRAI_HP  CRAI_composite
img_001_v1    0.90      0.85     0.75     0.88     0.05     0.82
img_001_v2    0.60      0.55     0.50     0.70     0.05     0.58
```

<p class="lead-label">Evaluation</p>

| Metric | Role | What it measures |
|---|---|---|
| **Spearman correlation** | official ranking | correlation between predicted and gold CRAI_composite scores (higher is better) |
| MAE | secondary / tiebreaker | mean absolute error on CRAI_composite (lower is better) |
| Per-dimension Spearman | diagnostic | CEA, CC, CS, CI, HP reported separately on leaderboard |

## CRAI Framework

The Cultural Representation Accuracy Index (CRAI) scores images across five dimensions:

| Dimension | Code | Weight | Description |
|---|---|---|---|
| Cultural Element Accuracy | CEA | 0.30 | Are expected cultural elements present and correctly depicted? |
| Contextual Coherence | CC | 0.20 | Are elements placed in culturally appropriate settings? |
| Cultural Specificity | CS | 0.20 | How specific is the depiction to the target culture? |
| Cultural Integrity | CI | 0.20 | Is the representation truthful and free of distortion? |
| Hallucination Penalty | HP | −0.10 | Are there fabricated cultural elements not in the caption? |

```
CRAI_composite = 0.30 × CEA + 0.20 × CC + 0.20 × CS + 0.20 × CI − 0.10 × HP
```

**Cultural Specificity (CS) uses fixed tiers:**

| Score | Meaning |
|---|---|
| 1.00 | Uniquely Qatari / target culture |
| 0.75 | Strongly associated with target culture |
| 0.50 | Regionally common across the Arab world |
| 0.25 | Generic Middle Eastern or vague |
| 0.00 | No cultural specificity |

**Score interpretation:** ≥ 0.85 highly accurate · 0.70–0.84 mostly accurate · 0.50–0.69 moderate · 0.30–0.49 weak · < 0.30 poor or misleading.

## Dataset

The dataset consists of (reference image, caption, AI-generated image) triples grounded in Qatari culture. Each of 40 reference images has **5 caption versions** varying in cultural specificity from fully Qatari-specific (v1) to entirely generic (v5).

| Split | Images | Instances | Gold Labels |
|---|---|---|---|
| `train` | 24 | 120 | yes |
| `dev` | 8 | 40 | yes |
| `test` | 8 | 40 | no (blind) |

Cultural categories covered: **people and traditional attire**, **architecture and built environment**, **objects**.

TSV files and Images are available on [Google Drive](https://drive.google.com/drive/u/1/folders/1aCU3O9TgggLTGwJWtAN5SNIfydL4mKrS?usp=sharing).

## Baselines

The [starter kit](https://github.com/YOUR_USERNAME/crai-bench/tree/main/baselines) includes two ready-to-run baseline scripts.

| System | Spearman | MAE | Description |
|---|---|---|---|
| Mean baseline | N/A | 0.3450 | Predicts training set mean for every instance — floor to beat |
| GPT-4 via OpenRouter | 0.6250 | 0.2248 | LLM-as-a-judge with full CRAI rubric — organizer baseline |

```bash
# Run the GPT-4 baseline
python baselines/baseline_gpt4.py \
    --captions data/dev/captions.tsv \
    --ref_dir  data/dev/imgs/ref \
    --gen_dir  data/dev/imgs/generated \
    --output   predictions.tsv \
    --api_key  YOUR_OPENROUTER_KEY

# Evaluate locally
python evaluation/evaluate.py --gold data/dev/gold_human.tsv --pred predictions.tsv
```

## Participation

You may use **any model or pipeline**. Approaches based on vision-language models, LLM-as-a-judge, multimodal embeddings, fine-tuned scorers, or novel combinations are all welcome.

Every participating team is expected to submit a short **system description paper**. See the [submission guidelines]({{ '/submission/' | relative_url }}).

## Submission

1. Produce predictions in the TSV format shown above.
2. Validate with the [format checker](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task2/format_checker):
   ```bash
   python format_checker/check_format.py --pred predictions.tsv --split dev
   ```
3. Evaluate locally with the [scorer](https://github.com/ImageEval2026/ImageEval2026-tasks/tree/main/task1/evaluation):
   ```bash
   python evaluation/evaluate.py --gold data/dev/gold_human.tsv --pred predictions.tsv
   ```
4. Zip as `predictions.zip` and upload to the Codabench leaderboard:
   ```bash
   zip predictions.zip predictions.tsv
   ```

| Phase | Period | Leaderboard |
|---|---|---|
| Development Phase | until July 20, 2026 | [Codabench — 16944](https://www.codabench.org/competitions/16944/) |

**Submission limits:** Development phase — unlimited (10/day max). Test phase — 5 total, 2/day. Best submission counts.

## Questions

See the [FAQ]({{ '/faq/' | relative_url }}) or email [imageeval2026@gmail.com](mailto:imageeval2026@gmail.com). The dataset is released for research use under CC BY-NC 4.0.
