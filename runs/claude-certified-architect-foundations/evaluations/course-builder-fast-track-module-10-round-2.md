# Evaluation — course-builder fast-track Module 10 (5.5, 5.6) — round 2

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_10_Human_Review_Confidence_and_Provenance/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items, adapted to the fast-track brief (same 7 items as round 1)
- Source of truth used: runs/claude-certified-architect-foundations/domain-map.md (5.5 and 5.6 bullets, lines 451-474); round-1 verdict file (read only). Research file and exam guide were verified in full in round 1. This round I re-checked only the changed content against the domain-map bullets. No web fetch needed.
- Repeat round: yes
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every 5.5/5.6 bullet ID taught and tested by at least one MCQ; state totals | PASS | Totals: 8 bullets for 5.5 plus 9 for 5.6 = 17 bullets; 17 taught, 17 tested, 0 gaps. Taught in fast-lesson.md after the merge. 5.5: K1 (exam rule, Reject bullet), K2 (stratified sampling bullet), K3 (field-level confidence bullet), K4 (per-type and field check before cutting review), S1 (sampling bullet), S2 (first Pick), S3 (confidence bullet, Reject "0.9 means 90%"), S4 (routing bullet). 5.6: K1 (rule, Reject "summaries that merge claims"), K2 (claim-source bullet), K3 (conflict bullet), K4 (date bullet and example), S1 (mappings bullet), S2 (separate sections plus "Keep each source's own context and method"), S3 (conflict bullet), S4 (date bullet), S5 (format bullet). Tested via the Tests lines: 5.5 Q1 K1/S2/K4, Q2 K2/S1, Q3 K3/S3, Q4 S4, Q5 K4/K1/S2; 5.6 Q1 K1/K2/S1, Q2 K3/S3, Q3 K4/S4, Q4 S2, Q5 S5. All 17 IDs are present. The round-1 gap on 5.6-S2 is closed. |
| 2 | fast-lesson.md: one block per statement, each <=150 words (exact count), Exam rule, 3-5 bullets, at most one tiny example, short plain sentences | PASS | Exact count, from "Exam rule" through the Example line, excluding the heading: 5.5 = 126 words (23 rule + 17 + 13 + 14 + 24 + 22 bullets + 13 example). 5.6 = 124 words (22 + 17 + 31 + 15 + 11 + 15 + 13). Both are under 150 even if the heading is added. Each block has an "Exam rule". Each has exactly 5 bullets, so the round-1 failure (7 bullets) is fixed. Each has exactly one one-line example. Sentences are short and plain. The 5.6 date bullet reads a little awkwardly ("may be change over time") but it is clear. |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, concrete scenario, no answer text, no code/exact-wording recall | PASS | 5 questions under 5.5 and 5 under 5.6, each tagged in the same `**Qn [x.y]**` format. All have options A-D and one defensible best answer. Scenarios are concrete, with figures explained. mcq.md has only a pointer to the answers file. No code or exact-wording recall. |
| 4 | mcq.md and mcq-answers.md match as sets; totals; each answer has letter, why, why-wrong per option, bullet IDs | PASS | 10 questions in mcq.md and 10 entries in mcq-answers.md, with matching IDs. All answer labels now use `**Qn [x.y]** Correct: L`, so the round-1 label inconsistency is fixed. Each entry has a letter, a Why line, exactly 3 wrong-option lines for the other letters, and a Tests line with valid bullet IDs. |
| 5 | Every tested concept taught in fast-lesson.md or an earlier/same-module lesson | PASS | The round-1 note is fixed: 5.6 Q4's "keeping each source's own context" is now taught in the separate-sections bullet. All other tested concepts (per-segment accuracy, stratified sampling, field calibration, priority routing, claim-source mappings, conflict annotation, dates, format by content type) are in fast-lesson.md. Concepts tested but not taught = 0. |
| 6 | Facts faithful to research file and exam guide; answer keys correct | PASS | The keys are unchanged since round 1, where all 10 were verified: 5.5 C, A, D, B, C; 5.6 B, D, A, C, D. I re-read each question this round and each key is still the single best answer. The new fast-lesson wording ("keep each source's own context and method") matches 5.6-S2 in the domain map. Merging the bullets introduced no new factual claims. |
| 7 | UNSOURCED concepts marked unverified where the learner reads them | PASS | Round 1 found no UNSOURCED marker on any 5.5 or 5.6 concept. The merge added no new concepts, so nothing needs marking. |

## Persisting issues

None. The round-1 issue (7 bullets per block against a limit of 3-5) is resolved. Both blocks now have 5 bullets and stay under 150 words. The round-1 minor notes (5.6-S2 context point missing from the lesson, cosmetic label mismatch) are also resolved.

## Not checked

- I did not re-open the research file or the exam guide this round. Their content was verified in full in round 1, and the only changes since then are a bullet merge, one added phrase that matches the domain map, and a label format fix.
- Earlier modules' lesson.md files. They are not needed, since every tested concept is covered in fast-lesson.md.
- Whether the builder's own message stated the totals. The totals are stated in this file instead.
