# Module 7 Fast MCQ Answers (4.4, 4.5, 4.6)

TUTOR: answers. Never show before the learner has attempted the question.

---

## 4.4

### Q4.4-1 — Correct: B
Why: A retry works best with the document, the failed output and the specific error.
- A wrong: same prompt gives no new information.
- C wrong: generic feedback does not say what to fix.
- D wrong: a bigger model does not fix the lack of specific feedback.
Tests: 4.4-K1, 4.4-S1

### Q4.4-2 — Correct: D
Why: The information is absent from the provided source, so retrying cannot produce it.
- A wrong: retry is ineffective for absent information.
- B wrong: `tool_choice` forces a tool call, not missing data.
- C wrong: examples do not create information that is not in the document.
Tests: 4.4-K2, 4.4-S2

### Q4.4-3 — Correct: A
Why: Values are well-typed but inconsistent. That is semantic, and the two-total field pair flags it.
- B wrong: it is not a syntax error, and a schema cannot check sums.
- C wrong: the JSON is already valid.
- D wrong: it is semantic, but `auto` may return text and does not fix it.
Tests: 4.4-K4, 4.4-S4

### Q4.4-4 — Correct: C
Why: Recording the triggering pattern on each finding lets dismissals be analysed by pattern.
- A wrong: confidence wording does not give analysis data.
- B wrong: memory is not systematic tracking.
- D wrong: a longer prompt does not show which patterns are dismissed.
Tests: 4.4-K3, 4.4-S3

### Q4.4-5 — Correct: B
Why: `conflict_detected` makes inconsistent source data visible instead of hiding it.
- A wrong: silently picking one value hides the conflict.
- C wrong: retry cannot fix a source that contradicts itself.
- D wrong: a required field forces a choice and can encourage fabrication.
Tests: 4.4-S4, 4.4-K2

---

## 4.5

### Q4.5-1 — Correct: C
Why: Blocking work needs low latency (synchronous). Latency-tolerant work gets the discount (batch).
- A wrong: batch has no latency guarantee, so it can stall the merge check.
- B wrong: it wastes the 50% saving on the weekly audit.
- D wrong: reversed.
Tests: 4.5-K1, 4.5-K2, 4.5-S1

### Q4.5-2 — Correct: A
Why: A batch entry is one request and one result. No mid-request tool execution.
- B wrong: invented restriction; the problem is the loop, not the list.
- C wrong: invented pricing rule.
- D wrong: batches can take up to 24 hours, and time is not the issue.
Tests: 4.5-K3

### Q4.5-3 — Correct: D
Why: `custom_id` links results to requests. Resubmit only failures, with a fix (chunking).
- A wrong: wasteful.
- B wrong: order is not reliable, and unchanged resubmission fails again.
- C wrong: drops data that could be fixed.
Tests: 4.5-K4, 4.5-S3

### Q4.5-4 — Correct: B
Why: Worst case is 24 hours plus the wait for the next submission. The gap must be 6 hours or less, and 4 hours fits.
- A wrong: 24 + 24 = 48 hours.
- C wrong: 24 + 12 = 36 hours.
- D wrong: 24 + 30 = 54 hours.
Tests: 4.5-S2, 4.5-K1

### Q4.5-5 — Correct: C
Why: Refine on a small synchronous sample first, then run the batch for a good first-pass success rate.
- A wrong: a systematic error shows up only after the full run.
- B wrong: still untested, and errors repeat across batches.
- D wrong: the discount does not remove rerun cost and delay.
Tests: 4.5-S4

---

## 4.6

### Q4.6-1 — Correct: D
Why: The generating session keeps its reasoning context, so it tends to re-justify its choices.
- A wrong: `tool_choice` is unrelated.
- B wrong: prompt length is not the cause.
- C wrong: batch is unrelated to review quality.
Tests: 4.6-K1

### Q4.6-2 — Correct: B
Why: An independent instance without the generator's reasoning catches subtle issues better.
- A wrong: extended thinking in the same session stays anchored to its own choices.
- C wrong: same session, same bias.
- D wrong: confidence wording does not make a reviewer independent.
Tests: 4.6-K2, 4.6-S1

### Q4.6-3 — Correct: A
Why: Per-file passes for local issues plus a cross-file pass avoid thin attention and contradictions.
- B wrong: a longer prompt does not fix attention dilution.
- C wrong: it misses cross-file issues.
- D wrong: random groups are still large single passes and split related files.
Tests: 4.6-K3, 4.6-S2

### Q4.6-4 — Correct: C
Why: Confidence with each finding allows routing. Strong findings go out and weak ones get more checking.
- A wrong: deleting weak findings loses them silently.
- B wrong: no calibration, so weak and strong findings carry the same authority.
- D wrong: the generator rating its own work is the self-review problem.
Tests: 4.6-S3

### Q4.6-5 — Correct: D
Why: Cross-file data flow needs a pass whose whole job is cross-file integration.
- A wrong: more detail within one file cannot see other files.
- B wrong: extended thinking does not widen the scope of what the pass sees.
- C wrong: self-review has the same blind spot and the same limited scope.
Tests: 4.6-K3, 4.6-S2
