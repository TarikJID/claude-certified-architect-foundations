# Module 7 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 4.4 (Validation, Retry, and Feedback Loops)

**Q1.** An extraction fails validation. What should a retry request include to
maximize the chance of success, and why does simply re-asking the same question
perform worse?

**Q2.** A `due_date` field keeps coming back empty for a specific invoice. Before
retrying, what should you check, and why?

**Q3.** What does a `detected_pattern` field enable that a plain "issue found /
no issue found" flag does not?

**Q4.** An invoice schema includes both `stated_total` and `calculated_total`.
What failure mode does this design catch, and how, without any extra validation
pass?

---

## Quiz — Lesson 4.5 (Batch Processing Strategies)

**Q1.** A pre-merge CI check needs Claude's review result within the pipeline's
2-minute timeout. Should this use the Batches API? Why or why not?

**Q2.** Why can't a workflow that needs Claude to call a tool, see the result,
and decide a follow-up action run inside a single batch request?

**Q3.** Out of 10,000 submitted batch documents, 40 come back `errored`. How do
you identify and handle exactly those 40, and what field makes this possible?

**Q4.** You need to guarantee results within a 30-hour SLA using a batch API with
a 24-hour maximum processing window. How often must you submit batches at
minimum, and what's the general formula?

**Q5.** Why should you test an extraction prompt synchronously on a small sample
before submitting 50,000 documents as one batch?

---

## Quiz — Lesson 4.6 (Multi-Instance and Multi-Pass Review)

**Q1.** Why is a Claude session less likely to catch its own mistakes when asked
to review code it just wrote, in the same session?

**Q2.** Would asking the generating session to use extended thinking to "double
check its work" solve the self-review limitation? Why or why not?

**Q3.** For a 40-file pull request, what review architecture avoids both
attention dilution and missing cross-file issues?

**Q4.** What's the benefit of having a verification pass report a confidence
score alongside each finding, rather than a plain flag/no-flag?
