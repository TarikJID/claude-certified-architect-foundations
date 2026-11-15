# Module 9 MCQ (fast track)

Pick the one best answer. Answers are in `mcq-answers.md`. Do not open it before attempting.

---

## Task statement 5.3

**Q1 [5.3]** A research system has a coordinator agent (the agent that hands out work and writes the final report) and several subagents (helper agents that each search one place). One subagent searches the company's internal help articles. Its search stopped after 30 seconds because the server never replied (a timeout). Before that, it had already found 2 of about 5 relevant articles. The deciding constraint: the coordinator can only choose its next step from what this subagent sends back. What should the subagent send?

A. Only the message "search failed."
B. That it was a timeout, what it searched for, the 2 articles it found, and other options such as a narrower search or the public help site.
C. The 2 articles, presented as the full result.
D. An empty list marked as a successful search, so the coordinator is not held up.

**Q2 [5.3]** In a customer support system, a lookup subagent searches the customer database by email address. Run 1: the database did not answer in time (a timeout), so the search never actually happened. Run 2: the database answered normally and had no account with that email. The deciding constraint: the coordinator retries only searches that might give a different answer on a second try. How should the subagent report the two runs?

A. Both as "no results," since neither run returned an account.
B. Both as "error," to be safe.
C. Run 1 as "search worked, zero matches", and run 2 as "could not reach the database".
D. Run 1 as "could not reach the database (timeout)", and run 2 as "search worked, zero matches".

**Q3 [5.3]** A coordinator agent sends four subagents (helper agents) to research a market at the same time. Three return their findings. The fourth, which collects market prices, cannot reach its data source. The deciding constraint: the user needs a report today, and it must be honest about what is missing. What should happen next?

A. The coordinator writes the report from the three findings and states clearly that market price data is unavailable.
B. The coordinator stops the whole job and shows the user an error.
C. The coordinator adds a market price section saying "no data found", so the report looks complete.
D. The coordinator throws away all four results and reruns every subagent until all four succeed.

**Q4 [5.3]** In a research system, a search subagent's first attempt fails with a connection error (the network link dropped for a moment). Errors like this usually clear up within seconds. The deciding constraint: the coordinator agent (the manager of the subagents) should only hear about problems the subagent could not fix by itself. Which design is best?

A. Immediately send "search unavailable" to the coordinator.
B. Report the failed search as a successful search with no results, so the coordinator is not interrupted.
C. Retry after a short wait, then try a narrower search. If both fail, tell the coordinator what it tried and anything it found.
D. Do nothing until the coordinator tells it to retry.

**Q5 [5.3]** A writer agent combines results from five subagents into one research report. The pricing and competitor findings each come from several independent sources. The subagent covering regulations (government rules for the industry) failed because its source could not be reached. The deciding constraint: readers must be able to tell which parts of the report they can rely on. Which report is best?

A. A report written in the same confident tone throughout that leaves out regulations without comment.
B. A report that marks pricing and competitor findings as well supported and states that regulatory information could not be retrieved.
C. A report that fills the regulations section from general industry knowledge, in the same tone as the rest.
D. No report at all, because one topic is missing.

---

## Task statement 5.4

**Q1 [5.4]** An engineer uses an agent to explore a large codebase (all the program files of a project). Forty steps into one long session, she asks whether the RefundProcessor part of the code checks currency codes. The agent opened that file earlier, but now replies with how such code "typically" works instead of what it found. The deciding constraint: for the rest of this long project she needs answers based on what the agent actually found. What is the best interpretation and response?

A. The agent knows nothing about refund code, so add more documentation to its instructions.
B. The earlier searches were wrong, so rerun every search.
C. The long session is blurring earlier findings, so save key findings in a notes file the agent re-reads, or start a fresh session for the next task.
D. The RefundProcessor code has a bug, so report it.

**Q2 [5.4]** An agent must find every place in hundreds of files where one piece of code (RefundProcessor) is used. The search output will be very long. A subagent is a helper agent with its own separate working memory, which reports back to the main agent. The deciding constraint: the main agent's context (the text it can hold in view at once) must stay free for planning the overall work. Which approach is best?

A. Send a subagent to answer just that question and return a short summary of where the code is used.
B. Have the main agent run all the searches itself so it sees every result.
C. Have the main agent open every file in the project first, then answer.
D. Ask the engineer to list the places by hand.

**Q3 [5.4]** Midway through a long codebase exploration, the agent's context (the text it can hold in view at once) is filling with long file lists and search output. `/compact` is a command that replaces the conversation so far with a summary, and you can tell it what to keep. Automatic compaction does the same on its own, but only when the context is nearly full, and without your instructions. The deciding constraint: what the agent learned about the refund flow (how refunds move through the code) must survive. What is the best action?

A. Wait for automatic compaction, since it will keep the important details.
B. Start a brand new session and discard everything learned.
C. Delete the project's CLAUDE.md file (the file of team instructions the agent reads) to free up space.
D. Run `/compact` now, telling it to keep the refund-flow findings and drop the file lists.

**Q4 [5.4]** A lead agent runs several subagents (helper agents) that explore a very large codebase for hours. Midway, the program crashes, and everything held only in the agents' working memory is lost. The deciding constraint: on restart, subagents that already finished must not be run again. Which design supports this?

A. Keep all progress only in the lead agent's working memory.
B. Each subagent saves its progress to a file in a known place. On restart, the lead agent reads a manifest (a list of those saved files) and puts that progress back into each agent's instructions.
C. Restart everything from scratch each time.
D. Rely on automatic compaction (the agent summarizing its own conversation when it gets full) to keep the progress.

**Q5 [5.4]** Phase 1 of exploring a codebase mapped how its parts are organized and produced a very long record of every step. Phase 2 will start new subagents (helper agents) to trace how refunds move through the code. New subagents start blank: they see nothing from the main conversation unless it is put in their starting instructions. The deciding constraint: phase 2 needs what phase 1 learned, without being flooded by it. How should the lead agent start them?

A. Paste the full phase 1 record into each subagent's instructions.
B. Give them only the task, with no phase 1 information.
C. Summarize the key phase 1 findings and put that summary in each subagent's starting instructions.
D. Give them only the task, because they will see the phase 1 work automatically.
