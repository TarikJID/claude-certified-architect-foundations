# Evaluation — course-builder final practice exam (context rework) — round 3

- Output evaluated: /home/user/claude-certified-architect-foundations/final-practice.md and /home/user/claude-certified-architect-foundations/final-practice-answers.md
- Checklist: course-builder "Done when" for final practice, items 1-8 (unchanged from round 2)
- Source of truth used: runs/claude-certified-architect-foundations/domain-map.md (read in full this round; it carries the exam guide bullets verbatim by ID). Round-1 and round-2 verdicts and dispatch/fast-track-context-rework-brief.md read. No web fetch.
- Repeat round: yes (round 2 was REWORK on item 8)
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | 20 questions under 4 scenario headings from the exam guide, 5 per scenario | PASS | Scenarios 1, 2, 3 and 6 (titles as verified in round 1). Q1-5, Q6-10, Q11-15, Q16-20. |
| 2 | Domain mix D1=5, D2=4, D3=4, D4=4, D5=3 by task tags | PASS | D1: Q1, Q4, Q10, Q11, Q12. D2: Q2, Q13, Q15, Q19. D3: Q6-Q9. D4: Q16, Q17, Q18, Q20. D5: Q3, Q5, Q14. The closing table agrees. |
| 3 | A-D, exactly one best answer, no answer text in final-practice.md | PASS | All questions have A-D. final-practice.md has no answer letters or explanations. One defensible best answer each. |
| 4 | Files match as sets; each answer has letter, why, why each wrong option fails, task ID | PASS | Q1-Q20 in both files, tags identical. Each entry has Correct, Why and three wrong-option lines. Letter spread counted: A = Q3, Q6, Q12, Q17, Q20; B = Q1, Q5, Q8, Q14, Q16; C = Q4, Q9, Q11, Q15, Q19; D = Q2, Q7, Q10, Q13, Q18 (5 each). |
| 5 | Every answer key correct (re-check Q6, Q9, Q20 and Scenario 2/3/6 setups) | PASS | Q6 A matches 3.1-K2/S1 (user-level file is not shared via version control; move to project-level). Q9 C matches 3.2-K3/S2 (context: fork isolates verbose output); B's "limits which tools" matches 3.2-S3 "restrict tool access". Q20 A matches 4.4-S4 (calculated_total beside stated_total); B is wrong per 4.3-K3 (strict schemas stop syntax errors, not semantic ones). Others re-checked against the map: Q1 B 1.5-S2; Q2 D 2.2-S2; Q3 A 5.2-S2; Q4 C 1.4-S3; Q5 B 5.1-S1/S3; Q7 D 3.3-S2/S3; Q8 B 3.4-S4; Q10 D 1.7-S4; Q11 C 1.3-S3; Q12 A 1.2-K4; Q13 D 2.3-S3; Q14 B 5.6-K3/K4; Q15 C 2.1-S2; Q16 B 4.3-S4; Q17 A 4.4-K2/S2; Q18 D 4.5-S1; Q19 C 2.3-S5/4.3-S2. The reworded Scenario 2, 3 and 6 setups do not change which option is best. |
| 6 | Every scenario and question setup says plainly what the system is and what each piece of data means | PASS | Each scenario intro defines its system. Question setups define their own data: Q5 context and the 40 versus 5 fields, Q10 session/resume/fork, Q18 the two ways to send work, Q19 the tool_choice values, Q20 stated_total and calculated_total. |
| 7 | Every question states its deciding constraint as an explicit sentence | PASS | All of Q1-Q20 carry a separate "Deciding constraint:" line. |
| 8 | Every technical term explained in plain words on first appearance (round 2 misses: strict schema checking, commands / personal commands folder, "tool" in Scenarios 3 and 6) | PASS | "Strict schema checking" is now defined in Q20 B ("a stricter mode that guarantees the filled form is always well formed, with every field present and of the right type"). "Command" is defined in the Scenario 2 intro (a saved set of instructions run by typing a slash and its name), as are the shared .claude/commands/ and personal ~/.claude/commands/ folders, which covers Q6 C and Q9 D. "Tool" is defined in the Scenario 3 intro ("functions it can call, such as one that runs a web search") and in the Scenario 6 intro ("a tool, a function it can call whose input is the form"). Other terms are defined in place: hook, system prompt, context, glob, skill, SKILL.md header settings, plan mode versus direct execution, library, session, resume and fork, subagent, coordinator, Task, schema, required and optional, null, retry, Message Batches API, tool_choice values, repository and version control. Minor non-failing observations: "header" and "paths" field in Q7 D are described in context but not formally defined; "root cause" (Q4, Q12) is plain-English. None is jargon a non-technical reader is blocked by. |

## Persisting issues

None. The round-2 failures on item 8 (strict schema checking; commands and personal commands folder; undefined "tool" in Scenarios 3 and 6) are all resolved. The round-1 observation about "allowed-tools" wording in Q9 remains. It matches the exam guide's "restrict" wording (3.2-S3) and does not affect the key.

## Not checked

- I did not re-fetch sources/exam-guide.txt directly. Keys were checked against domain-map.md, which transcribes the guide's bullets by ID. Scenario titles rely on round 1's direct check against the guide.
- Course lessons and research files were not re-read this round, because the key checks were done against the domain map and round 2 found no key changes.
