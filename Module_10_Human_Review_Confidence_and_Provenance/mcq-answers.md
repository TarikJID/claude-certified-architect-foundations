# Module 10 MCQ Answers

ANSWERS. Do not reveal before the learner has attempted the question.

---

## Task statement 5.5

**Q1 [5.5]** Correct: C
- Why: One aggregate number can hide a weak segment, so check per document type and field first.
- A wrong: The 97% average can hide receipts doing badly.
- B wrong: An equal threshold for all types ignores that errors cluster in some segments.
- D wrong: Document-level confidence is coarser. Errors happen at field level.
- Tests: 5.5-K1, 5.5-S2, 5.5-K4

**Q2 [5.5]** Correct: A
- Why: A random sample from every segment, including high-confidence, can find confident-but-wrong failures.
- B wrong: Reviewing fewer items finds fewer errors.
- C wrong: The model's own check is not independent human verification.
- D wrong: Volume alone does not tell you where errors are, and it skips confidence bands.
- Tests: 5.5-K2, 5.5-S1

**Q3 [5.5]** Correct: D
- Why: Raw confidence is not calibrated. Per-field thresholds from validation data fix this.
- A wrong: The same score means different accuracy per field.
- B wrong: The scores are usable once calibrated. Nothing says the model is broken.
- C wrong: Field-level scores are more useful, not less, once calibrated.
- Tests: 5.5-K3, 5.5-S3

**Q4 [5.5]** Correct: B
- Why: Low confidence and contradictory sources are two reasons to distrust it, so it needs the human most.
- A wrong: Speed of review is not the priority rule. Risk is.
- C wrong: Limited capacity requires prioritising.
- D wrong: Silently picking a value hides the conflict.
- Tests: 5.5-S4

**Q5 [5.5]** Correct: C
- Why: Automate only the segments shown to be accurate. Keep review where not verified.
- A wrong: It throws away the saving for the segment that checks out.
- B wrong: The average hides the weak scanned segment.
- D wrong: Scanned is the weak segment, so it needs review most.
- Tests: 5.5-K4, 5.5-K1, 5.5-S2

---

## Task statement 5.6

**Q1 [5.6]** Correct: B
- Why: Summarising merges claims and loses the source link. Structured claim-source mappings, kept by synthesis, preserve it (citations feature does this).
- A wrong: Length does not restore lost attribution.
- C wrong: Picking the highest figure discards information and ignores sources.
- D wrong: Guessing sources invents provenance.
- Tests: 5.6-K1, 5.6-K2, 5.6-S1

**Q2 [5.6]** Correct: D
- Why: Keep both values with sources, flag the conflict, let the coordinator or reader reconcile.
- A wrong: Silently picking one discards information.
- B wrong: An average is a number neither source reported.
- C wrong: Order read is arbitrary.
- Tests: 5.6-K3, 5.6-S3

**Q3 [5.6]** Correct: A
- Why: Dates show the gap is change over time, not disagreement.
- B wrong: Length does not help interpretation.
- C wrong: Dropping a source loses real information.
- D wrong: Favouring the larger number is arbitrary and ignores time.
- Tests: 5.6-K4, 5.6-S4

**Q4 [5.6]** Correct: C
- Why: Separate sections show different confidence levels and keep each source's context.
- A wrong: Single-source findings may still be useful if labeled.
- B wrong: Hiding the support level is the problem.
- D wrong: Blanket hedging does not tell the reader which claims are solid.
- Tests: 5.6-S2

**Q5 [5.6]** Correct: D
- Why: Match the format to the content type: table, prose, list.
- A wrong: Prose loses table alignment.
- B wrong: Bullets flatten numbers and narrative.
- C wrong: A table suits numbers but not narrative or requirements.
- Tests: 5.6-S5
