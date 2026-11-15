# CCAR-F Final Practice Exam: ANSWERS

TUTOR: These are the answers. Record the learner's attempt before opening this file, and never reveal an answer before that. All facts come from the CCAR-F Exam Guide v1.0.

---

## Scenario 1: Customer Support Resolution Agent

### Question 1 [Task 1.5, Domain 1]
Correct: B
Why: A hook is code, so it blocks every refund above $500 every time; a rule written in the instructions is usually followed but can still be missed.
- A: Louder wording and examples are still instructions, so the agent can still miss them now and then.
- C: Fewer steps does not stop one large refund from going through.
- D: The agent rating its own confidence is unreliable and is not a policy check.

### Question 2 [Task 2.2, Domain 2]
Correct: D
Why: A clearly marked error that names its kind, says retrying is pointless and carries a plain explanation lets the agent stop retrying and tell the customer why.
- A: More retries just waste attempts on a refusal that can never succeed.
- B: Pretending the failure was a success hides the error from the agent and the customer.
- C: Forcing a tool call on every turn does nothing to explain the refusal.

### Question 3 [Task 5.2, Domain 5]
Correct: A
Why: When a customer explicitly asks for a human, the agent hands over at once, without investigating first.
- B: Investigating first ignores what the customer clearly asked for.
- C: Offering to help first is right when a customer is frustrated but has not asked for a human; here they asked.
- D: The agent's rating of its own confidence is not a reliable signal for when to hand over.

### Question 4 [Task 1.4, Domain 1]
Correct: C
Why: The human cannot see the chat, so they need a structured summary: customer ID, root cause, refund amount and recommended action.
- A: One message leaves out the root cause and what to do next.
- B: A link and a note about mood give the human nothing to act on.
- D: Raw tool replies are long and still do not state the root cause or the next action.

### Question 5 [Task 5.1, Domain 5]
Correct: B
Why: A case-facts block sent in full every time keeps exact amounts and dates safe, and cutting lookups to the relevant fields stops clutter filling the agent's memory.
- A: Repeated short summaries are exactly how exact numbers and dates turn into vague words.
- C: Claude is most likely to miss information placed in the middle of long input.
- D: Without the full conversation, the agent loses track of what was already said.

---

## Scenario 2: Code Generation with Claude Code

### Question 6 [Task 3.1, Domain 3]
Correct: A
Why: The personal file applies only to its owner; the project-level CLAUDE.md is shared with everyone through version control.
- B: Hand copying is not shared, and the copies will drift apart over time.
- C: The personal commands folder is also personal, not shared.
- D: Copies in every folder are a manual workaround; the problem is that the rules sit in a personal file.

### Question 7 [Task 3.3, Domain 3]
Correct: D
Why: A rule file in .claude/rules/ with the pattern in its "paths" field loads only when a matching file is edited, whatever folder that file is in.
- A: Per-folder files do not suit files scattered across dozens of folders.
- B: The main CLAUDE.md is always loaded, so the rule would waste memory when nobody is editing tests.
- C: A skill only runs when someone starts it by hand, so it is easy to forget and does not load automatically.

### Question 8 [Task 3.4, Domain 3]
Correct: B
Why: A 45-file library switch is large, so plan it first and then carry out the plan; a single date check is small and clear, so just do it.
- A: This is the right pairing reversed.
- C: Skipping the plan on a 45-file change risks costly rework.
- D: Planning a one-line change is wasted effort.

### Question 9 [Task 3.2, Domain 3]
Correct: C
Why: "context: fork" runs the skill in its own side conversation, so its long output stays out of the main one.
- A: CLAUDE.md is always loaded, which adds clutter instead of removing it.
- B: "allowed-tools" limits which tools the skill can use; it does nothing about where the output goes.
- D: Moving it to personal folders takes it away from the team and still floods the conversation.

### Question 10 [Task 1.7, Domain 1]
Correct: D
Why: When most of the earlier work is still valid, reopen the session and tell it exactly which files changed, so it re-checks only those.
- A: Starting over is only worth it when most of the earlier results are out of date.
- B: Forking makes a separate copy to try a different approach; it does not reload changed files.
- C: Without being told, the session may keep working from old versions of the files.

---

## Scenario 3: Multi-Agent Research System

### Question 11 [Task 1.3, Domain 1]
Correct: C
Why: Subagents run in parallel when the coordinator issues all their Task calls in the same reply, instead of one per reply.
- A: Subagents talking directly bypasses the coordinator, which is meant to route all communication.
- B: More steps do not make the two jobs run at the same time.
- D: Merging loses the specialists and still does not run anything in parallel.

### Question 12 [Task 1.2, Domain 1]
Correct: A
Why: The subagents did their parts well, so the gap comes from the coordinator splitting the topic too narrowly.
- B: The subagents completed their tasks, so their tools were not the problem.
- C: Nothing shows sections were dropped; music, writing and film were never assigned.
- D: Tool count has nothing to do with topics that were never assigned.

### Question 13 [Task 2.3, Domain 2]
Correct: D
Why: Give each agent only the tools its role needs, plus a narrow tool for a frequent need like fact checks, and send bigger requests back through the coordinator.
- A: Too many tools, or tools outside an agent's role, make it pick wrongly and misuse them.
- B: An instruction alone is weaker than simply not giving it the tool.
- C: Removing the role does not fix the tool design.

### Question 14 [Task 5.6, Domain 5]
Correct: B
Why: When credible sources disagree, show both figures with their sources, and include dates so a change over time is not mistaken for a contradiction.
- A: Picking one figure to suit the story is exactly what to avoid.
- C: An average is a number neither source reported.
- D: Dropping credible data loses information; the disagreement should be shown, not hidden.

### Question 15 [Task 2.1, Domain 2]
Correct: C
Why: Renaming the overlapping tool and rewriting its description to state its purpose, input and limits lets the agent tell the two apart.
- A: A rule triggered by one word can push requests to the wrong tool.
- B: Forcing one tool means the other is never used.
- D: Longer replies do not make two near-identical descriptions any clearer.

---

## Scenario 6: Structured Data Extraction

### Question 16 [Task 4.3, Domain 4]
Correct: B
Why: An optional field that can be empty lets Claude say "no value" instead of inventing one to fill a required field.
- A: Retrying cannot produce a number the invoice does not contain.
- C: Vague instructions like "be conservative" do not make the output more accurate.
- D: A longer description still forces Claude to fill the field with something.

### Question 17 [Task 4.4, Domain 4]
Correct: A
Why: Retrying helps fix format or structure mistakes, but cannot produce information that is not in what Claude was given.
- B: Repetition cannot create a missing value.
- C: Forceful wording will not find missing data and makes an invented value more likely.
- D: Forcing a tool call controls whether a tool is used, not where the data comes from.

### Question 18 [Task 4.5, Domain 4]
Correct: D
Why: Batches suit work that can wait (50% cheaper, results within 24 hours, no promise of speed); a person waiting on screen needs the standard way.
- A: Batches give no promise of speed, so the waiting customer could wait for hours.
- B: Using the standard way overnight gives up the 50% saving for no benefit.
- C: This is the right pairing reversed.

### Question 19 [Task 2.3, Domain 2]
Correct: C
Why: "any" makes Claude always call a tool while still letting it pick the right form for an unknown document type.
- A: "auto" still allows a plain-text reply, which is the current problem.
- B: Forcing the invoice tool would put receipts and contracts on the wrong form.
- D: Pulling values out of plain text loses the reliability of having Claude fill a defined form.

### Question 20 [Task 4.4, Domain 4]
Correct: A
Why: Numbers that do not add up are a meaning error the schema check cannot see; filling in calculated_total next to stated_total exposes the mismatch.
- B: Strict checking catches badly formed output, not numbers that disagree.
- C: Prose removes the form check entirely and makes later checks harder.
- D: More required fields can push Claude to invent values and still check no sums.

---

## Closing table

| Domain | Weight | Target | Questions | Question numbers |
|---|---|---|---|---|
| 1. Agentic Architecture & Orchestration | 27% | ~5 | 5 | Q1, Q4, Q10, Q11, Q12 |
| 2. Tool Design & MCP Integration | 18% | ~4 | 4 | Q2, Q13, Q15, Q19 |
| 3. Claude Code Configuration & Workflows | 20% | ~4 | 4 | Q6, Q7, Q8, Q9 |
| 4. Prompt Engineering & Structured Output | 20% | ~4 | 4 | Q16, Q17, Q18, Q20 |
| 5. Context Management & Reliability | 15% | ~3 | 3 | Q3, Q5, Q14 |
| Total | 100% | 20 | 20 | |

Correct-letter distribution: A = 5, B = 5, C = 5, D = 5.
