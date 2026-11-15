# Evaluation — course-builder fast-track Module 7 (4.4, 4.5, 4.6), context rework — round 5

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_7_Extraction_Quality_Batching_and_Review_Architectures/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: the 8-item checklist given for this round (unchanged from round 4). Items 2, 6, 7, 8 measured against runs/claude-certified-architect-foundations/dispatch/fast-track-context-rework-brief.md.
- Source of truth used: all three output files read in full; sources/exam-guide.txt lines 606-669 (4.4-4.6) re-read this round; the round-4 verdict and the brief. Bullet-ID totals and research-file checks rely on the round-4 verification (22 bullets), re-confirmed here against the exam guide text. No web fetch.
- Repeat round: yes
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | All 4.4/4.5/4.6 bullet IDs taught and tested; totals | PASS | 22 bullets (4.4: 8, 4.5: 8, 4.6: 6). "Tests:" lines cover 4.4 K1-K4 and S1-S4 (Q1: K1,S1; Q2: K2,S2; Q3: K4,S4; Q4: K3,S3; Q5: S4,K2), 4.5 K1-K4 and S1-S4 (Q1: K1,K2,S1; Q2: K3; Q3: K4,S3; Q4: S2,K1; Q5: S4), 4.6 K1-K3 and S1-S3 (Q1: K1; Q2: K2,S1; Q3: K3,S2; Q4: S3; Q5: K3,S2). 22 of 22 tested. 4.4 is still taught in full: K1/S1 in the Before/After and Exam rule ("Retry with the specific error"); K2/S2 in bullet 2; K4 in bullet 3; S4 in bullet 4; K3/S3 in bullet 5. 4.5 and 4.6 are taught as in round 4. |
| 2 | Blocks follow rule A; ~220 words | PASS | Each block has Setting, Before/After, Exam rule and 5 bullets. Setting sentences: 4.4 = 3 (the round-4 failure of 5 is fixed), 4.5 = 3, 4.6 = 3. Exact word counts including the heading: 4.4 = 211, 4.5 = 213, 4.6 = 214. No overrun. Side scenarios (code-review bot, merge check) carry their own one-line setting. Traps say what they look like and why they fail (e.g. "bare 'try again' gives Claude nothing to fix"; "one giant pass ... flags a pattern in file 3, accepts it in file 17"). |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, no answer text | PASS | 5 + 5 + 5 = 15 questions, each tagged [4.x] with options A-D. No answers in the file. Key positions: 4.4 B D A C B; 4.5 C A D B C; 4.6 D B A C D. |
| 4 | Sets match; answer format | PASS | 15 questions in mcq.md and 15 answers in mcq-answers.md (Q4.4-1..5, Q4.5-1..5, Q4.6-1..5), matched one to one. Each answer has "Correct: X", a Why line, three wrong-option lines and a Tests line with bullet IDs. |
| 5 | Answer keys correct; re-check Q4.5-1, Q4.6-1, Q4.6-4 (and Q4.5-4 arithmetic) | PASS | All keys fit the guide. 4.4-1 B (guide 622-623). 4.4-2 D (624-625; forcing a value invites invention). 4.4-3 A (628-629; tool use removes syntax errors only, 618-619). 4.4-4 C (616-617, 626-627). 4.4-5 B (629). 4.5-1 C (636-638, 644-645). 4.5-2 A (639-640). 4.5-3 D (648-649). 4.5-4 B: 4+24=28, the others give 48, 36 and 54, so only B meets 30 (646-647). 4.5-5 C (650). 4.6-1 D (655-656). 4.6-2 B (657-658). 4.6-3 A (659-660, 665-666). 4.6-4 C: confidence score used for routing (667-668); D (the writer scores its own work) and A (silent deletion) fail. 4.6-5 D (665-666). The reworded Q4.5-1, Q4.6-1 and Q4.6-4 each keep one defensible answer. |
| 6 | Setups say plainly what the system is and what each piece of data means | PASS | Examples: invoices and form fields (Q4.4-1); due date and PO-77 "never sent to Claude" (Q4.4-2); code-review bot and "dismiss (reject)" (Q4.4-4); "custom_id, a unique label the team chose" (Q4.5-3); the sync and batch definitions repeated in Q4.5-1; "session" in Q4.6-1; "pass" in Q4.6-3; "confidence score means how sure the checker is that a comment points to a real problem" (Q4.6-4). |
| 7 | Deciding constraint stated as an explicit sentence | PASS | All 15 questions contain a sentence beginning "Deciding constraint:", each a full sentence stating the deciding fact. |
| 8 | Technical terms explained on first appearance; round-4 terms | PASS | Round-4 terms are all fixed. "Merge button" is glossed "(which adds his change to the main code)" in the lesson (4.5 bullet 1) and in Q4.5-1. "Confidence score" is glossed "how sure it is the problem is real" (4.6 bullet 5) and in Q4.6-4. "Finding" is glossed "(reported problem)" (lesson) and "(reported problems)" (Q4.6-1 option A). "Bot" is glossed "(a program where Claude comments on code automatically)" (4.4 bullet 5) and in Q4.4-4. "Local bugs" is replaced by "bugs inside that file". "Prompt" is glossed "(Claude's written instructions)". "API" is covered by "(Claude's bulk service)". Also glossed: extraction, schema, validation, tool use, synchronous, batch, custom_id, session, instance, pull request, pass, extended thinking, stated_total, calculated_total. Minor leftovers, none load-bearing or unexplained to the point of blocking: "30-hour promise" in the lesson is clarified fully in Q4.5-4; "the checker" in 4.6 bullet 5 is plain English. No other unexplained jargon found. |

## Persisting issues

None. The round-4 failures (4.4 Setting at 5 sentences; unexplained merge button, confidence score, finding, bot, local bugs, prompt, API) are all resolved. Earlier issues (bullet counts above 5, rounds 1-2) remain resolved: every block has 5 bullets.

## Not checked

- Word counts are my own manual counts (hyphenated and inline-code tokens counted as one word). All three blocks are at least 6 words under 220, so counting conventions do not change the result.
- I did not re-open domain-map.md or the research file this round. I relied on the round-4 verification of the 22 bullets and re-checked every answer key against the exam guide text.
