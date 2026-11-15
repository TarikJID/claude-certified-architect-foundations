# Module 10 MCQ Answers

ANSWERS. Do not reveal before the learner has attempted the question.

---

## Task statement 5.5

**Q1 [5.5]** Correct: C
- Why: One overall number can hide a weak document type, so measure each type and field before deciding.
- A wrong: The 97% can hide receipts doing badly, because they are only 3% of documents.
- B wrong: Errors gather in some document types, so the same change for all types misses the real problem.
- D wrong: One score per document is less precise. Mistakes happen in individual fields.
- Tests: 5.5-K1, 5.5-S2, 5.5-K4

**Q2 [5.5]** Correct: A
- Why: Only a random check that includes high-confidence fields can catch mistakes Claude is sure about.
- B wrong: Sending fewer fields to humans finds fewer mistakes, and still never checks high-confidence ones.
- C wrong: Claude checking itself is not an independent human check.
- D wrong: The biggest document type is not where the new mistakes are, and high-confidence fields are still skipped.
- Tests: 5.5-K2, 5.5-S1

**Q3 [5.5]** Correct: D
- Why: Claude's raw score does not mean the same thing for every field, so set each field's cutoff from the tested results.
- A wrong: One cutoff ignores that 0.9 means 96% for dates but only 82% for totals.
- B wrong: The scores are still useful once checked against known answers. Nothing shows the model is broken.
- C wrong: Field scores are more useful than one score per document, once they are checked.
- Tests: 5.5-K3, 5.5-S3

**Q4 [5.5]** Correct: B
- Why: Two warning signs at once (Claude unsure and the contract contradicting itself) make Y the least trustworthy.
- A wrong: Order by risk, not by how fast the check is.
- C wrong: With time for only 50 of 120, some must go first.
- D wrong: Letting Claude pick a date hides the contradiction.
- Tests: 5.5-S4

**Q5 [5.5]** Correct: C
- Why: Stop review only where a group has been shown accurate. Keep it where it has not.
- A wrong: It keeps review on digital PDFs, which have already been shown to be accurate.
- B wrong: An average hides the weak scanned group.
- D wrong: Scanned PDFs are the weak group, so they need review most.
- Tests: 5.5-K4, 5.5-K1, 5.5-S2

---

## Task statement 5.6

**Q1 [5.6]** Correct: B
- Why: Combining into prose loses which source said what. Keeping claim + source + excerpt pairs preserves it, and Claude's citations feature (which tags each sentence with the exact document text it came from) does this.
- A wrong: A longer summary still does not say which source said what.
- C wrong: Taking the highest number throws away the other source and still loses who said what.
- D wrong: Guessing sources makes them up.
- Tests: 5.6-K1, 5.6-K2, 5.6-S1

**Q2 [5.6]** Correct: D
- Why: Keep both numbers with their sources, mark the conflict, and let the coordinator decide.
- A wrong: Quietly choosing one throws away real information.
- B wrong: An average is a number neither source reported.
- C wrong: Which source was read first is not a reason to trust it.
- Tests: 5.6-K3, 5.6-S3

**Q3 [5.6]** Correct: A
- Why: With dates, the gap reads as growth over three years, not as two sources disagreeing.
- B wrong: A shorter output still has no dates.
- C wrong: Deleting a true source throws away real information.
- D wrong: Preferring the larger number is arbitrary and still ignores the dates.
- Tests: 5.6-K4, 5.6-S4

**Q4 [5.6]** Correct: C
- Why: Separate sections show the reader which findings are solid and which are doubtful, with each source's context kept.
- A wrong: A single-source finding can still be useful if it is labeled as such.
- B wrong: Hiding how well each finding is supported is the problem itself.
- D wrong: Putting "likely" everywhere still does not show which findings are solid.
- Tests: 5.6-S2

**Q5 [5.6]** Correct: D
- Why: Match each kind of content to its best format: table, paragraphs, list.
- A wrong: Paragraphs lose the rows and columns that make numbers comparable.
- B wrong: Bullets break the story apart and lose the columns of numbers.
- C wrong: A table suits numbers but not a story or a list of rules.
- Tests: 5.6-S5
