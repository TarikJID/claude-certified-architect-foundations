# Evaluation — course-builder fast-track Module 7 (4.4, 4.5, 4.6) — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_7_Extraction_Quality_Batching_and_Review_Architectures/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items adapted to the fast-track brief (7 items, as supplied by the orchestrator)
- Source of truth used: runs/claude-certified-architect-foundations/research/prompt-engineering-structured-output.md (read in full); runs/claude-certified-architect-foundations/sources/exam-guide.txt lines 608-669 (Tasks 4.4-4.6); runs/claude-certified-architect-foundations/domain-map.md (bullet IDs); Module 7 lesson.md (to check taught-ness). No web fetch was needed.
- Repeat round: no
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID of 4.4/4.5/4.6 taught in fast-lesson and tested by >=1 MCQ, or gap stated; state totals | PASS | Bullets in map: 4.4 = 8 (K1-K4, S1-S4), 4.5 = 8, 4.6 = 6, total 22. Bullets tested by the "Tests:" lines in mcq-answers.md: 4.4 all 8 (K1,K2,K3,K4,S1,S2,S3,S4), 4.5 all 8, 4.6 all 6. Total tested 22/22. Each is taught in a fast-lesson.md bullet (e.g. 4.4-K3/S3 `detected_pattern`; 4.5-S4 "Test the prompt on a small sample"; 4.6-S3 confidence value). No gaps. |
| 2 | One block per task statement, each <=150 words, an "Exam rule", 3-5 bullets, at most one tiny example, short plain sentences | FAIL | Three blocks, each with an "Exam rule": PASS. Word counts (my count, prose incl. heading): 4.4 about 143-150, 4.5 about 139, 4.6 about 130. 4.4 is at the limit; a wc-style count that includes markdown markers (## and "-") would push it over 150. Bullet count is the clear failure. 4.4 has 6 bullets (Pick, Reject, Do not retry, Tool use, calculated_total, detected_pattern). 4.5 has 7 bullets (Pick batch, Pick synchronous, Batch cannot, custom_id, On failures, SLA maths, Test the prompt). Both exceed the 3-5 limit. 4.6 has 5 bullets (OK). Examples: 4.4 has one, 4.6 has one, 4.5 has none. All fine. |
| 3 | mcq.md has 4-5 Qs per statement, tagged with statement ID, A-D, exactly one best answer, scenarios define data, no answers in file, no code/exact-wording recall | PASS | 5 questions each for 4.4, 4.5 and 4.6 (15 total). Each is tagged [4.4]/[4.5]/[4.6] and has options A-D. mcq.md contains no answer text. Scenarios define their data (e.g. Q4.4-3 "line items that do not add up to the stated total", Q4.5-1 explains the batch discount and latency). No question asks for written code or exact wording. I checked each key for a single best answer and found no second defensible option. |
| 4 | mcq.md and mcq-answers.md match as sets; totals; each answer has letter, one-line why, why each wrong option is wrong, bullet IDs | PASS | 15 question labels in mcq.md and 15 in mcq-answers.md. Labels Q4.4-1..5, Q4.5-1..5, Q4.6-1..5 match one to one. Every answer gives "Correct: X", a "Why:" line, exactly three wrong-option explanations, and a "Tests:" line with bullet IDs. |
| 5 | Every tested concept is taught in fast-lesson.md or a lesson.md of this or an earlier module; concepts tested but not taught must be zero | PASS | Concepts tested but not taught: 0. Every correct-answer concept is in fast-lesson.md: retry feedback, absent info, semantic vs syntax, `detected_pattern`, `conflict_detected`, batch vs sync, no tool loop, `custom_id`, resubmit failed only, SLA gap, sample first, self-review, fresh instance, per-file plus cross-file, confidence routing. Distractor-only mentions (`tool_choice`, few-shot, "be conservative" wording) belong to earlier modules (4.1-4.3) and are not what any question tests. |
| 6 | Facts faithful to research file and exam guide; every answer key correct | PASS | All 15 keys checked against the research file and exam-guide.txt lines 611-668, and all are correct. Examples: 4.4-1 matches research "Retry-with-error-feedback"; 4.4-2 matches the "Limits of retry" concept; 4.5-2 matches the no mid-request tool loop; 4.5-3 matches the `custom_id` example; 4.6-4 matches "Confidence self-reporting". SLA item: see the dedicated section below. Fast-lesson statements all trace to the research concepts. |
| 7 | Any concept marked Status: UNSOURCED in research is marked unverified where the learner reads it | PASS | The research file contains no "UNSOURCED" marker anywhere (read in full), so there is nothing to mark. |

## Builder self-report checks

- SLA/batch window (Q4.5-4): Consistent with both sources. Research concept "Calculating batch submission frequency against an SLA" gives interval <= (N-24) h, so 6 h for a 30 h SLA, and calls the guide's 4-hour windows (exam-guide.txt lines 646-647) a safety-margined version. fast-lesson.md states "gaps of 6 hours or less (the guide uses 4)", which matches both. Q4.5-4 options are 4/12/24/30. Worst case is 24 + gap, so the totals are 28, 36, 48 and 54 hours. Only 4 hours meets 30, so there is exactly one defensible answer (B). The answer-key explanation arithmetic is correct. One minor note, not a failure: the (N-24) formula is the researcher's derivation. The guide itself states only the 4-hour figure. This does not make the question ambiguous.
- Builder did not read the module's existing quiz.md: not a checklist item, and there is no evidence of conflict in the output. Not assessed further.

## Persisting issues

None (round 1).

## Not checked

- Whether Module 6 (4.3) and earlier lesson.md files actually contain the `tool_choice`/few-shot concepts used only as distractors. I did not open them. This does not affect item 5, because those concepts are not what any question tests.
- The module's existing quiz.md was not compared against the new MCQs, because the checklist has no item for it.

## Fix required for rework

Item 2 only: reduce the 4.4 block (6 bullets) and the 4.5 block (7 bullets) to 5 bullets or fewer each, and keep every block at or under 150 words. The 4.4 block is already at the limit.
