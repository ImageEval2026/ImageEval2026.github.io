---
title: "Submission Guidelines"
layout: page
permalink: /submission/
description: Paper submission guidelines for ImageEval Shared Task 2026.
bodyClass: page-submission
---

# Paper Submission Guidelines

<div class="submission-intro" markdown="1">
System description papers should explain what your team built, how it was trained and evaluated, and what the results reveal about the task. Keep the paper concise, reproducible, and analysis-focused.
</div>

<div class="submission-facts" markdown="1">
<div markdown="1">
<span>Paper length</span>
<strong>Maximum 4 pages</strong>
<p>References are unlimited.</p>
</div>
<div markdown="1">
<span>Required template</span>
<strong>EMNLP 2026 / ACL style</strong>
<p>LaTeX or Word templates.</p>
</div>
<div markdown="1">
<span>Title format</span>
<strong>Team at ImageEval</strong>
<p><code>&lt;Team Name&gt; at ImageEval Shared Task: &lt;Your Contribution&gt;</code></p>
</div>
</div>

<nav class="submission-jump" aria-label="Submission sections">
  <a href="#key-principles">Key Principles</a>
  <a href="#required-elements">Required Elements</a>
  <a href="#recommended-paper-structure">Paper Structure</a>
  <a href="#formatting">Formatting</a>
  <a href="#final-checklist">Final Checklist</a>
</nav>

<section class="submission-section" markdown="1">
## Key Principles

<div class="submission-grid" markdown="1">
<div markdown="1">
### Replicability

Provide enough implementation detail for another researcher to reproduce the system.
</div>
<div markdown="1">
### Analysis

Emphasize results, error patterns, ablations, and design decisions rather than only rankings.
</div>
<div markdown="1">
### Clarity

Briefly describe the task setup, but do not duplicate the task overview paper.
</div>
</div>
</section>

<section class="submission-section" markdown="1">
## Required Elements

- Cite the task overview paper.
- Follow the EMNLP/ACL templates exactly.
- Use the required title format: `<Team Name> at ImageEval Shared Task: <Your Contribution>`.
- Clearly state which task(s) and track(s) your team participated in.
- Describe external data, tools, APIs, or models used beyond the released task data.
- Distinguish official submitted results from post-submission experiments.

For popular algorithms, citation is usually sufficient. Full mathematical detail is only needed when it is central to your contribution. Move detailed hyperparameters and low-level implementation details to the appendix when space is limited.
</section>

<section class="submission-section" markdown="1">
## Recommended Paper Structure

<details class="submission-item" open markdown="1">
<summary>1. Abstract</summary>

Briefly summarize the task, your approach, and the main results in a few sentences.
</details>

<details class="submission-item" open markdown="1">
<summary>2. Introduction</summary>

- Describe the task and why it matters.
- Mention the language varieties and track(s) covered.
- Cite the task overview paper.
- Summarize your main system strategy.
- Highlight key findings, ranking, and challenges discovered.
- Include a code URL if available.
</details>

<details class="submission-item" markdown="1">
<summary>3. Background</summary>

- Summarize the task setup, including input and output types.
- Describe dataset details such as language, genre, and size.
- State the tracks you participated in.
- Cite related work and explain what is different about your system.
</details>

<details class="submission-item" markdown="1">
<summary>4. System Overview</summary>

- Explain key algorithms and design decisions.
- List resources used beyond the provided training data.
- Describe how your system addressed task-specific challenges.
- Include equations or pseudocode for novel methods.
- Clearly distinguish multiple configurations or submitted runs.
</details>

<details class="submission-item" markdown="1">
<summary>5. Experimental Setup</summary>

- Explain how train, development, and test splits were used.
- Provide preprocessing details and hyperparameters needed for replication.
- List external tools and libraries with versions and URLs.
- Summarize the official evaluation metrics.
- Put low-level details in the appendix if space is limited.
</details>

<details class="submission-item" markdown="1">
<summary>6. Results and Analysis</summary>

- Report official metric performance and ranking.
- Include ablations, comparisons, and design-decision analysis where possible.
- Provide error analysis with representative examples.
- Clearly mark which data split is used for each analysis.
- Distinguish official results from post-submission results.
</details>

<details class="submission-item" markdown="1">
<summary>7. Conclusion</summary>

Summarize the system, limitations, results, and future work.
</details>

<details class="submission-item" markdown="1">
<summary>8. Acknowledgments</summary>

Thank contributors, grants, infrastructure providers, and reviewers where appropriate.
</details>

<details class="submission-item" markdown="1">
<summary>9. Appendix</summary>

Use the appendix for low-level replication details that are useful but not essential to the main paper.
</details>
</section>

<section class="submission-section" markdown="1">
## Formatting

- Use the official EMNLP 2026 / ACL style templates in LaTeX or Word.
- Download templates from [acl-org/acl-style-files](https://github.com/acl-org/acl-style-files).
- Follow the general ACL conference formatting guidelines.
- Do not modify style files or use templates from other conferences.

Submissions with non-conforming paper size, margins, or font size may be rejected without review.
</section>

<section class="submission-section" markdown="1">
## Final Checklist

- The paper is no longer than 4 content pages.
- References are in the correct format.
- The title follows the required ImageEval format.
- The task overview paper is cited.
- All external data and tools are documented.
- Official and post-submission results are clearly separated.
- Code or data URLs are included when available.
</section>
