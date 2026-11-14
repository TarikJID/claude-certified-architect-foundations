# Evaluation — course-builder fast-track Module 7 (4.4, 4.5, 4.6) — round 3

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_7_Extraction_Quality_Batching_and_Review_Architectures/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder fast-track checklist (7 items, unchanged)
- Source of truth used: all three output files re-read in full this round; round-1 and round-2 verdicts (read). Research-file and exam-guide facts were verified in round 1 and are carried forward. This round I only checked that the current lesson wording still matches them.
- Repeat round: yes
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID taught and tested; totals | PASS | Totals: 22 bullets in the map (4.4 = 8, 4.5 = 8, 4.6 = 6). The "Tests:" lines in mcq-answers.md cover 4.4 K1-K4 and S1-S4, 4.5 K1-K4 and S1-S4, and 4.6 K1-K3 and S1-S3. That is 22 of 22 tested. Each concept is taught in the current fast-lesson.md: retry with specific error, absent info, semantic vs syntax, calculated_total, conflict_detected, detected_pattern, batch vs sync, no tool loop, custom_id, resubmit failures, SLA maths, sample test, self-review weak, fresh instance, per-file plus cross-file, confidence routing. |
| 2 | One block per statement, <=150 words (exact, incl. heading), Exam rule, 3-5 bullets, <=1 tiny example, short plain sentences | PASS | Three blocks, each with an "Exam rule". Bullets counted from the file as it is now: 4.4 = 5 (lines 7-11), 4.5 = 5 (lines 21-25), 4.6 = 5 (lines 33-37). Word counts including the heading text and excluding markdown symbols: 4.4 = 127, 4.5 = 127, 4.6 = 126. All are at or under 150, and they stay under 150 even if markdown markers are counted. Examples: 4.4 has one, 4.5 has none, 4.6 has one (all tiny). Sentences are short and plain. The SLA bullet is the longest, at 31 words across 3 sentences. |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, concrete scenario, no answers, no code/wording recall | PASS | 5 questions each for 4.4, 4.5 and 4.6, 15 in total. Each is tagged [4.x], has options A-D and a concrete scenario. mcq.md contains no answer text. No question needs code or exact-wording recall. |
| 4 | mcq.md and mcq-answers.md match as sets; letter, why, why-wrong per option, bullet IDs | PASS | 15 labels in mcq.md and 15 in mcq-answers.md, matching one to one (Q4.4-1..5, Q4.5-1..5, Q4.6-1..5). Each answer has "Correct: X", a "Why:" line, three wrong-option lines and a "Tests:" line with bullet IDs. |
| 5 | Every tested concept taught in fast-lesson.md or an earlier/same-module lesson.md | PASS | Every correct-answer concept appears in the current fast-lesson.md (see item 1). Distractor-only mentions (`tool_choice`, few-shot, confidence wording) are not what any question tests. |
| 6 | Facts faithful to the research file and exam guide; keys correct | PASS | Keys re-derived this round: 4.4: B, D, A, C, B. 4.5: C, A, D, B, C. 4.6: D, B, A, C, D. All are correct and each has a single best answer. The SLA arithmetic (24 + gap = 28/36/48/54 h vs a 30 h SLA; the answer is the 4 h gap) is correct. The lesson's "6 hours or less (the guide uses 4)" matches the round-1 verification against the research file and exam-guide.txt. |
| 7 | UNSOURCED concepts marked unverified where the learner reads them | PASS | The research file has no UNSOURCED markers (checked in round 1). Nothing needs marking. |

## Persisting issues

- Item 2 (bullet count above 5 in the 4.4 block and the 4.5 block) was first raised in round 1 and again in round 2. It is now resolved: both blocks have 5 bullets in the file on disk. No issue persists.

## Not checked

- I did not re-open the research file or exam-guide.txt this round. Facts were verified against them in round 1, and the lesson's factual statements are consistent with that verification.
- I did not re-open domain-map.md this round, so the bullet ID totals come from round 1 and the Tests lines.
- Word counts are my manual counts. They have wide margins (about 23 words under the limit), so a different counting convention would not change the result.
