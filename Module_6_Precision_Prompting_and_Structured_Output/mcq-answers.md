# Module 6 MCQ Answers (tutor only: never reveal before the learner has attempted the question)

## Task 4.1

### Q4.1-1
Correct: C. Tests: 4.1-K1, 4.1-S1.
- Why: it is an explicit, checkable criterion.
- A wrong: confidence wording does not reliably raise precision.
- B wrong: reporting more increases false positives.
- D wrong: self-scored confidence is still confidence-based filtering.

### Q4.1-2
Correct: D. Tests: 4.1-S2, 4.1-K3.
- Why: disabling the noisy category protects trust while its prompt is fixed.
- A wrong: a disclaimer leaves the noise and the lost trust.
- B wrong: a confidence cutoff is not a reliable fix and hits accurate categories too.
- C wrong: this throws away accurate categories.

### Q4.1-3
Correct: A. Tests: 4.1-S3.
- Why: a concrete example per level anchors classification.
- B wrong: an instruction to be consistent defines nothing.
- C wrong: more named levels add more ambiguity.
- D wrong: taking the higher severity does not make classification consistent.

### Q4.1-4
Correct: B. Tests: 4.1-S1, 4.1-K2.
- Why: it names categories to report and to skip.
- A wrong: confidence-based wording.
- C wrong: reports everything and relies on self-scored confidence.
- D wrong: "be conservative" is a vague general instruction.

### Q4.1-5
Correct: C. Tests: 4.1-K3.
- Why: a high false positive category undermines confidence in accurate categories.
- A wrong: security findings are 95% correct, so nothing suggests the prompt is broken.
- B wrong: not supported; the cause is lost trust.
- D wrong: model confidence is not the issue and is not a reliable guide anyway.

---

## Task 4.2

### Q4.2-1
Correct: B. Tests: 4.2-K1, 4.2-S2.
- Why: worked examples show the exact format and fix inconsistency that prose did not.
- A wrong: longer prose already failed.
- C wrong: emphasis is not a technique that shows the format.
- D wrong: confidence filtering does not fix format.

### Q4.2-2
Correct: D. Tests: 4.2-K2, 4.2-S1.
- Why: targeted examples with reasoning teach the deciding signal.
- A wrong: a vague instruction adds no signal.
- B wrong: obvious cases do not teach the ambiguous ones.
- C wrong: removing a tool loses capability and does not teach judgment.

### Q4.2-3
Correct: A. Tests: 4.2-S3, 4.2-K3.
- Why: contrast examples teach the boundary so judgment generalizes to new patterns.
- B wrong: a fixed list only matches known cases.
- C wrong: bug-only examples cause more false positives.
- D wrong: this would also miss real bugs of that kind.

### Q4.2-4
Correct: C. Tests: 4.2-K4.
- Why: examples of correct handling of informal measurements prevent fabrication.
- A wrong: required fields push the model to invent values.
- B wrong: a bare instruction shows nothing about how to handle the hard case.
- D wrong: retrying toward precision encourages inventing values.

### Q4.2-5
Correct: C. Tests: 4.2-S4, 4.2-S5.
- Why: examples of both layouts fix the empty extraction.
- A wrong: required fields do not teach where the data is.
- B wrong: a bare retry gives no new information.
- D wrong: this does not extract citations.

---

## Task 4.3

### Q4.3-1
Correct: A. Tests: 4.3-K1, 4.3-S1.
- Why: tool use with a JSON schema removes JSON syntax errors.
- B wrong: a prompt reminder is not enforced.
- C wrong: patching text is fragile.
- D wrong: asking twice does not guarantee valid format.

### Q4.3-2
Correct: C. Tests: 4.3-K2, 4.3-S2.
- Why: any forces a tool call and lets the model choose which schema fits.
- A wrong: auto may return text.
- B wrong: forcing one tool breaks receipts and purchase orders.
- D wrong: none prevents tool calls.

### Q4.3-3
Correct: D. Tests: 4.3-S3, 4.3-K2.
- Why: a forced named tool guarantees the step runs first; auto then follows.
- A wrong: auto does not guarantee any tool is called.
- B wrong: any does not control which tool is called.
- C wrong: a prompt instruction is not a guarantee.

### Q4.3-4
Correct: B. Tests: 4.3-K3.
- Why: schema checks syntax and types, not whether values agree.
- A wrong: tool use worked; the error is semantic.
- C wrong: the field already has a valid number, so required adds nothing.
- D wrong: tool_choice does not affect arithmetic consistency.

### Q4.3-5
Correct: D. Tests: 4.3-S4, 4.3-K4.
- Why: optional and nullable fields let the model return null instead of fabricating.
- A wrong: "other" is for categories, not missing values.
- B wrong: examples of invented values teach fabrication.
- C wrong: forcing the tool does not change the required field.
