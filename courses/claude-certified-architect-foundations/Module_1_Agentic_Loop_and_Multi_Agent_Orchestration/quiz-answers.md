# Module 1 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 1.1 (Agentic Loops)

**Q1.** `stop_reason`. `"tool_use"` means the loop must execute the requested tool(s) and
continue; `"end_turn"` means Claude produced a final response and the loop
terminates.

**Q2.** The Messages API is stateless — Claude only "sees" what is included in the next
request. If a tool's result isn't added as a `tool_result` block in the history
sent on the following call, Claude has no way to know the tool ran or what it
returned.

**Q3.** (1) Parsing assistant text for phrases like "I'm done" — free text is not a
structured signal. (2) Treating an arbitrary iteration cap as the primary stopping
mechanism — cuts off legitimate work or runs too long. (3) Checking for the
presence of assistant text as a completion proxy — fails because Claude can emit
explanatory text alongside a `tool_use` block in the same turn, so text presence
doesn't mean the loop should stop.

**Q4.** In model-driven decision-making, Claude reasons about which tool to call next
based on everything in context, adapting turn by turn. A pre-configured decision
tree hard-codes the sequence and branching logic in advance, with the LLM only
filling in specific sub-steps.


## Quiz — Lesson 1.2 (Coordinator-Subagent Orchestration)

**Q1.** No — subagents never communicate with each other directly. All inter-subagent
communication, error handling, and information routing passes through the
coordinator.

**Q2.** No. Subagent context isolation means the subagent's raw exploration (the 40
documents) stays in its own isolated context window; only its final summary
returns to the coordinator.

**Q3.** Overly narrow/vague task decomposition causes duplicated work and coverage gaps —
subagents can't see what others are doing. The coordinator should partition the
scope into distinct, non-overlapping slices (specific subtopics, source types, or
time periods) with explicit objectives, output format, tool/source guidance, and
boundaries for each subagent.

**Q4.** Apply the iterative refinement loop: re-delegate by spawning additional
search/analysis subagents with targeted queries addressing the specific gap, then
re-invoke synthesis — repeating until coverage is judged sufficient.


## Quiz — Lesson 1.3 (Subagent Invocation, Context Passing, Spawning)

**Q1.** No. The `Task`/`Agent` tool must be present in the coordinator's `allowedTools`
for it to spawn any subagent at all, regardless of how `AgentDefinition`s are
configured. It's missing here.

**Q2.** Subagents don't automatically inherit the coordinator's context or share memory
between invocations. Complete findings must be included directly (verbatim) in
the prompt — a reference like "the earlier findings" gives the subagent nothing
to resolve.

**Q3.** `description` (natural-language text Claude uses to decide when to invoke this
subagent automatically) and `prompt` (the subagent's own system prompt defining
its role, expertise, and behavior).

**Q4.** For parallelism: emit multiple `Task`/`Agent` tool calls within a single
coordinator response, rather than one call per turn. For diverging from a shared
baseline: `fork_session`, which creates an independent session copying the
existing session's full history without altering the original.

**Q5.** Goal-oriented (declarative) prompts let a subagent adapt its approach to what it
actually discovers; procedural instructions break as soon as reality diverges from
the anticipated sequence. Even so, the prompt needs an objective, an expected
output format, guidance on which tools/sources to use, and clear task boundaries.
