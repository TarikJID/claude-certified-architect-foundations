# Evaluation — course-builder (fast-track Module 9, task statements 5.3 and 5.4) — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_9_Error_Propagation_and_Codebase_Context/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items, adapted to the fast-track brief (7 items, as supplied by the orchestrator)
- Source of truth used: runs/claude-certified-architect-foundations/research/context-management-reliability.md (read in full) and runs/claude-certified-architect-foundations/domain-map.md (bullet IDs and wording for 5.3, 5.4). No URLs fetched.
- Repeat round: no
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every 5.3/5.4 bullet ID taught and tested by at least one MCQ (or gap stated); state totals | PASS | Bullets in map: 17 (5.3: 8 = K1-K4, S1-S4; 5.4: 9 = K1-K4, S1-S5). Bullets tested: 17, gaps: 0. Map: 5.3-K1 Q1; K2 Q2; K3 Q1,Q4; K4 Q3; S1 Q1,Q4; S2 Q2; S3 Q4; S4 Q3,Q5. 5.4-K1 Q1; K2 Q1; K3 Q2; K4 Q4; S1 Q2; S2 Q1; S3 Q5; S4 Q4; S5 Q3. Each is taught in a fast-lesson bullet. |
| 2 | fast-lesson.md: one block per statement, each ≤150 words (counted), "Exam rule", 3-5 bullets, at most one tiny example, short plain sentences | FAIL | Two blocks, each with an Exam rule and one example, so those parts pass. Failures: (a) Bullets: both blocks have 6 bullets, over the 3-5 limit. 5.3 has 6 (Pick, Pick, Pick, Pick, Reject, Trap). 5.4 has 6 (Symptom, Pick x4, Trap). The builder self-reported this. (b) Word count, counted by hand word by word, body from "Exam rule" through the Example, headings excluded: 5.3 = 158 (rule 24 + bullets 14+23+24+18+20+16 = 115 + example 19). 5.4 = 165 (rule 22 + bullets 30+19+21+20+21+13 = 124 + example 19). Both exceed 150. Even without the example they are 139 and 146, and adding the headings makes it worse. The builder's hand estimates (~140 and ~135) were wrong. |
| 3 | mcq.md: 4-5 questions per statement, tagged, A-D, one best answer, scenario states what data means; no answer text; no code or exact-wording recall | PASS | 5 questions under 5.3 and 5 under 5.4, each tagged [5.3] or [5.4] and with options A-D. Scenarios explain the data, for example "times out after 30 seconds, but 2 of roughly 5 relevant documents were already retrieved". No answer key or rationale in the file (only a pointer to mcq-answers.md). No question needs written code or exact wording. |
| 4 | mcq.md and mcq-answers.md match as sets; totals; each answer has letter, one-line why, why each wrong option is wrong, bullet IDs | PASS | Totals: 10 questions in mcq.md, 10 answers in mcq-answers.md, with 5.3 Q1-Q5 and 5.4 Q1-Q5 matching one to one. Every entry has the letter, a one-line "Why:", three wrong-option explanations and a "Tests ..." bullet-ID line. The IDs agree with the map in item 1. |
| 5 | Every concept tested is taught in fast-lesson.md or in lesson.md of this or an earlier module; concepts tested not taught = 0 | PASS | Concepts tested: access failure vs empty, structured error, local recovery, coverage notes, silent suppression, context degradation, scratchpad, subagent delegation, phase summary, manifest, /compact. All appear in fast-lesson.md. Concepts tested not taught: 0. Minor, not a failure: subagent context isolation (5.4 Q5 wrong option D) is not in the 5.4 block, but the stem states the fact. Earlier modules' lesson.md could not be checked (see Not checked). |
| 6 | Facts faithful to the research and exam guide; each answer key verified correct | PASS | Verified against the research concepts. 5.3: Q1 B (structured error context), Q2 D (access failure vs valid empty), Q3 A (graceful degradation, disclose gap), Q4 C (local recovery then propagate with attempts and partials), Q5 B (coverage annotations). 5.4: Q1 C (context degradation, scratchpad or fresh session), Q2 A (subagent delegation), Q3 D (/compact proactively with instruction), Q4 B (state exports plus manifest), Q5 C (phase summary injected). All keys correct, with one unambiguous best answer. The lesson wording matches the research. |
| 7 | Any Status: UNSOURCED concept marked unverified where the learner reads it | PASS | No "Status: UNSOURCED" marker appears on any concept in the research file, including 5.3 and 5.4. Nothing needed marking. |

## Persisting issues

Not applicable (round 1).

## Not checked

- sources/exam-guide.txt was not opened. Bullet wording was checked against domain-map.md, which says it was transcribed verbatim from the guide. Item 6 passes on the research file plus the domain map.
- lesson.md files of Module 9 and earlier modules were not opened, because this environment has no directory listing or search tool. The item 5 PASS rests on fast-lesson.md alone, which covers every tested concept.
- Word counts were done by hand, with no word-count tool available. The margins (158 and 165 against a limit of 150) are too large to flip with counting convention. Dropping the example would give 139 and 146, but the item 2 bullet-count failure remains either way.

## Summary of required rework (for routing; no fixes made by evaluator)

Item 2 only: reduce each block to 5 bullets or fewer, and bring each block to 150 words or fewer, counted exactly.
