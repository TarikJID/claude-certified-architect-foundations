# Module 9 Fast Lesson

## 5.3 Passing errors up in a team of agents

Setting (exam scenario: multi-agent research system): A coordinator agent (the "manager" that hands out work) sends four subagents (helper agents) to research a topic, then writes one report. If a subagent's source is down, the coordinator knows only what that subagent tells it.

Before: the market-data source is down. The subagent returns an empty list marked "success". The report silently skips market data.
After: the subagent reports "source down, tried twice, got 2 items". The report uses the other three findings and notes "market data unavailable".

Exam rule: say exactly what failed, so the coordinator can adapt. Hide nothing, stop nothing.

- Pick: a structured error: failure type, what was tried, partial results (anything already found), other options. Trap: a bare "search unavailable" leaves the coordinator guessing.
- Pick: report "could not reach the source" (an access failure, such as a timeout: no reply in time) differently from "searched, found nothing" (a valid empty result). Only the first is worth retrying. Trap: empty-as-success, as in Before, hides the failure.
- Pick: the subagent retries or tries a backup source itself first, and reports up only if that fails.
- Pick: the report ends with coverage notes: which findings are well supported, which topics have gaps.
- Trap: stopping everything over one failure: no report, and three good findings wasted.

## 5.4 Keeping the agent's working memory clean in a big codebase

Setting (exam scenario: developer productivity): An engineer uses an agent to explore an unfamiliar codebase (a project's program files). Every file and search result piles into its context (the text it can "see" at once). In a long session (one continuous conversation), early findings fade.

Before: asked if RefundProcessor checks currency codes, the agent (which read that code earlier) says what such code "typically" does. Warning sign.
After: it saved "RefundProcessor: no currency check" in a notes file, re-reads it, answers exactly.

Exam rule: keep bulky output out of the main agent; keep key findings outside its context.

- Pick: a scratchpad file (notes saved on disk) the agent re-reads, or a fresh session for a new task.
- Pick: a subagent for a narrow question ("find all test files"). It works in its own context and returns a short summary. Trap: the main agent reading every file buries its context.
- Pick: between phases, give phase 2 subagents a summary of phase 1, since they start blank. Trap: the full phase 1 record floods them.
- Pick: crash recovery: each agent saves progress to a known file; on restart the coordinator reads a manifest (a list of those files).
- Pick: `/compact` (replaces the history with a summary), run early, saying what to keep. Trap: waiting for automatic compaction gives less control.
