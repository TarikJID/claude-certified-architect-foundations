# Module 9 Fast Lesson

## 5.3 Error propagation across multi-agent systems

Exam rule: A failing subagent tells the coordinator what happened, in structured form. The coordinator then adapts. Nothing is hidden and nothing is stopped.

- Pick: an error that carries failure type, what was tried, partial results, and alternatives.
- Pick: a timeout (access failure) reported differently from a finished query with zero matches (valid empty result). Only the timeout is worth retrying.
- Pick: the subagent retries or uses a fallback first. It escalates only if that fails, and then includes what it tried and partial results.
- Pick: a final report with coverage notes. Say which findings are well supported and which topics have gaps.
- Reject: generic "search unavailable"; an empty result returned as success (silent suppression); stopping the whole workflow because one subagent failed.
- Trap: "return an empty list so the pipeline keeps running" sounds tidy but hides the failure.

Example: Three of four subagents succeed and market data is down. Report the three findings plus "market data unavailable."

## 5.4 Context in large codebase exploration

Exam rule: Long sessions degrade, so keep verbose exploration out of the main agent and keep key findings outside the context window.

- Symptom: the model says what classes "typically" do instead of naming what it actually found earlier. Fix: write findings to a scratchpad file, or start a fresh session or subagent.
- Pick: a subagent for a narrow question (such as "find all test files"). It returns only a short summary.
- Pick: summarize one phase and inject that summary into the next phase's subagents. Reject passing the full transcript or passing nothing.
- Pick: each agent exports state to a known place. The coordinator loads a manifest on resume. This is crash recovery.
- Pick: `/compact` (with an instruction on what to keep) when context fills with discovery output. Use it before context is full.
- Trap: "just read every file upfront" or "keep everything in the main context."

Example: Phase 1 maps modules. A five-bullet summary goes to the phase 2 subagents that trace the refund flow.
