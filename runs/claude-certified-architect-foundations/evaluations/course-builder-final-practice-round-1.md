# Evaluation — course-builder final practice exam — round 1

- Output evaluated: /home/user/claude-certified-architect-foundations/final-practice.md and /home/user/claude-certified-architect-foundations/final-practice-answers.md
- Checklist: course-builder "Done when" (final practice items 1-6, as supplied by the orchestrator)
- Source of truth used: runs/claude-certified-architect-foundations/sources/exam-guide.txt (read in full), runs/claude-certified-architect-foundations/domain-map.md (read in full), course-outline.md, Module_1 to Module_5 lesson.md, Module_6/7/8/10 fast-lesson.md (all read). No web fetch needed.
- Repeat round: no
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | 20 questions under 4 scenario headings in the exam guide, 3-4 sentence setup, 5 per scenario | PASS | Headings: Scenario 1 Customer Support Resolution Agent (Q1-5), Scenario 2 Code Generation with Claude Code (Q6-10), Scenario 3 Multi-Agent Research System (Q11-15), Scenario 6 Structured Data Extraction (Q16-20). All four titles match exam-guide section 5 exactly. Counted 5 questions each, 20 total. Setups: S1 = 4 sentences, S2 = 3, S3 = 3, S6 = 3. |
| 2 | Domain mix roughly 27/18/20/20/15 (claimed 5/4/4/4/3) | PASS | By tag: D1 = Q1 (1.5), Q4 (1.4), Q10 (1.7), Q11 (1.3), Q12 (1.2) = 5. D2 = Q2 (2.2), Q13 (2.3), Q15 (2.1), Q19 (2.3) = 4. D3 = Q6 (3.1), Q7 (3.3), Q8 (3.4), Q9 (3.2) = 4. D4 = Q16 (4.3), Q17 (4.4), Q18 (4.5), Q20 (4.4) = 4. D5 = Q3 (5.2), Q5 (5.1), Q14 (5.6) = 3. Ideal for 20 questions is 5.4/3.6/4/4/3, so this is within rounding. The claim is verified. |
| 3 | Tagged with an existing task statement ID; A-D; one best answer; plausible distractors; no code or exact-wording recall; no answer text in final-practice.md | PASS | Every tag (1.2-1.5, 1.7, 2.1-2.3, 3.1-3.4, 4.3-4.5, 5.1, 5.2, 5.6) exists in domain-map.md. Every question has options A-D. I found one defensible best answer per question. Distractors are the guide's named anti-patterns (confidence scores, iteration caps, "be conservative", averaging, forcing one tool). Questions test recognition and application only, and options name features but nothing needs to be typed or recalled verbatim. final-practice.md contains no answer letters or explanations. Minor observation, not a failure: the Q8 stem has no scenario detail ("Which assignment of approach to task is best?"), but it is unambiguous. |
| 4 | The two files match as sets; each answer has letter, one-line why, why each wrong option is wrong, and task ID | PASS | Both files hold Q1-Q20 with the same 4 scenario groupings (20 and 20). Task IDs match question-by-question in both files. Each answer has "Correct:", one "Why:" line and exactly three wrong-option lines. The closing table gives Q numbers per domain (5/4/4/4/3 = 20) and agrees with the tags. |
| 5 | Every answer key correct against exam guide / domain map / research; even spread of letters | PASS | Verified all 20 against exam-guide section 6 and domain-map bullets. Q1 B (1.5-K2/S2, K3). Q2 D (2.2-S1/S2, K3). Q3 A (5.2-S2). Q4 C (1.4-S3). Q5 B (5.1-S1/S3). Q6 A (3.1-K2/S1). Q7 D (3.3-S2/S3). Q8 B (3.4-S1/S2/S4). Q9 C (3.2-K3/S2). Q10 D (1.7-S3/S4). Q11 C (1.3-S3). Q12 A (1.2-K4). Q13 D (2.3-S3). Q14 B (5.6-K3/K4). Q15 C (2.1-S2). Q16 B (4.3-S4). Q17 A (4.4-K2/S2). Q18 D (4.5-K1/K2/S1). Q19 C (2.3-S5/4.3-S2). Q20 A (4.4-S4, 4.3-K3). The wrong-option explanations are also consistent with the guide. Letter spread counted: A = Q3, Q6, Q12, Q17, Q20 (5). B = Q1, Q5, Q8, Q14, Q16 (5). C = Q4, Q9, Q11, Q15, Q19 (5). D = Q2, Q7, Q10, Q13, Q18 (5). The claimed 5 each is confirmed. See "Not checked" for the research files. |
| 6 | Every concept tested is taught in the course (Modules 1-10) | PASS | All 20 tested concepts and the distractor concepts are taught. Q1 and Q4 in Module_2 lesson.md Lessons 1.5 and 1.4. Q2, Q13, Q15, Q19 in Module_3 Lessons 2.1-2.3. Q10, Q11, Q12 in Module_1 and Module_2 Lessons 1.2, 1.3, 1.7. Q6-Q9 in Module_4 Lessons 3.1-3.3 and Module_5 Lesson 3.4. Q16-Q20 in Module_6 fast-lesson 4.3 and Module_7 fast-lesson 4.4 and 4.5. Q3 and Q5 in Module_8 fast-lesson 5.2 and 5.1. Q14 in Module_10 fast-lesson 5.6. Distractor concepts (iteration caps, lost in the middle, "be conservative", strict schema covered as "schema fixes syntax, not correctness", keyword-sensitive prompts) are also taught. No tested concept is untaught. |

## Persisting issues

None (round 1).

## Not checked

- I did not read the five research files in runs/claude-certified-architect-foundations/research/ directly. Answer correctness was verified against the exam guide and domain-map.md, and the lessons (which carry the research forward) agree with every answer key. A conflict between a research file and the guide would not have been caught.
- Module_9 fast-lesson.md and the Modules 6-10 lesson.md files were not read, because no question tests 5.3 or 5.4. Modules 6-10 were checked through their fast-lessons only, which is the content the tutor teaches on the fast track.
- Observation only, not a failure: the Q9 answer text says allowed-tools "restricts which tools the skill may use". Module_4 lesson.md Lesson 3.2 says it pre-approves tools and "does not itself block other tools". The exam guide uses the word "restrict" (3.2-S3). The answer for Q9 (C) and the reason option B is wrong (it does not isolate output) are correct either way.
