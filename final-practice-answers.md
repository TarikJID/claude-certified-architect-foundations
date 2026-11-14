# CCAR-F Final Practice Exam: ANSWERS

TUTOR: These are the answers. Never reveal them before the learner has attempted the question. Source for all facts: CCAR-F Exam Guide v1.0.

---

## Scenario 1: Customer Support Resolution Agent

### Question 1 [Task 1.5, Domain 1]
Correct: B
Why: A hook intercepting outgoing tool calls gives a deterministic guarantee; prompt instructions have a non-zero failure rate.
- A: Stronger prompt wording and few-shot examples remain probabilistic compliance.
- C: An iteration cap is not a policy control and does not stop a single large refund.
- D: Self-reported confidence is not a compliance mechanism and is unreliable.

### Question 2 [Task 2.2, Domain 2]
Correct: D
Why: Structured errors (isError, category, retryable flag, customer-friendly text) let the agent recover correctly and avoid wasted retries on a business-rule error.
- A: More retries waste attempts on a non-retryable policy violation.
- B: Returning an empty result as success silently suppresses the error.
- C: tool_choice "any" forces some tool call and does not address the error response.

### Question 3 [Task 5.2, Domain 5]
Correct: A
Why: An explicit request for a human is honored immediately, without investigating first.
- B: Investigating first ignores the explicit request.
- C: Offering resolution first applies to general frustration, not an explicit demand.
- D: Self-reported confidence is an unreliable proxy for when to escalate.

### Question 4 [Task 1.4, Domain 1]
Correct: C
Why: Human agents without the transcript need a structured summary: customer ID, root cause, refund amount, recommended action.
- A: One message lacks the root cause and the recommended action.
- B: A link and a sentiment note give no actionable detail.
- D: Raw dumps are verbose and omit the root cause and recommended action.

### Question 5 [Task 5.1, Domain 5]
Correct: B
Why: A persistent case-facts block preserves numbers and dates outside summarised history, and trimming verbose tool output stops irrelevant fields consuming context.
- A: Progressive summarisation is exactly what turns amounts and dates into vague prose.
- C: Content in the middle of long inputs is the most likely to be missed (lost in the middle).
- D: Complete conversation history must be passed to preserve coherence.

---

## Scenario 2: Code Generation with Claude Code

### Question 6 [Task 3.1, Domain 3]
Correct: A
Why: User-level ~/.claude/CLAUDE.md applies only to that user and is not shared by version control; project-level CLAUDE.md is shared.
- B: Manual copying is not shared configuration and will drift.
- C: ~/.claude/commands/ is user-scoped and personal, not shared.
- D: Duplicating into subdirectories is a manual workaround that does not fix the scoping problem.

### Question 7 [Task 3.3, Domain 3]
Correct: D
Why: Path-scoped rules in .claude/rules/ with a glob in the paths frontmatter load only when matching files are edited, regardless of directory.
- A: Directory-level CLAUDE.md files do not fit conventions spread across many directories.
- B: Always-loaded root content spends tokens on irrelevant context.
- C: A manually invoked skill is on-demand and easy to forget; it is not conditional loading.

### Question 8 [Task 3.4, Domain 3]
Correct: B
Why: Plan mode suits large multi-file or architectural work (then execute directly); direct execution suits a simple, well-scoped single-function change.
- A: Reverses the correct pairing.
- C: Skipping planning on a 45+ file migration risks costly rework.
- D: Plan mode on a one-function change is unnecessary overhead.

### Question 9 [Task 3.2, Domain 3]
Correct: C
Why: context: fork runs the skill in an isolated sub-agent context so verbose output does not pollute the main conversation.
- A: CLAUDE.md is always-loaded universal standards, which adds context instead of isolating it.
- B: allowed-tools restricts which tools the skill may use; it does not isolate output.
- D: Moving it to a personal commands folder removes it from the team and does not isolate output.

### Question 10 [Task 1.7, Domain 1]
Correct: D
Why: When prior context is mostly valid, resume by name and inform the session of specific file changes for targeted re-analysis.
- A: Full re-exploration is only needed when prior results are largely stale.
- B: fork_session creates independent branches to explore different approaches; it does not refresh file contents.
- C: Resuming without telling it about changes risks acting on stale results.

---

## Scenario 3: Multi-Agent Research System

### Question 11 [Task 1.3, Domain 1]
Correct: C
Why: Parallel subagents come from multiple Task tool calls emitted in one coordinator response rather than across separate turns.
- A: Direct subagent-to-subagent messaging breaks hub-and-spoke routing through the coordinator.
- B: More iterations do not make work parallel.
- D: Merging removes specialisation and does not address sequential spawning.

### Question 12 [Task 1.2, Domain 1]
Correct: A
Why: Subagents did their assigned work, so the narrow decomposition by the coordinator caused the incomplete coverage.
- B: Subagents completed their tasks well; tool descriptions are not implicated.
- C: Nothing in the scenario shows synthesis dropped content; the missing subtopics were never assigned.
- D: Tool count is unrelated to missing subtopics.

### Question 13 [Task 2.3, Domain 2]
Correct: D
Why: Scoped tool access with a limited cross-role tool for a high-frequency need (verify_fact), with complex cases routed via the coordinator.
- A: Too many or out-of-role tools degrades selection and encourages misuse.
- B: Prompt-only restriction is weaker than removing the tools.
- C: Removing the synthesis role does not fix the design.

### Question 14 [Task 5.6, Domain 5]
Correct: B
Why: Conflicting statistics are annotated with source attribution, and dates prevent temporal differences being read as contradictions.
- A: Arbitrarily selecting one value is the anti-pattern.
- C: Averaging fabricates a figure neither source reported.
- D: Dropping credible data loses information; conflicts should be annotated, not hidden.

### Question 15 [Task 2.1, Domain 2]
Correct: C
Why: Renaming and rewriting the description to remove functional overlap (e.g. extract_web_results) is the guide's recommended fix.
- A: Keyword-sensitive prompt rules can create unintended tool associations.
- B: Forcing one tool stops the other being used at all.
- D: max_tokens does not clarify overlapping descriptions.

---

## Scenario 6: Structured Data Extraction

### Question 16 [Task 4.3, Domain 4]
Correct: B
Why: Optional (nullable) fields stop the model fabricating values to satisfy required fields when the source lacks the data.
- A: Retrying does not give the document information it does not contain.
- C: General instructions such as "be conservative" do not improve precision.
- D: A longer description still forces a value for a required field.

### Question 17 [Task 4.4, Domain 4]
Correct: A
Why: Retries fail when the information is absent from the provided source; they help with format or structural errors.
- B: Repeating retries cannot create information absent from the source.
- C: Forceful wording will not surface missing data and risks fabrication.
- D: tool_choice "any" controls whether a tool is called, not where data comes from.

### Question 18 [Task 4.5, Domain 4]
Correct: D
Why: Batches suit latency-tolerant overnight work (50% savings, up to 24 hours, no latency SLA); a waiting user needs the synchronous API.
- A: Batch has no guaranteed latency, which is unsuitable for a waiting user.
- B: Synchronous for the backfill forgoes the 50% saving.
- C: Reverses the correct pairing.

### Question 19 [Task 2.3, Domain 2]
Correct: C
Why: tool_choice "any" guarantees a tool is called while letting the model pick the right extraction schema when document type is unknown.
- A: "auto" allows conversational text instead of a tool call.
- B: Forcing the invoice tool would apply the wrong schema to receipts and contracts.
- D: Parsing text with a regex discards the reliability of tool use with JSON schemas.

### Question 20 [Task 4.4, Domain 4]
Correct: A
Why: Line items not summing to the total is a semantic error; extracting calculated_total next to stated_total flags the discrepancy.
- B: Strict schemas eliminate syntax errors, not semantic ones.
- C: Prose output removes schema validation and makes downstream checks harder.
- D: More required fields can encourage fabrication and do not check sums.

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
