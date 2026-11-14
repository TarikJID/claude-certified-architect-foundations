# Module 9 Fast Lesson

## 5.3 Error propagation across multi-agent systems

Exam rule: A failing subagent tells the coordinator what happened, in structured form. The coordinator then adapts; nothing is hidden, nothing is stopped.

- Pick: an error with failure type, what was tried, partial results, and alternatives.
- Pick: timeout (access failure) reported differently from zero matches (valid empty result). Only the timeout is worth retrying.
- Pick: subagent retries or uses a fallback first, then escalates with what it tried and partial results.
- Pick: a final report with coverage notes: what is well supported, what has gaps.
- Reject: generic "search unavailable"; empty result returned as success; stopping everything because one subagent failed. Trap: "return an empty list so the pipeline keeps running" hides the failure.

Example: Three of four subagents succeed; market data is down. Report three findings plus "market data unavailable."

## 5.4 Context in large codebase exploration

Exam rule: Long sessions degrade. Keep verbose exploration out of the main agent, and keep key findings outside the context window.

- Symptom: the model says what classes "typically" do instead of what it found. Fix: scratchpad file, or fresh session or subagent.
- Pick: a subagent for a narrow question ("find all test files"); it returns only a short summary.
- Pick: summarize one phase and inject the summary into the next phase's subagents. Reject full transcripts or nothing.
- Pick: each agent exports state to a known place; the coordinator loads a manifest on resume (crash recovery).
- Pick: `/compact`, with an instruction on what to keep, before context is full. Trap: reading every file upfront.

Example: Phase 1 maps modules; a five-bullet summary goes to phase 2 subagents tracing the refund flow.
