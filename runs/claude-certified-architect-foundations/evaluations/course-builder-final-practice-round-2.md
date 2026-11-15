# Evaluation — course-builder final practice exam (context rework) — round 2

- Output evaluated: /home/user/claude-certified-architect-foundations/final-practice.md and /home/user/claude-certified-architect-foundations/final-practice-answers.md
- Checklist: course-builder "Done when" for final practice, items 1-8 as supplied by the orchestrator (items 6-8 per the brief rules B-C)
- Source of truth used: sources/exam-guide.txt, domain-map.md and the course lessons, as verified in round 1. Round-1 verdict and dispatch/fast-track-context-rework-brief.md read. This round I re-read both output files in full and re-checked all 20 keys against the guide's content as carried in domain-map.md and the lessons. No web fetch.
- Repeat round: yes (revision after a round-1 PASS)
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | 20 questions, 4 scenario headings, 5 each | PASS | Scenarios 1, 2, 3 and 6 with their exam-guide titles. Q1-5, Q6-10, Q11-15, Q16-20. |
| 2 | Domain mix 5/4/4/4/3 by tag | PASS | D1: Q1, Q4, Q10, Q11, Q12. D2: Q2, Q13, Q15, Q19. D3: Q6-Q9. D4: Q16, Q17, Q18, Q20. D5: Q3, Q5, Q14. The closing table in the answers file agrees. |
| 3 | A-D, one best answer, no answer text in final-practice.md | PASS | Every question has A-D. final-practice.md carries no answer letters or explanations. Each question has one defensible best answer. |
| 4 | Files match as sets; each answer has letter, why, why each wrong option fails, task ID | PASS | Q1-Q20 in both files, with identical task tags. Each answer has "Correct:", "Why:" and three wrong-option lines. Letter spread is A=5, B=5, C=5, D=5 (confirmed by count). |
| 5 | All 20 keys correct, re-verified after rewording | PASS | Re-checked each one. Q1 B (hook enforces policy deterministically). Q2 D (structured error that is non-retryable with a customer-facing explanation). Q3 A (explicit request for a human means hand over at once). Q4 C (structured handoff summary). Q5 B (case-facts block plus trimmed tool output). Q6 A. Q7 D (.claude/rules with paths glob). Q8 B. Q9 C (context: fork). Q10 D (resume and report the changed files). Q11 C (multiple Task calls in one reply). Q12 A (coordinator decomposition too narrow). Q13 D (scoped tools plus verify_fact). Q14 B (both values with dates). Q15 C (rename and rewrite the description). Q16 B (nullable or optional field). Q17 A (retry cannot supply information missing from the source). Q18 D (standard for the waiting customer, batches for the overnight job). Q19 C (tool_choice any). Q20 A (calculated_total beside stated_total). The rewording did not change which option is best in any question. |
| 6 | Every scenario and question setup says what the system is and what each piece of data means (rule B) | PASS | Each scenario intro defines the system, and each question restates its situation. The Q10 session, the Q18 two ways to send work, the Q19 tool_choice values, the Q20 stated_total and calculated_total, and the Q5 "40 fields, 5 matter" are all explained in the setup. |
| 7 | Every question states its deciding constraint as an explicit sentence (rule B) | PASS | All 20 questions carry a separate "Deciding constraint:" line (Q1 through Q20). |
| 8 | Every technical term explained in plain words on first appearance; no undefined jargon (rules B-C); list any term left unexplained | FAIL | Most terms are defined in place: hook, system prompt, tools, context, glob, skill, plan mode versus direct execution, resume and fork, context: fork, allowed-tools, subagent, coordinator, Task, schema, required and optional, null, retry, Message Batches API, and tool_choice with its three values. Terms left unexplained: (a) "strict schema checking" in Q20 option B is never defined. Only "schema" is defined, and "strict" is not explained. (b) "commands" and "personal commands folder" (~/.claude/commands/) in Q6 option C and Q9 option D. The Scenario 2 intro says "reusable commands" and never says what a command is. (c) Minor: "tool" is defined in Scenario 1 but not in Scenario 6, where Q17 option D ("forces Claude to call some tool") and Q19 use it. In Scenario 3, "tools" is not defined before its use in Q12, Q13 and Q15. Item (c) alone would not fail the item. (a) and (b) are concrete misses against "no undefined jargon". |

## Persisting issues

- Round 1 raised no failing issue. Round 1 did record an observation that the Q9 answer wording says allowed-tools "limits" or "restricts" which tools the skill may use, whereas Module_4 lesson.md says it pre-approves tools. The wording is still present in the Q9 setup and in the Q9 option B explanation. It does not change the key (C), so it is not a failure.
- The round-1 observation that the Q8 stem had no scenario detail is resolved. The setup now gives both tasks.

## Not checked

- The research files were not read, as in round 1. Keys were verified against the exam guide as carried in domain-map.md and the lessons.
- I did not re-read Module_9 fast-lesson.md, because no question tests 5.3 or 5.4.
