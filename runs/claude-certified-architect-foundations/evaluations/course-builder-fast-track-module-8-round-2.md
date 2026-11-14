# Evaluation — course-builder fast-track Module 8 (task statements 5.1, 5.2) — round 2

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_8_Context_Management_and_Escalation_Design/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items as adapted to the fast-track brief (7 items, unchanged from round 1)
- Source of truth used: round 1 verdict (/home/user/claude-certified-architect-foundations/runs/claude-certified-architect-foundations/evaluations/course-builder-fast-track-module-8-round-1.md); the current fast-lesson.md. mcq.md and mcq-answers.md were not re-read because the builder reported no change to them. Round 1 verified them against research/context-management-reliability.md and sources/exam-guide.txt.
- Repeat round: yes
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID of 5.1, 5.2 taught and tested; totals | PASS | Unchanged from round 1: 19 of 19 bullets tested (5.1 = 10, 5.2 = 9). fast-lesson.md still covers each concept. |
| 2 | fast-lesson.md: one block per statement, each <=150 words, Exam rule, 3-5 bullets, <=1 tiny example, short plain sentences | FAIL | Word count by hand: 5.1 is about 130 words and 5.2 is about 125. Both are under 150. Each block has an Exam rule and one example. The bullet count is still 6 in each block. 5.1 has 6 bullets on lines 7-12: case facts, tool results, middle of inputs, stateless API, subagent output, Trap. 5.2 has 6 bullets on lines 20-25: three triggers, explicit request, frustrated, policy silent, several matches, Trap. The limit is 3-5. The builder said the bullets were merged to 5 per block. The file does not show that. |
| 3 | mcq.md: 4-5 questions per statement, tagged, A-D, one best answer, no answers, no code or exact wording | PASS | Unchanged from round 1 (5 + 5 questions). |
| 4 | mcq.md and mcq-answers.md match as sets; each answer complete | PASS | Unchanged from round 1 (10 and 10, all fields present). |
| 5 | Every tested concept taught | PASS | Unchanged from round 1. fast-lesson.md still carries every tested concept. |
| 6 | Facts faithful; keys correct | PASS | Unchanged from round 1 (keys 5.1 B, D, A, C, A; 5.2 C, A, D, B, C). |
| 7 | UNSOURCED concepts marked unverified | PASS | No UNSOURCED markers exist for 5.1 or 5.2 in the research file. |

## Persisting issues

- Item 2, bullet count above 5 in both blocks (6 and 6). First raised in round 1 and still present. Round 2 did not change the count.

## Not checked

- mcq.md and mcq-answers.md were not re-read. I relied on the builder's statement that they were not changed, and on the round 1 results.
- Word counts were done by hand. Both blocks are well under 150, so a small counting error would not change the result.
