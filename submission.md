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
<p>Unlimited pages for references and appendix.</p>
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
- Use the required title format: `<Team Name> at ImageEval 2026 Shared Tasks: <Your Contribution>`.
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

### Example papers:

<details class="submission-item" markdown="1">
<summary>Example papers</summary>
- [https://aclanthology.org/2025.semeval-1.2.pdf](https://aclanthology.org/2025.semeval-1.2.pdf)
- [https://aclanthology.org/2024.arabicnlp-1.51.pdf](https://aclanthology.org/2024.arabicnlp-1.51.pdf)
</details>

</section>

<section class="submission-section" markdown="1">

## Formatting

- Use the official EMNLP 2026 / ACL style templates in LaTeX.
  - **ACL style-files repository:** [github.com/acl-org/acl-style-files](https://github.com/acl-org/acl-style-files)
  - **Overleaf template:** [Association for Computational Linguistics (ACL) conference template](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj)
- Authors should follow the [general ACL formatting requirements](https://acl-org.github.io/ACLPUB/formatting.html).
- Do not modify style files or use templates from other conferences.

Submissions with non-conforming paper size, margins, or font size may be rejected without review.
</section>

<!-- <section class="submission-section" markdown="1">

## Final Checklist

- The paper is no longer than 4 content pages.
- References are in the correct format.
- The title follows the required ImageEval format.
- The task overview paper is cited.
- All external data and tools are documented.
- Official and post-submission results are clearly separated.
- Code or data URLs are included when available.
</section> -->

<section class="submission-section" markdown="1">

## Author Information and Review

ImageEval system description papers are **not submitted anonymously**. Authors should include their names, affiliations, and contact information in the submitted paper.

The papers will be reviewed to ensure that they:

- provide an adequate description of the submitted system;
- report the experimental setup and results clearly;
- follow the required paper format;
- include appropriate analysis or discussion;
- cite the ImageEval overview and dataset papers; and
- meet the basic standards required for inclusion in the proceedings.

A high leaderboard rank is not required for paper acceptance. The quality and clarity of the system description, analysis, and scientific discussion will be considered during review.

</section>

<section class="submission-section" markdown="1">
## Paper Submission

Papers must be submitted through the official ArabicNLP 2026 shared-task paper submission portal.

**Submission portal:** **TBA**

Before submitting, please confirm that:

- the paper uses the official ACL template;
- the paper contains no more than four pages of main content;
- the title follows the required naming format;
- all authors and affiliations are included;
- all external data and resources are disclosed;
- the official ArGuard papers are cited; and
- the submitted PDF opens and displays correctly.

</section>

<section class="submission-section" markdown="1">
## ACL PubCheck for Camera-ready

All camera-ready papers must be checked using **ACL PubCheck** before final submission. ACL PubCheck automatically identifies common formatting problems involving margins, fonts, page dimensions, spacing, and other ACL publication requirements. Authors are also encouraged to run PubCheck before the initial paper submission.


### PubCheck Resources

- **GitHub repository:** [github.com/acl-org/aclpubcheck](https://github.com/acl-org/aclpubcheck)
- **Google Colab:** [Run ACL PubCheck in Google Colab](https://colab.research.google.com/github/acl-org/aclpubcheck/blob/main/aclpubcheck_online.ipynb)
- **Hugging Face interface:** [ACL PubCheck on Hugging Face Spaces](https://huggingface.co/spaces/teelinsan/aclpubcheck)

Please address all relevant PubCheck errors before submitting the camera-ready paper. Warnings should also be reviewed carefully.

</section>

<section class="submission-section" markdown="1">
## Required Citations

System description papers must cite:

1. the ImageEval shared-task overview paper; and
2. the relevant ImageEval dataset papers.

Please find the BibTeX entries for the overview and dataset papers below.


```bibtex
@inproceedings{imageeval-2026,
  title     = "{ImageEval 2026}: Culturally Grounded {A}rabic
               Multimodal Evaluation",
  author    = {Abdaljalil, Samir and
               Bhatti, Hunzalah Hassan and
               Bashiti, Ahlam and
               Amir, Farina and
               Hasan, Md Arid and
               Mousi, Basel and
               Durrani, Nadir and
               Dalvi, Fahim and
               Sheikh Ali, Zien and
               Serpedin, Erchin and
               Kurban, Hasan and
               Jarrar, Mustafa and
               Chowdhury, Shammur Absar and
               Alam, Firoj},
  booktitle = {Proceedings of the Fourth Arabic Natural Language
               Processing Conference: Shared Tasks},
  month     = oct,
  year      = {2026},
  address   = {Budapest, Hungary},
  publisher = {Association for Computational Linguistics}
}

@article{alam2025everydaymmqa,
  title   = "{OASIS}: A Multilingual and Multimodal Dataset for
             Culturally Grounded Spoken Visual {QA}",
  author  = {Alam, Firoj and
             Shahroor, Ali Ezzat and
             Hasan, Md. Arid and
             Ali, Zien Sheikh and
             Bhatti, Hunzalah Hassan and
             Kmainasi, Mohamed Bayan and
             Chowdhury, Shammur Absar and
             Mousi, Basel and
             Dalvi, Fahim and
             Durrani, Nadir and
             Milic-Frayling, Natasa},
  journal = {arXiv preprint arXiv:2510.06371},
  year    = {2025}
}

@inproceedings{mousi-etal-2026-correct,
  title     = {Once Correct, Still Wrong: Counterfactual Hallucination
               in Multilingual Vision-Language Models},
  author    = {Mousi, Basel and
               Dalvi, Fahim and
               Chowdhury, Shammur Absar and
               Alam, Firoj and
               Durrani, Nadir},
  editor    = {Liakata, Maria and
               Moreira, Viviane P. and
               Zhang, Jiajun and
               Jurgens, David},
  booktitle = {Findings of the {A}ssociation for {C}omputational
               {L}inguistics: {ACL} 2026},
  month     = jul,
  year      = {2026},
  address   = {San Diego, California, United States},
  publisher = {Association for Computational Linguistics},
  url       = {https://aclanthology.org/2026.findings-acl.234/},
  doi       = {10.18653/v1/2026.findings-acl.234},
  pages     = {4763--4788},
  isbn      = {979-8-89176-395-1}
}

@inproceedings{mousi2026said,
  title     = {Said Aloud, Read Different: Cross-Modal Instability
               in Multimodal Models},
  author    = {Mousi, Basel and
               Dalvi, Fahim and
               Chowdhury, Shammur and
               Alam, Firoj and
               Durrani, Nadir},
  booktitle = {Proceedings of Interspeech 2026},
  year      = {2026},
  address   = {Sydney, Australia},
  note      = {Accepted}
}
```

</section>

<section class="submission-section" markdown="1">
## Information Required for the Overview Paper

The ImageEval 2026 organizers will publish an overview paper summarizing the shared task, participating teams, submitted methods, and official results.

Each participating team must provide:

- the team name;
- participating subtasks;
- a short description of the system;
- models and external resources used;
- the official submission results;
- authors and affiliations; and
- the BibTeX entry for the system description paper.

Please submit this information using the following form:

[ImageEval 2026 overview paper information form](https://forms.gle/45QfNwf1Y17U6EAX6)

#### System Paper BibTeX Template

Please replace the placeholders with your paper information.

```bibtex
@inproceedings{imageeval-2026-team-name,
    author = {Last-Name, First-Name and
              Last-Name, First-Name},
    title = "{Team Name} at {ImageEval 2026 Shared Tasks}:
             Title of the Paper",
    booktitle = {Proceedings of the Fourth Arabic Natural Language
                 Processing Conference: Shared Tasks},
    address = {Budapest, Hungary},
    month = oct,
    year = {2026},
    publisher = {Association for Computational Linguistics}
}
```

Use a short and unique citation key based on your team name. Please ensure that the author names and paper title exactly match the submitted paper.
</section>

<section class="submission-section" markdown="1">

## Leaderboards

**Task 1: AynVQA**

- **Spoken VQA (1a)	English:** [Codabench 17049/](https://www.codabench.org/competitions/17049/)
- **Spoken VQA (1a)	MSA:** [Codabench 17048/](https://www.codabench.org/competitions/17048/)
- **Hallucination (1b)	English:** [Codabench 17051/](https://www.codabench.org/competitions/17051/)
- **Hallucination (1b)	MSA:** [Codabench 17050/](https://www.codabench.org/competitions/17050/)
<br/>

**Task 2: Cultural Representation Accuracy Index (CRAI)**

- **CRAI-Bench:** [Codabench competition](https://www.codabench.org/competitions/16944/)


<section class="submission-section" markdown="1">
## Test Sets and Gold Labels

TBA
<!-- Gold-labelled test sets are available to support result verification and detailed error analysis. -->

<!-- **Task A gold-labelled test set**

<span class="status-placeholder">Task A test-set link to be announced</span>

**Task B gold-labelled test set**

<span class="status-placeholder">Task B test-set link to be announced</span>

Participants must continue to follow the applicable dataset licences and terms of use when accessing, analysing, or redistributing task data. -->
</section>

<section class="submission-section" markdown="1">
## Call for Reviewers

Researchers who have previously published at *ACL conferences and are interested in serving as reviewers for the shared-task proceedings are invited to complete the following form: [https://forms.gle/Deg6QdwsuF6aFX2X9](https://forms.gle/Deg6QdwsuF6aFX2X9)

</section>
