# Evaluation — course-builder (fast-track Module 6, task statements 4.1-4.3) — round 2

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_6_Precision_Prompting_and_Structured_Output/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items, fast-track brief (7 items, unchanged)
- Source of truth used: runs/claude-certified-architect-foundations/research/prompt-engineering-structured-output.md; runs/claude-certified-architect-foundations/sources/exam-guide.txt (lines 541-607, read directly). Bullet IDs follow the K1..Kn / S1..Sn order of the exam guide (the same scheme round 1 used: 4.1 = 6, 4.2 = 9, 4.3 = 10). I did not re-open domain-map.md. No web fetch needed.
- Repeat round: yes
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID of 4.1-4.3 taught and tested; state totals | PASS | Bullets: 4.1 = 6, 4.2 = 9, 4.3 = 10, so 25 in total. Tested per "Tests:" lines: 4.1 covers K1, K2, K3, S1, S2, S3 (6/6). 4.2 covers K1, K2, K3, K4, S1, S2, S3, S4, S5 (9/9). 4.3 covers K1, K2, K3, K4, S1, S2, S3, S4, S5, S6 (10/10). Total 25/25. The round-1 gaps are closed. 4.3-S5 is tested by Q4.3-5, 4.3-S6 by Q4.3-6, and 4.3-K4 is now fully tested: Q4.3-4 covers required vs optional and Q4.3-5 covers enum "other" + detail. All are taught in fast-lesson.md (the 4.3 bullets on enums and normalization). |
| 2 | fast-lesson.md structure | PASS | Three blocks, one per task statement, each with an "Exam rule" line. Bullets counted from the file as it is now: 4.1 = 5 (4 Pick, 1 Reject), 4.2 = 5, 4.3 = 5. Word counts by hand, including the heading text: 4.1 about 126, 4.2 about 126, 4.3 about 138, and counting the "##" tokens adds 1. All are at or under 150. Examples: 4.1 has one, 4.2 has one, 4.3 has none, so none has more than one. Sentences are short and plain. The 32-word tool_choice bullet is the longest, but each of its sentences is short. Round-1 FAIL (6 and 7 bullets) is resolved. |
| 3 | mcq.md format | PASS | 5 questions for 4.1, 5 for 4.2, and 6 for 4.3 (16 total). The 6 for 4.3 is within the lenient allowance the orchestrator gave. Every question is tagged [4.x], has options A-D, one best answer by my read, and a concrete scenario with data (45%, 95%/40%, $210 vs $250, specific date formats). No answer text appears in mcq.md. No question needs code or recalled exact wording. |
| 4 | mcq.md and mcq-answers.md match as sets | PASS | 16 questions in mcq.md (Q4.1-1..5, Q4.2-1..5, Q4.3-1..6) and 16 answers (same labels, no orphans either way). Each answer has "Correct: X", a "Why:", three wrong-option explanations, and "Tests:" bullet IDs. |
| 5 | Every tested concept taught | PASS | All concepts map to fast-lesson.md bullets: category and checkable criteria, confidence traps, disabling a noisy category and the trust loss, severity examples, 2-4 ambiguous-case examples, full-format examples, acceptable-vs-real-issue pairs, informal measurements and varied layouts, tool schema, tool_choice auto/any/forced, semantic vs syntax errors, optional/nullable, enum other + detail + unclear, and normalization. Q4.3-2 ("forced first, then auto") is covered by the "run one step first" wording. No earlier lesson.md was needed. |
| 6 | Facts faithful; all answer keys verified | PASS | All 16 keys match the exam guide and the research file. 4.1: C (K1/S1), D (S2), A (S3), B (S1/K2), C (K3). 4.2: B (K1/S2), D (K2/S1, 2-4 examples), A (S3/K3), C (K4), C (S4/S5). 4.3: C (K1/S1/K2/S2, "any" when the type is unknown, tool call read for the data), D (S3, forced named tool then auto), B (K3, $210 vs $250), A (S4, optional/nullable), D (K4/S5, "other" + detail + "unclear"), C (S6, normalization in the prompt beside the schema). New or merged 4.3 questions were checked in particular. Q4.3-1 is a sound merge: B (auto) can still return prose and D breaks other types, so C is the single best answer. Distractors in Q4.3-4, Q4.3-5 and Q4.3-6 are each clearly wrong against the sources. |
| 7 | UNSOURCED concepts marked unverified | PASS | The research file has no "Status: UNSOURCED" concepts for 4.1-4.3 (every concept cites the exam guide and/or Anthropic docs), so nothing needed marking. |

## Persisting issues

None. Round-1 issues (4.1 with 6 bullets, 4.3 with 7 bullets, 4.3-S5 and S6 untested, 4.3-K4 half-tested) are all resolved.

## Not checked

- Word counts are my manual tallies. All are at most 139 even when headings are included, so the 150 cap is not in doubt.
- No lesson.md files were opened. They were not needed because fast-lesson.md alone covers every tested concept.
- I did not re-open domain-map.md. Bullet totals and IDs come from the exam guide's order and the round-1 count, and they are consistent with every "Tests:" ID in the answers file.
