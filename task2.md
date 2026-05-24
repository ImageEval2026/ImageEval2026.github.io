---
title: "Task 2: CRAI-Bench"
layout: content
permalink: /task2/
description: Cultural accuracy evaluation for text-to-image generation.
bodyClass: page-task2
---

# Task 2: CRAI-Bench

## Cultural Accuracy Evaluation for Text-to-Image Generation

CRAI-Bench evaluates whether AI-generated images faithfully represent Qatari and Arab cultural scenes. The task introduces the Cultural Representation Accuracy Index (CRAI), a five-dimensional scoring framework, and is structured into two complementary subtasks.

## Subtask 2A: Cultural Accuracy Evaluation

**Objective:** Given a reference image of a Qatari cultural scene, a culturally grounded English image caption, and an AI-generated image produced from that caption, participants produce CRAI scores in the range [0,1] across five dimensions.

**Dataset:** The dataset consists of reference image, caption, and generated-image triples grounded in Qatari culture across five categories: people and traditional attire; objects and natural elements; architecture and built environment; cultural activities and practices; and historical and cultural context.

**Submission format:** Submit a TSV file with one scored instance per line:

- `id`
- `CRAI_CEA` - Cultural Element Accuracy, 0-1
- `CRAI_CC` - Contextual Coherence, 0-1
- `CRAI_CS` - Cultural Specificity, 0-1
- `CRAI_CI` - Cultural Integrity, 0-1
- `CRAI_HP` - Hallucination Penalty, 0-1
- `CRAI_composite` - weighted composite score, 0-1

**Evaluation:** Systems are ranked by Spearman correlation and mean absolute error against human-annotated gold CRAI scores, both overall and per dimension.

`CRAI = 0.30 CEA + 0.20 CC + 0.20 CS + 0.20 CI - 0.10 HP`

Score bands: 0.85 or higher is highly accurate, 0.70-0.84 is mostly accurate, 0.50-0.69 is moderate, 0.30-0.49 is weak, and below 0.30 is poor or misleading.

## Subtask 2B: Culturally Accurate Caption Generation

**Objective:** Given a reference image of a Qatari cultural scene, participants generate a culturally grounded English image caption designed to maximize the cultural accuracy of a downstream text-to-image model's output.

**Dataset:** Participants receive the same reference images as Subtask 2A, without the associated captions or generated images. The same training, development, and hidden test split structure applies.

**Submission format:** Submit a TSV file with one caption per line:

- `id`
- `caption`

**Evaluation:** Submitted captions are passed through a fixed text-to-image system; the resulting images are scored with CRAI. Systems are ranked by mean CRAI score. Higher is better.
