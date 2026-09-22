# Module 10 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 5.5 (Human Review and Confidence Calibration)

**Q1.** An extraction pipeline reports 97% overall accuracy. Is it safe to reduce
human review across the board? What must you check first?

**Q2.** Why does a QA process that only reviews low-confidence extractions miss
important failure modes?

**Q3.** A field-level confidence score of 0.9 means correct 96% of the time for
"invoice date" but only 82% of the time for "line-item total." What does this
tell you about using raw model confidence directly as a review threshold?

**Q4.** Given limited reviewer capacity, which of these two extractions should be
prioritized for human review: (a) low confidence on an unambiguous field, or (b)
low confidence on a field where two source pages state contradictory values?
Why?

---

## Quiz — Lesson 5.6 (Information Provenance and Multi-Source Synthesis)

**Q1.** Two sources report slightly different figures for the same statistic.
After an unstructured summarization pass, the report says "reports suggest
values in this range" with no way to tell which source said what. What went
wrong, and what's the structural fix?

**Q2.** Source A reports a market size of $4.2B and Source B reports $5.1B for
what looks like the same fact. What should the document-analysis output do,
and what should it NOT do?

**Q3.** Source A (2023) reports headcount as 500; Source B (2026) reports 1,200.
Without any additional metadata, how might this be misread, and what field
prevents that misreading?

**Q4.** How should a synthesis report structurally distinguish a finding
supported by three independent sources from a finding supported by only one
lower-confidence source?

**Q5.** A synthesis report includes quarterly revenue figures, a market
narrative, and a list of technical compliance requirements. Should all three be
rendered as prose? Why or why not?
