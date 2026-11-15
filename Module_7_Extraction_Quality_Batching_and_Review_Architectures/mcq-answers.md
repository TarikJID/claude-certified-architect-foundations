# Module 7 Fast MCQ Answers (4.4, 4.5, 4.6)

TUTOR: answers. Never show before the learner has attempted the question.

---

## 4.4

### Q4.4-1 — Correct: B
Why: A second attempt works best when Claude gets the invoice, its first answer and the exact problem.
- A wrong: the same request gives Claude nothing new to go on.
- C wrong: "wrong, try again" does not say what to fix.
- D wrong: a bigger model still does not know what was wrong.
Tests: 4.4-K1, 4.4-S1

### Q4.4-2 — Correct: D
Why: The due date is not in anything Claude receives, so no retry can produce it.
- A wrong: repeating the request cannot create missing information.
- B wrong: forcing a value makes Claude invent a date.
- C wrong: examples do not put the date into these invoices.
Tests: 4.4-K2, 4.4-S2

### Q4.4-3 — Correct: A
Why: The form is well formed but the values disagree. Comparing the printed total with Claude's own sum flags that.
- B wrong: it is not a formatting problem, and form rules cannot check sums.
- C wrong: the output is not broken.
- D wrong: free text loses the guaranteed form and does not check the sum.
Tests: 4.4-K4, 4.4-S4

### Q4.4-4 — Correct: C
Why: Recording what triggered each comment, next to whether it was dismissed, shows which kinds get dismissed.
- A wrong: a confidence instruction gives no data to analyse.
- B wrong: memory is not reliable tracking.
- D wrong: a longer instruction does not show which comments are dismissed.
Tests: 4.4-K3, 4.4-S3

### Q4.4-5 — Correct: B
Why: A "conflict detected" field makes the document's own inconsistency visible instead of hiding it.
- A wrong: quietly picking one value hides the conflict.
- C wrong: a retry cannot fix a document that disagrees with itself.
- D wrong: forcing one value makes Claude pick and hides the conflict.
Tests: 4.4-S4, 4.4-K2

---

## 4.5

### Q4.5-1 — Correct: C
Why: When a person is waiting, use fast synchronous calls. When nobody is waiting, use the cheaper batch.
- A wrong: a batch can take hours, so the merge button stays locked.
- B wrong: it pays full price for the audit for no reason.
- D wrong: the wrong way round.
Tests: 4.5-K1, 4.5-K2, 4.5-S1

### Q4.5-2 — Correct: A
Why: Each batch request is one question and one answer. It cannot pause for the team's code to run a lookup.
- B wrong: made-up restriction. The problem is the back-and-forth, not the tools.
- C wrong: made-up pricing rule.
- D wrong: batches can take up to 24 hours, and time is not the issue.
Tests: 4.5-K3

### Q4.5-3 — Correct: D
Why: The labels match results to requests. Resend only the failures, fixed by splitting them.
- A wrong: pays for 9,960 documents again.
- B wrong: the order is not reliable, and unchanged documents fail again.
- C wrong: throws away documents that can be fixed.
Tests: 4.5-K4, 4.5-S3

### Q4.5-4 — Correct: B
Why: Worst case is the wait for the next batch plus 24 hours. The wait must be 6 hours or less, and 4 hours fits (4 + 24 = 28).
- A wrong: 24 + 24 = 48 hours.
- C wrong: 12 + 24 = 36 hours.
- D wrong: 30 + 24 = 54 hours.
Tests: 4.5-S2, 4.5-K1

### Q4.5-5 — Correct: C
Why: Fix the instructions on a small fast sample first, so the big batch works the first time.
- A wrong: a repeated mistake is only found after all 50,000.
- B wrong: still untested, and the mistake repeats in each batch.
- D wrong: the discount does not remove the cost and delay of rerunning.
Tests: 4.5-S4

---

## 4.6

### Q4.6-1 — Correct: D
Why: The writing conversation keeps its own reasoning, so it defends its choices instead of questioning them.
- A wrong: neat formatting does not make a reviewer question the design.
- B wrong: the length of the request is not the cause.
- C wrong: the batch service has nothing to do with review quality.
Tests: 4.6-K1

### Q4.6-2 — Correct: B
Why: A separate Claude call that never saw the writer's reasoning catches subtle bugs better.
- A wrong: extended thinking in the same conversation still reasons from its own choices.
- C wrong: same conversation, same blind spot.
- D wrong: a caution instruction does not make the reviewer independent.
Tests: 4.6-K2, 4.6-S1

### Q4.6-3 — Correct: A
Why: Per-file passes give focused attention. The separate between-files pass catches cross-file problems.
- B wrong: longer instructions do not fix thin attention.
- C wrong: misses problems between files.
- D wrong: groups are still big passes, and related files may end up apart.
Tests: 4.6-K3, 4.6-S2

### Q4.6-4 — Correct: C
Why: A score on each comment lets strong ones go out and doubtful ones get checked again.
- A wrong: deleting low scores silently loses comments.
- B wrong: a plain yes/no cannot tell strong from doubtful.
- D wrong: the writer scoring its own work is the self-review problem.
Tests: 4.6-S3

### Q4.6-5 — Correct: D
Why: A problem between files needs a pass whose job is looking across files.
- A wrong: more detail about one file still cannot see the other file.
- B wrong: more reasoning does not widen what the pass can see.
- C wrong: re-checking has the same blind spot and sees the same single file.
Tests: 4.6-K3, 4.6-S2
