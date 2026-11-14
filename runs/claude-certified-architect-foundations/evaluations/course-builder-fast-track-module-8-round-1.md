# Evaluation — course-builder fast-track Module 8 (task statements 5.1, 5.2) — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_8_Context_Management_and_Escalation_Design/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items as adapted to the fast-track brief (7 items)
- Source of truth used: runs/claude-certified-architect-foundations/research/context-management-reliability.md; runs/claude-certified-architect-foundations/sources/exam-guide.txt (lines 674-722, 5.1 and 5.2 bullets); runs/claude-certified-architect-foundations/domain-map.md (5.1 and 5.2 bullet IDs). No web fetch needed.
- Repeat round: no
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID of 5.1, 5.2 taught and tested by at least one MCQ, or gap stated; state totals | PASS | Bullets in map: 19 (5.1 = 10: K1-K4, S1-S6; 5.2 = 9: K1-K4, S1-S5). Bullets tested: 19 of 19. Every ID appears in a "Tests:" line in mcq-answers.md, and every one is taught in fast-lesson.md. 5.2-K1 is tested via Q1 and Q4. The "unable to make progress" trigger is named only as an option in 5.2 Q4-B and has no question of its own. This matches the builder's self-report. The bullet is still covered, so this is not a gap. |
| 2 | fast-lesson.md: one block per task statement, each <=150 words, an "Exam rule", 3-5 bullets, at most one tiny example, short plain sentences | FAIL | Two blocks, one per statement (pass). Word counts by hand are about 129 for 5.1 and about 134 for 5.2, both under 150 (pass). Each block has an Exam rule and one tiny example (pass). Bullet count fails. 5.1 has 6 bullets (case facts, tool results, middle of inputs, stateless API, subagent output, Trap). 5.2 has 6 bullets (three triggers, explicit request, frustrated, policy silent, several matches, Trap). The limit is 3-5. |
| 3 | mcq.md: 4-5 questions per statement, tagged, A-D, one best answer, scenario defines data, no answer text, no written code or recalled exact wording | PASS | 5 questions under 5.1 and 5 under 5.2, each tagged [5.1] or [5.2]. All have options A-D. Scenarios define their data (e.g. 5.1 Q1 gives the order, promised date, invoice and amount; 5.2 Q5 says the tool returned two accounts). mcq.md contains no answers, only a pointer to mcq-answers.md. No question needs code or exact wording. Each question has one defensible best answer. |
| 4 | mcq.md and mcq-answers.md match as sets; totals; each answer has letter, one-line why, why each wrong option is wrong, bullet IDs | PASS | 10 questions in mcq.md, 10 in mcq-answers.md. Q1-Q5 under each statement match one to one. Every entry gives the correct letter, a "Why:" line, three wrong-option explanations, and "Tests:" IDs. All IDs exist in the domain map. |
| 5 | Every concept tested is taught in fast-lesson.md or an earlier lesson.md; concepts tested but not taught = 0 | PASS | Concepts used in the questions are all in fast-lesson.md: summary blur, case-facts block per issue, trimming, key-findings plus headers, stateless API, compact structured subagent output with metadata, policy silence, explicit human request, frustration handling, sentiment and confidence unreliability, few-shot criteria, clarification on multiple matches. Count not taught = 0. Minor: 5.1 Q4-C's phrase "or a faithful summary" is not in the lesson, but it is not the tested concept. |
| 6 | Facts faithful to the research and exam guide; answer keys actually correct | PASS | The 5.1 and 5.2 bullet IDs and wording in the domain map match exam-guide.txt lines 674-722. All 10 keys are correct against the research and the guide: 5.1 B, D, A, C, A; 5.2 C, A, D, B, C. Observation, not a failure: the fast-lesson 5.1 "Trap: bigger context window or summarize harder" line has no direct source sentence in the research. It is only loosely supported by the context-rot and compaction concepts. It is used as the wrong-option rationale for 5.1 Q1-A and Q1-C. |
| 7 | Concepts marked Status: UNSOURCED in the research are marked unverified where the learner reads them | PASS | The research file has no "Status: UNSOURCED" markers for the 5.1 or 5.2 concepts, so nothing needs marking. |

## Builder self-report check

- 5.2-K1 "unable to make progress" trigger has no question of its own: confirmed (see item 1).
- The builder did not open the exam guide or the domain map: all bullet IDs in the output were checked against the real domain map and the exam guide. They are correct and complete, with no invented, missing or mis-numbered IDs.

## Persisting issues

None (round 1).

## Not checked

- Word counts were done by hand, not by tool. Both blocks are about 20 words under the limit, so a small counting error would not change the result.
- Whether any lesson.md from an earlier module covers extra concepts was not checked. It was unnecessary because every tested concept is taught in fast-lesson.md.
