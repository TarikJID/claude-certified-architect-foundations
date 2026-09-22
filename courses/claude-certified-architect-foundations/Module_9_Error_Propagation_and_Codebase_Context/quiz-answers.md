# Module 9 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 5.3 (Error Propagation Across Multi-Agent Systems)

**Q1.** A structured error payload including failure type, what was attempted, any
partial results, and possible alternatives. This gives the coordinator enough
information to make an intelligent recovery decision (retry, try an alternative,
proceed with partial data) instead of reacting to a bare failure signal.

**Q2.** They require opposite coordinator responses: an access failure (timeout,
unreachable backend) may warrant a retry or escalation decision, while a valid
empty result is a completed, trustworthy answer that retrying won't change.
Collapsing both into one response removes the information the coordinator needs
to choose correctly.

**Q3.** Anti-pattern 1: silently suppressing the error (returning `{}` as if it were a
valid empty result), which misleads the report. Anti-pattern 2: terminating the
entire workflow because of the one failure, wasting the three subagents'
completed work. Better: include the three successful findings plus an explicit
note that market data is unavailable — targeted recovery, not suppression or
full termination.

**Q4.** No — it should attempt local recovery first (retry, alternate query, fallback
source). Only once local recovery is exhausted should it propagate to the
coordinator, and the propagated error should include what was attempted and any
partial results gathered, not just a bare failure.

**Q5.** The generic message discards exactly the details (what failed, what was tried,
what's recoverable) that would let the coordinator act intelligently — it can
only guess whether to retry, wait, or switch sources. The instructive message
states what went wrong and what to try next, enabling an informed decision.


## Quiz — Lesson 5.4 (Context in Large Codebase Exploration)

**Q1.** Context degradation (a codebase-exploration manifestation of context rot) — the
earlier, specific finding has effectively "rotted" out of reliable reach in a
long, growing history. The standard mitigation is to start a fresh session or
subagent for a new task rather than letting one session run indefinitely.

**Q2.** It records key findings outside the context window, so the agent can reference
it for subsequent questions instead of relying on in-context memory. Because the
file is external, its contents survive compaction, session restarts, and
context-window boundaries — none of which in-context memory survives.

**Q3.** Spawn a subagent to investigate the narrow question (e.g. "find every place
`RefundProcessor` is instantiated"). The subagent's own isolated context absorbs
the raw exploration output (file reads, grep results); only its condensed
summary returns to the main agent's context.

**Q4.** Because context exceeding 200,000 tokens gets truncated, and the plan needs to
survive that truncation. Exporting state to a known location (with a
coordinator-level manifest referencing it) lets work resume from where it
stopped, rather than restarting from scratch, if a crash or truncation occurs.

**Q5.** `/compact` asks the model to summarize the conversation so far and replaces the
message history with that summary, freeing space consumed by verbose discovery
output. Running it proactively — optionally steered with an instruction about
what to keep — gives more control over what survives than waiting for an
automatic compaction trigger to decide for you.
