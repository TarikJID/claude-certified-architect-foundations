# Module 9 MCQ (fast track)

Pick the one best answer. Answers are in `mcq-answers.md`. Do not open it before attempting.

---

## Task statement 5.3

**Q1 [5.3]** A coordinator runs a documentation subagent. The subagent searches an internal knowledge base. The search times out after 30 seconds, but 2 of roughly 5 relevant documents were already retrieved. What should the subagent send back to the coordinator?

A. A short message saying "search failed."
B. The failure type (timeout), the query it attempted, the 2 documents already found, and alternatives such as a narrower query or the public help center.
C. The 2 documents, presented as the complete result so the coordinator can continue.
D. An empty list marked as success, so the coordinator does not stall.

**Q2 [5.3]** A customer-lookup subagent runs twice for the same customer email. In run 1 the database call times out. In run 2 the call completes normally and finds no account for that email. The coordinator must decide which run is worth retrying. How should the subagent report them?

A. Both as "no results," because in both cases the coordinator received no account.
B. Both as "error," to be safe.
C. Run 1 as an empty successful result, and run 2 as an error.
D. Run 1 as an access failure (timeout), and run 2 as a success with zero matches.

**Q3 [5.3]** In a research workflow, four subagents run in parallel. Three return findings. The fourth, which gathers market data, cannot reach its data source. What should happen next?

A. The coordinator continues, builds the report from the three findings, and states clearly that market data is unavailable.
B. The coordinator stops the whole workflow and returns an error to the user.
C. The coordinator adds a market data section marked "no data found," so the report looks complete.
D. The coordinator discards all four results and reruns every subagent until all four succeed.

**Q4 [5.3]** A search subagent gets a connection error on its first query. Such errors are usually brief network glitches. Which design is best?

A. Immediately send "search unavailable" to the coordinator so it can decide.
B. Return an empty result as a success so the coordinator is not interrupted.
C. Retry with backoff and try a narrower query. If those also fail, send the coordinator what was attempted plus any partial results.
D. Wait for the coordinator to tell it to retry, because only the coordinator may recover from errors.

**Q5 [5.3]** A synthesis agent combines output from five subagents. The pricing and competitor findings each have several independent sources. The regulatory subagent failed because its source was unreachable. Which final report is best?

A. A uniformly confident report that leaves out regulatory topics without comment.
B. A report that marks pricing and competitor findings as well supported and states that regulatory information could not be retrieved.
C. A report that fills the regulatory section from general industry knowledge, written in the same tone as the rest.
D. No report at all, because one topic is missing.

---

## Task statement 5.4

**Q1 [5.4]** A developer has explored a large repository for 40 tool calls in one session. Asked whether the RefundProcessor class checks currency codes, a class it read earlier, the model replies with a general statement about how refund processors "typically" handle currency. What is the best interpretation and response?

A. The model lacks knowledge of refund code, so add more documentation to the prompt.
B. The earlier tool results were wrong, so rerun every search.
C. The session is degrading, so keep key findings in a scratchpad file that is re-read for later questions, or start a fresh session or subagent for the next task.
D. The RefundProcessor class has a bug, so file an issue.

**Q2 [5.4]** The main agent must find every place a class is instantiated across hundreds of files. The developer wants the main agent's context kept for high-level planning. Which approach is best?

A. Spawn a subagent for that narrow question and have it return a short summary of the call sites.
B. Have the main agent run all the searches itself so it sees every result.
C. Have the main agent read every file in the repository first, then answer.
D. Ask the user to list the call sites.

**Q3 [5.4]** Midway through a long exploration of the same task, the session context is filling with verbose file listings and search output. The developer still needs what was learned about the refund flow. What is the best action?

A. Wait for automatic compaction, since it always keeps the important details.
B. Start a brand new session and discard everything learned.
C. Delete the project CLAUDE.md to free up space.
D. Run `/compact` before context is full, with an instruction to keep the refund-flow findings and drop the file listings.

**Q4 [5.4]** A lead agent coordinates several subagents that explore a monorepo for hours. The process crashes. The team wants to resume without re-running subagents that already finished. Which design supports this?

A. Keep all agent state only in the lead agent's context window.
B. Each subagent exports its state to a known location. On resume, the coordinator loads a manifest of those exports and injects the state into agent prompts.
C. Restart from scratch each time, since reruns are simple.
D. Rely on automatic compaction to preserve each subagent's progress.

**Q5 [5.4]** Phase 1 of an exploration mapped a codebase's module structure and produced a very long transcript. Phase 2 will spawn new subagents to trace the refund flow. Phase 2 subagents do not see the main conversation. How should the coordinator start them?

A. Paste the complete phase 1 transcript into each subagent's prompt.
B. Give them only the task, with no phase 1 information.
C. Summarize the key phase 1 findings and put that summary in each subagent's initial context.
D. Assume they inherit the phase 1 history automatically, and give them only the task.
