# Evaluation — course-builder fast-track Module 10 (5.5, 5.6) — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_10_Human_Review_Confidence_and_Provenance/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items, adapted to the fast-track brief (7 items as given by orchestrator)
- Source of truth used: runs/claude-certified-architect-foundations/domain-map.md (read in full); runs/claude-certified-architect-foundations/research/context-management-reliability.md (read in full); runs/claude-certified-architect-foundations/sources/exam-guide.txt (lines 766-809, Task Statements 5.5 and 5.6, compared against the domain map). No web fetch needed.
- Repeat round: no
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every 5.5/5.6 bullet ID taught and tested by at least one MCQ, or gap stated; state totals | PASS (with note) | Domain map has 8 bullets for 5.5 (K1-K4, S1-S4) and 9 for 5.6 (K1-K4, S1-S5) = 17. The exam guide text matches the map. Tested: 5.5 K1 (Q1,Q5), K2 (Q2), K3 (Q3), K4 (Q1,Q5), S1 (Q2), S2 (Q1,Q5), S3 (Q3), S4 (Q4); 5.6 K1 (Q1), K2 (Q1), K3 (Q2), K4 (Q3), S1 (Q1), S2 (Q4), S3 (Q2), S4 (Q3), S5 (Q5). That is 17 of 17 tested and no gaps. Each is taught in fast-lesson.md, with one small exception under item 5. Note: the output files do not state the totals, and I was not given the builder's message, so I could not check whether it did. |
| 2 | fast-lesson.md: one block per statement, each <=150 words, Exam rule, 3-5 bullets, at most one tiny example, short plain sentences | FAIL | One block per statement: yes. Word counts are about 127 for 5.5 and about 128 for 5.6, both within 150. Each has an "Exam rule" and exactly one tiny example. Short plain sentences: yes. Bullet count fails. 5.5 has 7 bullets (4 Pick, 3 Reject) and 5.6 has 7 bullets (5 Pick, 2 Reject). The limit is 3-5. |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, scenario defines data, no answer text, no code or exact-wording recall | PASS | 5 questions under 5.5 and 5 under 5.6, each tagged [5.5] or [5.6] with options A-D. I checked each for a single defensible best answer and found one each (for example 5.5 Q5: C beats A, and 5.6 Q2: D). Data meanings are given in the scenarios: 5.5 Q3 explains "labeled validation set" and the 0.9 score, and 5.5 Q5 gives the per-segment figures. mcq.md contains only a pointer to the answers file and no answer text. No code or exact-wording recall. |
| 4 | mcq.md and mcq-answers.md match as sets; state totals; each answer has letter, one-line why, why each wrong option is wrong, bullet IDs | PASS (with note) | Both files have 5 + 5 = 10 entries with the same IDs (5.5 Q1-Q5, 5.6 Q1-Q5). Every entry gives the correct letter, a Why line, exactly 3 wrong-option explanations that cover the right letters, and a Tests line. All cited bullet IDs exist in the domain map and match the question content. Builder self-report check: the builder said the 5.5 Q1 label is the odd one out. It is not. Q1, Q3 and Q4 use `**Qn [5.5]**`, and Q2 is the one that uses `**Q2** [5.5]`. The mismatch is cosmetic. The ID and tag are still present, so the set comparison holds. Totals are not stated in the output files (see item 1). |
| 5 | Every concept tested is taught in fast-lesson.md or an earlier lesson.md (concepts tested not taught = 0) | PASS (minor note) | Each question maps to a lesson bullet or rule: aggregate masking, stratified sampling including high-confidence items, field-level calibration, ambiguous/contradictory routing and priority, claim-source mappings, conflict annotation, dates, well-established vs contested sections, and format by content type. Minor note: the correct option of 5.6 Q4 ("keeping each source's own context") reflects 5.6-S2's "preserving original source characterizations and methodological context", which fast-lesson.md does not mention. The tested core, separate sections, is taught. I did not treat this as a failure, but the builder may want to add it. I did not open earlier modules' lesson.md files, because the lesson covers all tested concepts. |
| 6 | Facts faithful to research file and exam-guide.txt; answer keys actually correct | PASS | I checked all 10 keys against the research concepts and the exam guide text. 5.5: Q1 C, Q2 A, Q3 D, Q4 B, Q5 C. 5.6: Q1 B, Q2 D, Q3 A, Q4 C, Q5 D. All are correct. Q3's figures (0.9 giving 96% for invoice date and 82% for line-item total) and the 500 vs 1,200 example match the research examples. The "contradictory plus low confidence goes first" rule matches the 5.5-S4 research example. The wrong-option reasons are sound. |
| 7 | Concepts marked Status: UNSOURCED in the research are marked unverified where the learner reads them | PASS | The research file has no "Status: UNSOURCED" marker on any 5.5 or 5.6 concept. Every concept lists a Source. Nothing needs marking. |

## Persisting issues

None. This is round 1.

## Not checked

- Whether the builder's own report stated bullet totals (items 1 and 4). I was not given that report, and the output files contain no totals line.
- Earlier modules' lesson.md files. Not needed, since every tested concept is covered in fast-lesson.md except the minor point in item 5.

## Rework required (for the orchestrator to route)

- fast-lesson.md: both blocks (5.5 and 5.6) have 7 bullets and must have 3-5, while staying at or under 150 words.
