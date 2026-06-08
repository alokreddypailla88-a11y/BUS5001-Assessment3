# Q4 NotebookLM Evaluation Experiment Log

## Scenario

A university innovation team is evaluating whether NotebookLM can support students, lecturers and researchers in coursework and research. The simulated academic scenario focuses on ESG reporting, sustainability governance and responsible AI use in higher education.

## Sources Uploaded

Three sources were uploaded into NotebookLM:

1. TEQSA assessment reform source on artificial intelligence.
2. A general AI education source.
3. A generative AI education article.

## Screenshot Index

| Figure | Description |
|---|---|
| Figure 44 | NotebookLM notebook with uploaded sources. |
| Figure 45 | Five-point summary generated from sources. |
| Figure 46 | Source-cited governance risk response. |
| Figure 47 | NotebookLM-generated university briefing outline. |
| Figure 48 | Comparison output showing source limitation. |
| Figure 49 | Revision questions generated from uploaded sources. |

## Test 1: Notebook Setup

**Prompt used:** No prompt. Notebook setup only.

**Observation:** The notebook was created under the topic “ESG Reporting and Sustainability Governance Evaluation.” Three sources were visible in the source panel. This confirms that NotebookLM was being used as a source-grounded assistant rather than a general chatbot.

**Screenshot evidence:** Figure 44.

## Test 2: Source Summary

**Prompt used:**

```text
Summarise the uploaded sources into five key points about ESG reporting and sustainability governance.
```

**Output summary:** NotebookLM generated a five-point response covering institutional reporting and accountability, environmental sustainability planning, governance of emerging technologies, social responsibility and compliance monitoring.

**Accuracy and relevance:** The output was relevant to the uploaded source set, although the sources focused more strongly on education regulation and AI governance than traditional ESG reporting. This means the response was useful but shaped by the available source mix.

**Usefulness:** Helpful for students beginning an assignment because it converts several readings into a manageable overview.

**Screenshot evidence:** Figure 45.

## Test 3: Source-Based Question Answering

**Prompt used:**

```text
What are the main governance risks in ESG reporting according to the uploaded sources?
```

**Output summary:** NotebookLM identified risks such as integrity and technological risks from AI, academic misconduct, safety and social responsibility risks, cybersecurity and data governance, and transparency failures.

**Accuracy and relevance:** The answer was relevant because it drew from the uploaded sources and included citation numbers. The citation markers allowed verification of whether the claim was connected to a source.

**Usefulness:** Strong for academic workflows because it helps students find source-grounded ideas and supports evidence checking.

**Screenshot evidence:** Figure 46.

## Test 4: Briefing Outline Generation

**Prompt used:**

```text
Create a university briefing outline on ESG reporting governance using only the uploaded sources.
```

**Output summary:** NotebookLM produced a briefing structure with sections on governance and accountability, mandatory reporting instruments, transparency, risk-based oversight and environmental governance.

**Accuracy and relevance:** The output was useful as an outline, but it should not be copied directly into coursework without human review. It helped structure ideas but did not replace independent analysis.

**Usefulness:** Useful for students preparing an assignment plan and for lecturers preparing discussion material.

**Screenshot evidence:** Figure 47.

## Test 5: Source Comparison

**Prompt used:**

```text
Compare the sustainability policy document with the lecture notes. Identify similarities, differences and any gaps.
```

**Output summary:** NotebookLM stated that a direct comparison could not be fully performed because the sources did not contain documents explicitly titled as such. It then used available proxy sources to identify similarities and gaps.

**Accuracy and relevance:** This was the most important limitation test. NotebookLM correctly recognised that the exact requested documents were not present. However, it still attempted a proxy comparison. This is useful but creates interpretation risk because a student might mistake the proxy comparison for a direct comparison.

**Hallucination risk:** The tool did not completely fabricate the missing documents, but it partially reframed the task using available sources. This shows that even source-grounded AI requires careful review.

**Screenshot evidence:** Figure 48.

## Test 6: Revision Questions

**Prompt used:**

```text
Generate five revision questions and answers based on the uploaded ESG sources.
```

**Output summary:** NotebookLM generated revision questions on environmental governance, technological transparency, social responsibility and risk management.

**Accuracy and relevance:** The questions were relevant to the source set and useful for exam preparation or tutorial discussion.

**Usefulness:** Helpful for students who need active recall practice and for lecturers designing class discussion prompts.

**Screenshot evidence:** Figure 49.

## Critical Analysis

### Accuracy and Relevance

NotebookLM was most accurate when the prompt matched the uploaded sources. The summary and Q&A outputs were relevant and included citation markers. However, relevance was constrained by the uploaded sources. Since the source set focused heavily on AI in education and governance, the ESG reporting outputs emphasised accountability, integrity and responsible AI rather than broader environmental metrics.

### Evidence Quality

NotebookLM’s citation markers improved evidence quality because the user could check the source behind each claim. However, citation presence does not guarantee that every interpretation is correct. Each claim still needs human verification.

### Usefulness in Academic Workflows

NotebookLM was useful for:

- summarising long readings,
- generating assignment outlines,
- answering questions from uploaded sources,
- comparing documents,
- producing revision questions,
- supporting lecturers in preparing tutorial activities,
- helping researchers identify early themes.

### Limitations and Risks

The comparison test showed a clear limitation. When the exact source types were not present, NotebookLM acknowledged the gap but still created a proxy comparison. This could mislead students if they do not read the caveat carefully.

Bias is also possible because NotebookLM only reflects the uploaded materials. If the source set is narrow, the output will also be narrow. A student who uploads only policy or institutional sources may receive a positive governance-focused view and miss critical perspectives.

Over-reliance is another concern. Students may treat NotebookLM summaries as a substitute for reading. Lecturers should therefore require citation checking, reflection and source critique in assessment tasks.

## Practical Adoption Recommendation

NotebookLM is suitable for a controlled university pilot. It should be adopted with clear rules:

- Students must verify citations.
- Students must disclose AI use where required.
- Confidential or sensitive documents should not be uploaded without approval.
- AI outputs should support learning, not replace independent analysis.
- Lecturers should design assessments that require reflection and source evaluation.
- Researchers should use NotebookLM for early-stage organisation, not final evidence.

