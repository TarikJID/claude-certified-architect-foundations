# Evaluation — course-builder (fast-track Module 6, task statements 4.1-4.3) — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_6_Precision_Prompting_and_Structured_Output/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder "Done when" items, adapted to the fast-track brief (7 items, as given by the orchestrator)
- Source of truth used: runs/claude-certified-architect-foundations/research/prompt-engineering-structured-output.md; runs/claude-certified-architect-foundations/sources/exam-guide.txt (Domain 4, lines 541-607, read directly); runs/claude-certified-architect-foundations/domain-map.md (bullet list for 4.1-4.3). No web fetch needed.
- Repeat round: no
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID of 4.1-4.3 taught and tested, or gap stated; state totals | PASS (with note) | Bullets in map: 4.1 = 6 (K3,S3), 4.2 = 9 (K4,S5), 4.3 = 10 (K4,S6); total 25. Tested per mcq-answers.md "Tests:" lines: 4.1 = 6/6, 4.2 = 9/9, 4.3 = 8/10. Total tested 23/25. Untested: 4.3-S5 and 4.3-S6. The builder's self-report is confirmed: no answer cites S5 or S6. Both are taught in fast-lesson.md (the "other"/"unclear" enum bullet and the normalization bullet). Note: the gap is stated only in the builder's self-report, not inside the three files. Note: 4.3-K4 is only half-tested. Q4.3-5 covers required vs optional. Nothing tests the enum "other" + detail pattern, and "other" appears only as a wrong option. |
| 2 | fast-lesson.md: one block per statement, each <=150 words, "Exam rule", 3-5 bullets, at most one tiny example, short plain sentences | FAIL | Three blocks, each with an "Exam rule" line. Word counts by hand: 4.1 about 128, 4.2 about 127, 4.3 about 143 excluding the heading or about 152 including it (borderline, the ruling on whether headings count is unclear). **Bullet counts: 4.1 has 6 bullets (Pick x4, Reject, Why disable). 4.3 has 7 bullets (Pick, tool_choice, Schema valid, Pick, Pick, Pick, Trap). Both exceed the 3-5 limit.** 4.2 has 5 bullets and passes. Examples: 4.1 has one, 4.2 has one, 4.3 has none, so that is within the limit. Sentences are short and plain except the long tool_choice bullet in 4.3 (32 words). |
| 3 | mcq.md: 4-5 questions per statement, tagged, A-D, one best answer, scenario defines data, no answer text, no written code or exact wording | PASS | 5 questions each for 4.1, 4.2 and 4.3 (15 total), each tagged [4.x]. All have options A-D. No answer text is present in mcq.md. Scenarios define their data (for example "about 45% of style findings are wrong", "security findings are correct 95% of the time", "three line item amounts add up to $210"). No question needs written code or recalled exact wording. Each question has one best answer by my read. |
| 4 | mcq.md and mcq-answers.md match as sets; totals; each answer has letter, one-line why, why each wrong option is wrong, bullet IDs | PASS | Questions written: 15 (Q4.1-1..5, Q4.2-1..5, Q4.3-1..5). Answers written: 15, with identical labels and no orphans either way. Every answer gives "Correct: X", a "Why:" line, three wrong-option explanations (A-D minus the correct one), and "Tests:" bullet IDs. |
| 5 | Every concept tested is taught in fast-lesson.md or lesson.md of this or an earlier module; concepts tested not taught must be zero | PASS (with caveat) | Concepts tested not taught in fast-lesson.md: 0. Every tested concept maps to a fast-lesson bullet: confidence wording, disabling a noisy category, severity examples, format examples, ambiguous-case examples, acceptable vs real issue pairs, informal measurements and varied layouts, tool-schema output, tool_choice auto/any/forced, semantic vs syntax errors, nullable fields. Minor looseness: Q4.3-3's "force the named tool first, then auto afterwards" is only implied by the lesson. Q4.2-5's inline-citation vs bibliography case is covered only by the generic "varied document layouts" bullet. I did not open any lesson.md, so the "earlier module" path was not needed or checked. |
| 6 | Facts faithful to research file and exam guide; every answer key actually correct | PASS | All 15 keys match the sources. 4.1: C (K1/S1, exam guide 544-545), D (S2), A (S3), B (S1/K2), C (K3). 4.2: B (K1/S2), D (K2/S1, 2-4 examples), A (S3/K3), C (K4), C (S4/S5). 4.3: A (K1/S1), C (S2: "any" when document type is unknown), D (S3: forced named tool, then auto), B (K3: $210 vs $250), D (S4: optional/nullable). The wrong-option rationales are consistent with the research. Minor: the fast-lesson 4.2 line "Reject: ... 'do not hallucinate' lines, and confidence thresholds" goes slightly beyond the exam guide wording. It is consistent with the research's prose-vs-examples rationale, so I did not fail it. |
| 7 | Any concept with Status: UNSOURCED in the research is marked unverified where the learner reads it | PASS | The research file contains no "Status: UNSOURCED" entries (every concept cites the exam guide and/or Anthropic docs), so nothing needs marking. |

## Persisting issues

Not applicable (round 1).

## Not checked

- No lesson.md of Module 6 or earlier modules was opened. Item 5 was judged against fast-lesson.md alone and found sufficient.
- Word counts are my manual tallies. 4.3 is 143 or 152 depending on whether the heading counts, and the checklist does not say. The REWORK does not depend on this, because the bullet-count failures are unambiguous.
- Whether the builder stated the 4.3-S5 and 4.3-S6 gap in its handback was not visible to me. I only confirmed that the gap is real and that the files themselves do not state it.

## Rework needed (for routing, no fixes made)

- fast-lesson.md 4.1 block: 6 bullets, limit is 3-5.
- fast-lesson.md 4.3 block: 7 bullets, limit is 3-5. The block is also at or near the 150-word cap.
