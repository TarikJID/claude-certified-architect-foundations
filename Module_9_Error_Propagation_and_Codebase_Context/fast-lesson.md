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

Setting (exam scenario: developer productivity): An engineer's main agent (the one she talks to) explores an unfamiliar codebase (a project's program files). Files and search results pile into its context (the text it can "see" at once). In a long session (one continuous conversation), early findings fade.

Before: asked if RefundProcessor (the refund-handling code) checks currency, the agent, though it read it, says what such code "typically" does.
After: it re-reads its notes ("RefundProcessor: no currency check"), then answers exactly.

Exam rule: send bulky work to subagents; keep key findings in files.

- Pick: a scratchpad file (notes on disk) to re-read, or a fresh session per task.
- Pick: a subagent (a helper with its own context) for a narrow question ("find all test files"), returning a short summary. Trap: the main agent reading every file buries its context.
- Setting: work runs in phases (stages): map the code, then trace refunds. Pick: give phase 2 subagents a phase 1 summary; they cannot see the main conversation. Trap: the full record floods them.
- Setting: agents run for hours; the program crashes. Pick: each saves progress to a known file; on restart the main agent reads a manifest (list of those files).
- Pick: `/compact` (swaps history for a summary) early, saying what to keep. Trap: automatic compaction (the same, run alone when nearly full) gives less control.
