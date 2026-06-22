---
title: "FAQ"
layout: page
permalink: /faq/
description: Frequently asked questions for ImageEval Shared Task 2026.
bodyClass: page-faq
---

# Frequently Asked Questions

<div class="faq-intro" markdown="1">
This page groups common questions about participation, evaluation, system papers, review expectations, and support for ImageEval 2026.
</div>

<nav class="faq-jump" aria-label="FAQ sections">
  <a href="#participation">Participation</a>
  <a href="#evaluation-and-data">Evaluation and Data</a>
  <a href="#paper-requirements">Paper Requirements</a>
  <a href="#review-and-publication">Review and Publication</a>
  <a href="#support">Support</a>
</nav>

<section class="faq-section" id="participation" markdown="1">
## Participation

<details class="faq-item" open markdown="1">
<summary>Who can participate in ImageEval 2026?</summary>

Anyone can participate, either independently or as part of a team.
</details>

<details class="faq-item" markdown="1">
<summary>Is there a fee to participate?</summary>

Participation in the shared task is free. At least one team member should register for the conference if the paper is accepted and presented.
</details>

<details class="faq-item" markdown="1">
<summary>How can I sign up?</summary>

Sign up on the relevant Codabench competition and get the data from the [Hugging Face dataset](https://huggingface.co/datasets/QCRI/AynVQA-ArabicNLP26). Join our [Slack channel](https://join.slack.com/t/mm-eval/shared_invite/zt-41j09ml4j-WMn0NzhqAgT9ZK6e1L8eBA) for announcements, deadlines, and task-specific updates.
</details>

<details class="faq-item" markdown="1">
<summary>Can I participate in multiple ImageEval tasks?</summary>

Yes. Teams may participate in Task 1, Task 2, or both.
</details>

<details class="faq-item" markdown="1">
<summary>Can I participate in multiple teams for the same task?</summary>

This depends on the task policy. If this is relevant to your team, contact the organizers before submitting runs.
</details>

<details class="faq-item" markdown="1">
<summary>Which models and methods can I use?</summary>

For Task 1, any model and any pipeline are welcome, cascaded or end to end, and both open and closed models are allowed (we especially encourage open models for reproducibility and low-resource settings). Please take part in good faith: run each track in its own language from end to end rather than reusing another track's predictions. See the [Task 1 page]({{ '/task1/' | relative_url }}) for the full participation notes.
</details>
</section>

<section class="faq-section" id="evaluation-and-data" markdown="1">
## Evaluation and Data

<details class="faq-item" markdown="1">
<summary>What does the evaluation period mean?</summary>

The evaluation period is the official competition window. Organizers release evaluation data at the beginning of this period, and system outputs are due before the deadline.
</details>

<details class="faq-item" markdown="1">
<summary>How many runs can a team submit?</summary>

Submission limits are task-specific. Check the task page and platform instructions for the final limits.
</details>

<details class="faq-item" markdown="1">
<summary>Where can I find the datasets?</summary>

Task datasets are distributed by the task organizers. Check the task pages and official announcements for release details.
</details>
</section>

<section class="faq-section" id="paper-requirements" markdown="1">
## Paper Requirements

<details class="faq-item" open markdown="1">
<summary>Do I need to write a system paper?</summary>

Yes. Teams that participate and request task data are expected to submit a system description paper.
</details>

<details class="faq-item" markdown="1">
<summary>What happens if a participating team does not submit a paper?</summary>

Requesting the data commits the team to submitting a paper. Abandoning the task after receiving data may affect future participation.
</details>

<details class="faq-item" markdown="1">
<summary>What is the paper format?</summary>

System papers should follow the ArabicNLP 2026 short-paper format. Papers must use the official EMNLP/ACL LaTeX or Word templates and may be up to 4 pages, excluding unlimited references. Templates are available from [acl-org/acl-style-files](https://github.com/acl-org/acl-style-files).
</details>

<details class="faq-item" markdown="1">
<summary>How should the paper title be formatted?</summary>

Use this format:

`<Team Name> at <Task Name>: <Your Contribution>`

Example:

`Scholarly at ImageEval Shared Task: LLMs for Arabic Visual Question Answering`
</details>

<details class="faq-item" markdown="1">
<summary>Must I cite the task overview paper?</summary>

Yes. Each team is required to cite the shared task overview paper in its system paper.
</details>

<details class="faq-item" markdown="1">
<summary>What happens if I exceed the page limit?</summary>

Submissions that exceed length requirements may be desk rejected.
</details>
</section>

<section class="faq-section" id="review-and-publication" markdown="1">
## Review and Publication

<details class="faq-item" markdown="1">
<summary>Are papers anonymous?</summary>

No. Shared task papers, including system papers and overview papers, are not anonymous.
</details>

<details class="faq-item" markdown="1">
<summary>Do I need an OpenReview account?</summary>

Yes. Participants and organizers are required to create an OpenReview account.
</details>

<details class="faq-item" markdown="1">
<summary>Will I need to review other papers?</summary>

Yes. Shared task teams are expected to serve as reviewers, and reviews will be checked by a member of the organizing team.
</details>

<details class="faq-item" markdown="1">
<summary>Must accepted papers be presented at the conference?</summary>

Yes. Accepted papers must be presented at the conference, either in person or virtually. Papers without at least one presenting author registered by the required deadline may be rejected.
</details>

<details class="faq-item" markdown="1">
<summary>Can I post my paper on arXiv?</summary>

Yes. Authors may submit papers to arXiv at any time. Since shared task papers are not anonymous, this does not interfere with the review process.
</details>

<details class="faq-item" markdown="1">
<summary>Can I make changes for the camera-ready version?</summary>

No additions, revisions, or name changes are allowed after the review period for the camera-ready version unless explicitly permitted by the organizers.
</details>
</section>

<section class="faq-section" id="support" markdown="1">
## Support

<details class="faq-item" markdown="1">
<summary>What if my research raises ethical concerns?</summary>

Discuss ethical considerations, including potential misuse, clearly in the system paper.
</details>

<details class="faq-item" markdown="1">
<summary>Should I release my code?</summary>

Code and data release is highly encouraged. Include the URL in the system paper when possible to support reproducibility.
</details>

<details class="faq-item" open markdown="1">
<summary>My question is not answered here. Who should I contact?</summary>

- For task-specific questions, consult the task page and contact the task organizers.
- For workshop logistics, contact the shared task organizers.
- For OpenReview technical issues, contact OpenReview support.
</details>
</section>
