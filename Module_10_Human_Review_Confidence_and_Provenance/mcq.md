# Module 10 Multiple-Choice Questions

Pick the single best answer. Answers are in `mcq-answers.md`. Do not open it before you answer.

---

## Task statement 5.5

**Q1 [5.5]** A document-extraction pipeline processes invoices, contracts, and handwritten receipts. Its overall accuracy is 97%, measured across all documents together. Handwritten receipts are only 3% of the volume. The team wants to remove human review for the whole pipeline. What should they do first?

A. Remove review, because 97% is above the usual target.
B. Raise the model's confidence threshold for every document type equally.
C. Measure accuracy separately for each document type and field, then decide where review can go.
D. Ask the model to report one confidence score for each whole document.

**Q2 [5.5]** A team sends only low-confidence extractions to human reviewers. Reviewers fix most of them, and the team believes the system is safe. The model is then updated, and it starts making a new kind of mistake while reporting high confidence. Which change would best catch this kind of problem?

A. Each month, humans check a random sample from every document type and confidence band, including high-confidence items.
B. Lower the confidence cutoff so slightly fewer items are reviewed.
C. Ask the model to double-check its own high-confidence answers.
D. Review only the items from the document type with the most volume.

**Q3 [5.5]** The model gives each extracted field a confidence number. On a labeled validation set (documents with known correct answers), extractions with confidence 0.9 are correct 96% of the time for "invoice date" and 82% of the time for "line-item total". What is the best conclusion?

A. Use one global threshold of 0.9, since the model reports the same score for both.
B. The model is broken and should be replaced.
C. Use only document-level confidence, because field-level scores are unreliable.
D. Set review thresholds per field from the measured correctness, with a stricter one for line-item totals.

**Q4 [5.5]** Reviewers can handle only 50 items today, and 120 are flagged. Item type X: the model has low confidence on a field, but the source text is clear. Item type Y: the model has low confidence on a contract end date, and two pages of the contract give different dates. Which should be prioritized?

A. Type X, because a clear source means the reviewer can finish quickly.
B. Type Y, because low confidence plus contradictory sources is the most untrustworthy case.
C. Both equally, since both are flagged.
D. Neither. Let the model pick one of the two dates.

**Q5 [5.5]** A team wants to stop reviewing high-confidence extractions. A per-segment analysis shows that high-confidence extractions from digital PDFs are 99% correct. High-confidence extractions from scanned PDFs are only 85% correct. What is the best decision?

A. Keep review for all high-confidence extractions, because one segment is weak.
B. Remove review for all segments, since the average is above 95%.
C. Remove review for digital PDFs and keep it for scanned PDFs.
D. Remove review for scanned PDFs, because they are the harder ones and reviewers waste time on them.

---

## Task statement 5.6

**Q1 [5.6]** Three research subagents each return a paragraph of findings. The synthesis agent compresses them into one summary. Two sources gave different figures for the same statistic. The final report says "estimates fall in this range" and no reader can tell which source gave which number. What is the best fix?

A. Ask the synthesis agent to write longer summaries.
B. Have subagents return structured claim-source mappings (claim, source, excerpt), and have synthesis keep them.
C. Tell the synthesis agent to use the highest figure.
D. Add a final step that asks the model to guess the sources from memory.

**Q2 [5.6]** A document-analysis subagent finds that Source A says a market is worth $4.2B and Source B says $5.1B. Both sources are credible and both describe the same year. What should the subagent output?

A. Only the larger figure, because it is more complete.
B. The average of the two figures.
C. Only the figure from the first source it read.
D. Both figures, each with its source, marked as conflicting, for the coordinator to resolve.

**Q3 [5.6]** One report, published in 2023, says a company has 500 employees. Another report, published in 2026, says 1,200. The synthesis agent flags this as a contradiction between two sources. What would have prevented the false contradiction?

A. Requiring each subagent to include the publication or collection date with each figure.
B. Requiring subagents to return shorter outputs.
C. Removing the older source before synthesis.
D. Asking the model to always favor the larger number.

**Q4 [5.6]** A synthesis report mixes findings backed by three independent sources with a finding backed by one weaker source. All of it is written in the same confident tone. Which report design best fixes this?

A. Delete the single-source finding.
B. Put the strongest findings first and say nothing about their support.
C. Use separate sections for well-established findings and contested or single-source findings, keeping each source's own context.
D. Add the word "likely" to every sentence.

**Q5 [5.6]** A synthesis report must show quarterly revenue from several sources, a short market narrative, and a list of technical compliance requirements. Which rendering is best?

A. Write everything as paragraphs.
B. Write everything as bullet points.
C. Put everything in one large table.
D. A comparison table for revenue, prose for the narrative, and a list for the compliance requirements.
