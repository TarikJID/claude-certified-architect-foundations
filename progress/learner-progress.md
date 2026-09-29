# Learner Progress

<!-- The tutor reads this at the start of every session and writes to it AS THINGS
     HAPPEN, not at the end. Learners do not need to edit it.

     The rule this file exists to enforce: record EVIDENCE, not intentions. A note
     saying "check whether they remember X" can never be satisfied, so it survives
     forever and X gets asked again every session. A record of a clean cold answer
     closes the item. -->

## Learner profile

- Name: Tarik
- Preferred style: Lecture + checkpoints
- Started: 2026-09-22
- Last session: 2026-09-29
- Notes: "i'm rather into short straight forward sentences, long texts and complicated sentences make me zone out" — keep chunks small, plain sentences, check in often.
  Also: "it's a bit weird that you call it 'my' code" — say **the harness**, not "your code". He is
  reasoning about the architecture, not writing it.
  Also (2026-09-27, 2026-09-28): twice flagged a checkpoint question as unclear. Scenarios must be
  fully concrete — say exactly what each piece of data means, ask ONE question, no hidden
  assumptions (e.g. an unexplained code like `status: 3`).
  Also: state the premise a question depends on in the teaching itself, before asking. On the
  MCP formats checkpoint the lesson said "tools format data differently" but never said "and
  Claude has no key to decode them" — he fairly inferred Claude could decode per tool.
- Glossary: https://claude.ai/artifact/DF2gqN4scYhQ6v9uyvVce6 (source: `progress/glossary.html`,
  republish with that `url`). Requested 2026-09-27. Add each concept's exact name, plain definition
  and tag (API / Tools / Loop / Design / Harness) as it is taught. Only taught material.

## Module status

<!-- Modules come from course-outline.md. Do not maintain a second list here —
     add a row the first time a module is touched. -->

| Module | Status | Notes |
|--------|--------|-------|
| Module 1 — The Agentic Loop and Multi-Agent Orchestration | in progress | Started 2026-09-22. Lesson 1.1 taught + quizzed (2026-09-27). Lesson 1.2 taught + quizzed 2026-09-27. Lesson 1.3 taught + quizzed 2026-09-27. All Module 1 lessons taught and quizzed; exercise not done; nothing closed yet |
| Module 2 — Workflow Enforcement, Decomposition, and Sessions | in progress | Started 2026-09-28. Lesson 1.4 taught + quizzed 2026-09-28. Lesson 1.5 taught + quizzed (2026-09-28/29) |

Status values: `not started` · `in progress` · `completed`

## Concept tracker

<!-- One block per concept that has been taught. Two axes, closed independently.

     recall       — can name it cold (the term, the exact path, the metric)
     application  — can use it correctly on a real problem

     Conditions:
       just-taught — answered right after being taught. NEVER closes an item.
       cued        — the answer was somewhere in context.
       cold        — no help in context. The only condition that closes recall.

     Closing rules:
       recall      closed by two clean COLD recalls on SEPARATE days
       application closed by one correct unaided application, plus one later

     A closed item is not re-checked as an opener. Reopen it only if they get it
     wrong during normal work. -->

### Messages API request/response cycle and `tool_use` blocks
- Module: 1 (Lesson 1.1, prerequisite concept)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-22` · application · just-taught · correct — said the caller's code executes the tool, not Claude. Surprised by it; asked a good follow-up about who the "caller" is on claude.ai.

### Agentic loop lifecycle (`stop_reason`-driven control flow)
- Module: 1 (Lesson 1.1)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-22` · application · just-taught · correct — traced both branches unprompted: `end_turn`
    stops the loop and the text is surfaced to the user; `tool_use` means execute the named tool and
    continue.
  - `2026-09-27` · recall · cold · wrong — asked for the `stop_reason` value that means "run a
    tool". Said `run_tool`. Answer: `tool_use`.
  - `2026-09-27` · recall · cued · correct — L1.1 quiz Q1: named `stop_reason`, `tool_use`,
    `end_turn` exactly. Cued (said many times this session); does not count toward closing.
  - `2026-09-29` · recall · cold · correct — fresh conversation drill: "what field tells the harness
    to continue or stop?" → `stop_reason`, exact. First clean cold recall; one more on a later day closes it.

### Appending tool results to conversation history (`tool_result` + `tool_use` ID pairing)
- Module: 1 (Lesson 1.1)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-22` · application · just-taught · correct — reasoned that with no `tool_result` in
    history Claude has no knowledge of the outcome, so it re-requests the tool. Right mechanism.
    Told him the API-level detail (an unanswered `tool_use` is a 400, not a silent re-ask) and
    flagged it as outside the course material.
  - `2026-09-27` · application · cued · correct (1 hint) — L1.1 quiz Q2. First answer gave only the
    effect; after a hint said Claude has no memory and only sees what the harness sends. That is
    the stateless-API point. Did not produce the words *stateless* / `tool_result` (recall gap).

### Model-driven decision-making vs pre-configured decision trees
- Module: 1 (Lesson 1.1)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-22` · application · just-taught · correct — classified a fixed three-step invoice
    pipeline as a workflow, and gave the right reason (steps never vary, so predictability and cost
    win). Did not need the trade-off spelled out.
  - `2026-09-27` · recall · cold · wrong — asked for the name of the design where the step order is
    fixed in code ahead of time. Said "pipeline". Course terms: **workflow** / pre-configured
    decision tree (vs model-driven, i.e. agent). Right idea, wrong word — he used "workflow"
    himself on 09-22.
  - `2026-09-27` · application · cued · correct — L1.1 quiz Q4, no hints. Clear contrast: decision
    tree = path fixed in advance with branches; agentic loop = model picks next step from results.
    Cued: the drill earlier today named both terms.

### Agentic loop termination anti-patterns
- Module: 1 (Lesson 1.1)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — on "stop when any text appears", with
    Claude saying "Let me check the logs first" + a read request: said the harness stops, never
    runs the tool, and the logs are never read. Right. Then asked unprompted who needs
    `stop_reason`, the harness or the LLM. Answer given: Claude sets it, the harness reads it.
  - `2026-09-27` · application · cued · correct (1 hint) — L1.1 quiz Q3. Named and justified
    "any text = done" and "Claude said I'm done" unaided; needed a hint ("the harness just counts")
    for the iteration cap, then reasoned it well. Taught ~20 min earlier, so cued at best.

### Hub-and-spoke coordinator architecture
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — a search subagent fails mid-task: said the
    orchestrator finds out and decides, e.g. re-runs the subagent. Right: all error handling routes
    through the coordinator.
  - `2026-09-27` · application · cued · correct (2 hints) — L1.2 quiz Q1. "No direct talk" and
    tasks/results unaided; needed hints for info routing between subagents and for error handling
    (had applied the error case correctly himself ~40 min earlier).

### Subagent context isolation
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — user told coordinator "2024 sources only";
    subagent prompted "research the chip shortage". Said the subagent won't respect it: it has no
    knowledge of the user–coordinator conversation. Right.
  - `2026-09-27` · application · cued · correct — L1.2 quiz Q2 (40 documents), no hints. Explained
    via purpose (avoid clutter) and outcome (only useful content returns). Didn't use the term
    *context isolation* — recall still shaky.

### Coordinator responsibilities (decomposition, delegation, aggregation, dynamic subagent selection)
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — "What year was the CHIPS Act signed?":
    named dynamic subagent selection, zero subagents, coordinator answers itself. Added unprompted:
    if the setup forbids the coordinator doing work, it's one subagent via delegation. Good nuance.

### Risks of overly narrow / vague task decomposition
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — Lisbon offsite, three subagents with the same
    vague prompt: named duplicated work, missed information (no subtask assigned), coverage gaps
    (e.g. nobody does transport), and linked them causally. Strong.
  - `2026-09-27` · application · cued · partial — L1.2 quiz Q3: named duplication only; missed coverage
    gaps (had named them himself ~30 min earlier on the Lisbon case).

### Partitioning research scope across subagents
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — wrote a full transport-subagent prompt with
    objective (Paris→Lisbon, 30 people, dates), output format (flight list with fields), tools (live
    search), boundaries (plane, direct, no departures before 8am). Boundaries covered constraints but
    not what is out of scope (hotels/food/local transfers) — pointed that out as the non-overlap part.
  - `2026-09-27` · application · cued · partial (1 hint) — L1.2 quiz Q3. First fix offered was "use a
    single subagent" (wrong direction). After hint, listed all four elements incl. don'ts. Did not
    produce the word *partitioning*.

### Iterative refinement loop (coordinator re-delegation)
- Module: 1 (Lesson 1.2)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct (partial) — Lisbon draft missing airport→hotel
    transfer: said spawn a new subagent scoped to transfers for 30 people per arrival time. Right
    re-delegation, well targeted. Didn't mention re-running synthesis and re-checking afterwards.
    Also caught a sloppy tutor sentence ("the coordinator, not Claude") — correctly: the coordinator
    is itself a Claude instance.
  - `2026-09-27` · application · cued · correct (1 hint) — L1.2 quiz Q4. First said "rework from the
    researcher"; after hint: spawn a fresh subagent targeted at the gap (linked to context
    isolation himself), then check completeness and merge. Did not say "repeat until sufficient".

### Task/Agent tool and the `allowedTools` requirement
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — coordinator with allowed tools Read/Grep/
    WebSearch never uses its defined subagents: said it lacks the Task/Agent tool; fix is to add
    `Agent` to its allowed tools. Right.
    Note: this checkpoint is close to L1.3 quiz Q1 — treat a same-day Q1 answer as heavily cued.
  - `2026-09-27` · application · cued · correct — L1.3 quiz Q1, no hints. Heavily cued.

### Explicit context passing to subagents
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · partial — "Fix the failing test" with no context: said
    the subagent won't know what the coordinator means (right, but general). Read "don't touch the
    database code" as forbidding all code changes → "paradox". Tutor's scenario was ambiguous: the
    bug is in auth.ts, the database code is a separate part. Clarified; asked for the better prompt.
  - `2026-09-27` · application · just-taught · correct — after clarification: without the rule the
    subagent might change database code if it thinks that fixes the bug. Wrote: "Bug in auth.ts,
    error is 'XXX'. Fix it in auth.ts, never touch the database code." File, error, decision all
    passed as content. (Learner flagged the original question as unclear — fair.)
  - `2026-09-27` · application · cued · correct — L1.3 quiz Q2, no hints: no memory of earlier
    findings; pass them in the prompt (or a file path if it can read). Course answer: verbatim in prompt.

### `AgentDefinition` configuration
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — reviewer subagent with description "helps
    with stuff" rarely used: said the coordinator needs a clear description of when/why to trigger
    it. Right: `description` drives when it gets invoked.
  - `2026-09-27` · recall · cued · correct — L1.3 quiz Q3: named `description` and `prompt` exactly.
  - `2026-09-27` · application · cued · correct — description = when/why to trigger; prompt = "how"
    (thin; should say the subagent's own system prompt: role and behaviour).

### Session forking (`fork_session`)
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — slow checkout page, two fixes to try: said
    fork the session. Added "after asking Claude to log its conclusions" — unnecessary, the fork
    copies full history. Didn't say which branch runs A vs B; told him (fork → A, original → B).
  - `2026-09-27` · recall · cued · partial — L1.3 quiz Q4b: said "you fork"; exact name is
    `fork_session`.
  - `2026-09-29` · recall · cold · correct — fresh conversation drill, scenario-only question →
    `fork_session`, exact. Fixed the 09-27 slip ("fork"). First clean cold recall.

### Structured data formats separating content from metadata
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — rewrote "cost carmakers ~$210B in 2021,
    according to a report I read" as Claim / Evidence / Source fields. Right structure.

### Parallel subagent spawning in a single turn
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · correct — 4+3+2 min sequential = 9 min; spawn all three
    → 4 min (the slowest). Right. Didn't say "in one response" explicitly.
  - `2026-09-27` · application · cued · correct — L1.3 quiz Q4a: multiple Agent calls in the same
    response, each with its own structured prompt. No hints.

### Goal-oriented coordinator prompts (vs step-by-step procedural)
- Module: 1 (Lesson 1.3)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-27` · application · just-taught · partial — procedural hotel prompt: named two good break
    points (first result may be an ad / not in Lisbon; booking.com could be down). Rewrite was
    goal-oriented ("best rating/price ratio, reputable sites like booking.com") but thin: no output
    format, no boundaries (30 people, dates, budget, how many). Asked for a retry.
  - `2026-09-27` · application · just-taught · correct (retry) — "Find 3 Lisbon hotels for 30 people,
    27–30 September, list prices." Boundaries and a minimal output format now present, but dropped
    the quality criterion and source guidance from v1. Showed him the merged version.
  - `2026-09-27` · application · cued · correct — L1.3 quiz Q5, no hints: procedural breaks when
    reality diverges; listed all four elements. First complete four-item list unaided today.

### Permission evaluation order for tool calls (hooks first)
- Module: 2 (Lesson 1.4, prerequisite)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · correct — allow rule for `process_refund` + hook
    blocking refunds > $500, $800 request: "the hook blocks it, hooks run before allow rules." Right.
  - `2026-09-28` · application · cued · partial (1 hint, then revealed) — L1.4 quiz Q2. Explained the
    gate via determinism and "bypassPermissions only skips asking the user"; did not use the
    evaluation order (hooks first, before permission mode) even after a hint pointing at it.

### Programmatic enforcement vs prompt-based guidance (deterministic vs probabilistic)
- Module: 2 (Lesson 1.4)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · correct — bank, 10k refunds/month, prompt rule vs hook:
    "Team A, because rules in prompts can fail." Right; didn't use *probabilistic*/*deterministic*.
  - `2026-09-28` · application · cued · correct — L1.4 quiz Q1, no hints: prompts can be forgotten
    (full context) or misread; deterministic alternative = code-based gate, e.g. `PreToolUse`.

### Programmatic prerequisite gates (`PreToolUse` deny with reason)
- Module: 2 (Lesson 1.4)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · correct — ship_order gated on charge_payment: checks
    payment succeeded; if not, deny with reason "charge_payment has not happened or failed". Right.
    Small slip: said "if yes, it calls ship_order" — the hook doesn't call the tool, it lets the
    requested call through. Corrected.

### Multi-concern request decomposition with parallel investigation
- Module: 2 (Lesson 1.4)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · partial — "can't log in + wrong plan on invoice": split
    into two issues (right), but handled them sequentially (login first, invoice only after login is
    fixed) and as two separate interactions; no shared context, no single combined reply. Hint given.
  - `2026-09-28` · application · just-taught · correct (retry) — "investigate both at once, then send
    one combined reply." Raised a fair point: actually fixing may take several exchanges. Agreed —
    the rule is about the investigation and the first unified reply, not a one-message fix.
  - `2026-09-28` · application · cued · correct — L1.4 quiz Q3, no hints. Missing: shared context.

### Structured handoff summaries for human escalation
- Module: 2 (Lesson 1.4)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · correct — wrong-plan invoice escalation: all four
    fields (customer ID, root cause "plan change failed 3 Sept", amount "€30 overcharge × months",
    action "refund overcharges"). Computed the €30 himself. Refinements given: state a concrete total
    rather than a formula; action should also fix the plan so it doesn't recur.
  - `2026-09-28` · recall · cued · partial — L1.4 quiz Q4: listed root cause, amounts, recommended
    action; first item muddled ("customer root cause" for customer details). Skipped the why.
    Pushed back that the question is tied to customer service — gave a generic framing (on-call
    engineer handoff) and explained the exam guide uses the support scenario itself.

### MCP tool results: `isError` and inconsistent formats across tools
- Module: 2 (Lesson 1.5, prerequisite)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · partial — checkpoint needed two rewrites (learner rightly
    said it lacked context). Final: `shipped: "yes"`, `paid: 1` where 1 = not paid, agent not told.
    Answered "shipped and not paid" — used the meaning the tutor had given him, which the agent
    lacked. Point explained: agent likely reads 1 as "yes" → tells customer it's paid. Tutor's
    question design was the main problem here, not his reasoning.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q2: formats differ because separate tools
    set their own standards and MCP doesn't force a shared one. Didn't name `outputSchema`.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q4 (reworded), no hints: failure arrives as
    content Claude can read → retry / escalate / other tool; a crash gives nothing. Matches course.

### `PostToolUse` hooks for result normalization
- Module: 2 (Lesson 1.5)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-28` · application · just-taught · correct — said the hook should replace `paid: 1` with the
    status it maps to in the tool's documentation, then the agent answers from that value. Right
    mechanism (translate before Claude sees it). Didn't spell out the final customer answer.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q1 (Post half): rewrites the result before
    Claude sees it. Didn't say *normalize*.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q2, no hints: PostToolUse normalizes;
    used the word *normalizing* this time. Also gave the why (tools built separately, own formats).

### `PreToolUse` hooks for compliance interception (deny + redirect)
- Module: 2 (Lesson 1.5)
- recall: shaky
- application: shaky
- Attempts:
  - `2026-09-29` · application · just-taught · correct — $800 refund, rule > $500 needs a human: wrote
    "Refunds over $500 need human approval, use escalate_to_human instead." Matches the course.
    Then asked unprompted whether the "refused because X, do Y" is code or LLM. Explained: the
    check and the reason text are code (deterministic); following the redirect is Claude
    (probabilistic) — the block is guaranteed, the redirect is guidance.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q1 (Pre half): checks before the tool
    runs, against predefined conditions. Didn't mention deny/redirect.
  - `2026-09-29` · application · cued · correct — L1.5 quiz Q3: deny + guide to escalate_to_human.
    Didn't state the why (avoid a dead end). Heavily cued.

## Quiz attempts

<!-- Written BEFORE quiz-answers.md is opened. This is what makes an answer leak
     visible after the fact — the only thing standing in for a control here. -->

| Date | Module | Question | Attempted | Outcome |
|------|--------|----------|-----------|---------|
| 2026-09-27 | 1 | L1.1 Q2 — why a tool result must be appended to history | yes: "so the next round of Claude's thinking can use it; otherwise it would never be used" | correct after 1 hint — retry: "Claude has no memory; it only works with what the harness provides". Right mechanism; didn't use the words *stateless* or `tool_result` |
| 2026-09-27 | 1 | L1.1 Q4 — model-driven vs pre-configured decision tree | yes: "decision tree: next step known in advance (do this, then that, if X else Y). Agentic loop: model decides next step based on how the previous went; path not known in advance" | correct, clean, no hints |
| 2026-09-27 | 1 | L1.1 Q3 — three termination anti-patterns + why | yes: (a) stop on any text — text can come with a tool request; (b) stop when Claude says it's done — ambiguous, unreliable; (c) couldn't recall | correct after 1 hint — 3rd: fixed round budget (e.g. 10) is wrong as the main rule: too few for some tasks, far more than needed for others. Did not add that a cap is fine as a safety backstop |
| 2026-09-27 | 1 | L1.1 Q1 — field driving continue/stop + its two values | yes: "stop_reason, with values tool_use and end_turn" | correct, no hints — but heavily cued (answer said repeatedly this session) |
| 2026-09-27 | 1 | L1.2 Q1 — can subagents talk directly; what passes through the coordinator | yes: "No, each subagent only speaks with the coordinator. Coordinator dispatches work (objective, tools, output, boundaries), receives results back" | partial — first half right; tasks-out/results-back right but missed errors and subagent-to-subagent info routing. Correct after 2 hints: got info routing on hint 1, errors on hint 2 |
| 2026-09-27 | 1 | L1.2 Q2 — subagent read 40 docs: are they in the coordinator's context? | yes: "No, it would clutter the coordinator's context for no good reason; the coordinator only gets the useful content" | correct, no hints — gave the purpose (keep coordinator context clean) and the result (only the summary returns); did not name *context isolation* / own context window |
| 2026-09-27 | 1 | L1.2 Q3 — 3 unguided subagents on "semiconductor shortage": failure + fix | yes: "Duplicated work. The coordinator should have given the task to a single researcher subagent" | partial — failure half right (duplication; missed coverage gaps). Fix wrong: one subagent avoids overlap but drops the split; course answer is partitioning. After 1 hint: "clear objective, boundaries with do's and don'ts, tools, output format" — all four elements; didn't say *partitioning* / non-overlapping slices, and never named coverage gaps. Correct after 1 hint, incomplete |
| 2026-09-27 | 1 | L1.2 Q4 — coordinator notices a topic gap after first draft | yes: "Request a rework from the researcher, with explicit mention of what needs to be done" | partial — targeted re-delegation right; but "rework from the researcher" (course: spawn new targeted subagents) and no re-synthesis / repeat. Correct after 1 hint: new subagent (the old one has no memory), targeted at what was missed; then check completeness and merge with the first output |
| 2026-09-27 | 1 | L1.3 Q2 — "use the findings from the earlier search": why it fails | yes: "subagent has no memory of earlier findings; coordinator should provide the findings, or a path to a file with them if the subagent has a read tool" | correct, no hints. File-path alternative is sensible but the course answer is: include the findings verbatim in the prompt |
| 2026-09-27 | 1 | L1.3 Q3 — two required AgentDefinition fields + what each controls | yes: "description: when/why the coordinator should trigger it; prompt: how" | correct, no hints. Both field names exact (recall, cued). "how" is thin for prompt — it is the subagent's own system prompt (role, expertise, behaviour) |
| 2026-09-27 | 1 | L1.3 Q4 — parallelism in one response + feature to branch completed analyses | yes: "spawn the three subagents in the same response using the Agent tool, each with its own structured prompt. You fork" | correct, no hints. Said "fork", not the exact name `fork_session` |
| 2026-09-27 | 1 | L1.3 Q5 — why goal-oriented > procedural + four elements | yes: "step-by-step breaks if reality doesn't align with what's expected. Objective, tools, output format, boundaries" | correct, clean, no hints — all four elements |
| 2026-09-27 | 1 | L1.3 Q1 — reviewer defined, allowed_tools Read/Grep: can it be invoked? | yes: "No, it can't spawn a subagent; it's missing the Agent tool" | correct, no hints — heavily cued (near-identical checkpoint earlier today) |
| 2026-09-28 | 2 | L1.4 Q1 — why prompt-only ordering fails + deterministic alternative | yes: "prompting isn't infallible: can be forgotten when the context window is full, or misinterpreted. Alternative: code-based gating, e.g. PreToolUse, imposing a condition before a tool can be used" | correct, clean, no hints. Named `PreToolUse` exactly |
| 2026-09-28 | 2 | L1.4 Q2 — how a PreToolUse gate guarantees order even in a permissive mode | yes: "the LLM has no influence on the PreToolUse condition check: either it happened or not" | partial — determinism right, but the "even in a permissive mode" part needs the evaluation order (hooks run before permission mode). Retry: "bypassPermissions skips asking the user, it doesn't change how the code works" — sound intuition, but still no evaluation order. Answer revealed. Partial after 1 hint |
| 2026-09-28 | 2 | L1.4 Q3 — damaged + charged twice: decomposition and reply structure | yes: "split into two issues, investigate both at once, one combined reply" | correct, no hints; omitted "same shared context" |
| 2026-09-28 | 2 | L1.4 Q4 — four handoff elements + why transcript access matters | yes: "customer root cause [sic], problem root cause, amount if applicable, recommended action"; did not answer the 'why'; said the question felt tied to the customer-service example | partial — 3/4 elements clean ("customer root cause" likely meant customer details); 'why' part missing. No hints; answer given with a generic framing |
| 2026-09-29 | 2 | L1.5 Q1 — PreToolUse vs PostToolUse: when + typical use | yes: "Pre checks before the tool runs whether the agent may use it, based on predefined conditions. Post prepares the tool's result before Claude sees it, rewriting it to make it clear" | correct, no hints. Missing the exam words: *deny/redirect* (Pre) and *normalize* (Post) |
| 2026-09-29 | 2 | L1.5 Q2 — orders int vs billing string status: fix + why it exists | yes: "PostToolUse normalizes the results to remove ambiguity. Difference exists because the two MCP tools can be built by different owners with their own standards; PostToolUse handles it rather than asking owners to adapt" | correct, clean, no hints. Course phrasing: MCP lets each tool declare its own `outputSchema`, no requirement to match — his "different owners, own standards" is the same point |
| 2026-09-29 | 2 | L1.5 Q3 — what a >$500 refund denial should also do, and why | yes: "deny and guide to the alternative tool decided by the developer, e.g. escalate_to_human" | correct, no hints; "why" (no dead end, productive next step) implied, not stated. Heavily cued (checkpoint same scenario earlier) |
| 2026-09-29 | 2 | L1.5 Q4 (reworded: isError vs crash; JSON-RPC part not yet taught) | yes: "agent understands what's happening, can retry, escalate, use another tool; a crash leaves it in the dark" | correct, clean, no hints. Small wording: the tool didn't crash — it failed and reported it as content |

## Still open

<!-- Concepts with either axis shaky, and anything the learner asked to come back to.
     A concept that did not land belongs here until it does — never dropped quietly. -->

- MCP isError / inconsistent tool formats, PostToolUse normalization, PreToolUse deny+redirect (L1.5): both axes shaky, just taught.
- Permission evaluation order, programmatic vs prompt enforcement, prerequisite gates, multi-concern decomposition, structured handoff (L1.4): both axes shaky, just taught.
- Task/Agent tool + allowedTools, explicit context passing, AgentDefinition, fork_session, structured claim/evidence/source, parallel spawning, goal-oriented prompts (L1.3): both axes shaky, just taught.
- Hub-and-spoke, subagent context isolation, coordinator responsibilities, decomposition risks, partitioning, iterative refinement (L1.2): both axes shaky, just taught.
- All five Lesson 1.1 concepts: recall and application both shaky (see tracker).

## Session log

<!-- Newest first. What was taught, what landed, what did not, and anything about
     HOW to teach this learner that the next session should know. -->

### 2026-09-29 — Session 3 (fresh conversation, so cold checks count)
- Cold drill: `stop_reason` — correct, exact. `fork_session` — correct, exact (was "fork" on 09-27).

### 2026-09-29 — Session 2, continued (same conversation, third day)
- Finished Lesson 1.5 (PreToolUse redirect). Asked whether the redirect is code or LLM — explained
  the split (check + reason text = code; following it = Claude).
- L1.5 quiz: 4/4, no hints (Q4 reworded to skip untaught JSON-RPC part). Q3 heavily cued. Used
  *normalizing* unprompted. Still omits "why" halves occasionally (Q3).
- Earlier in Lesson 1.5 (09-28): pushed back twice on unclear checkpoint questions — both fair.
  See profile note: state premises, fully concrete scenarios.

### 2026-09-28 — Session 2, continued (same conversation, new day)
- Before Module 2, asked why his own multi-agent system spawned subagents with no tool list in
  CLAUDE.md. Explained CLAUDE.md is instructions, not tool config; with no restriction, built-in
  tools incl. Agent are available by default (flagged as outside course). Exam rule stands.
- No cold drill: the same conversation still has yesterday's answers on screen, so nothing asked
  here can count as `cold`. Cold checks need a fresh conversation.
- Started Module 2, Lesson 1.4.
- Lesson 1.4 taught (5 concepts, all checkpoints correct; multi-concern needed a retry).
- L1.4 quiz: Q1 clean, Q2 partial (didn't use evaluation order, revealed), Q3 clean, Q4 partial
  (3/4 elements, no 'why'). All cued. Recurring gap: the *mechanism name* behind an answer
  (evaluation order) and complete lists.

### 2026-09-27 — Session 2
- Cold drill on two items. Both wrong on the exact word, right on the idea: `run_tool` for
  `tool_use`, "pipeline" for workflow. Pattern matches the profile: reasoning strong, vocabulary
  weak. Keep drilling exact names.
- Taught the last Lesson 1.1 concept (termination anti-patterns). Checkpoint correct
  (just-taught). Asked a sharp roles question: who sets vs who reads `stop_reason`.
- Asked what in the harness makes the decision: explained it is a plain if/else on `stop_reason`,
  no second LLM — which is why a structured field exists. Landed.
- Asked for a glossary artifact (link in profile). Built with 12 Lesson 1.1 terms.
- L1.1 quiz: 4/4 with 2 hints (Q2 stateless why; Q3 iteration cap). All cued — same day as
  teaching/drill. Names still the weak point: didn't produce *stateless* or `tool_result`.
- Lesson 1.2 taught, all 6 concepts; every checkpoint correct (just-taught). Applied well in
  scenarios (Lisbon offsite). Glossary extended with a Multi-agent tag.
- L1.2 quiz: 4/4 with hints — Q1 2 hints (errors, info routing), Q2 clean, Q3 1 hint and incomplete
  (proposed one subagent; missed coverage gaps), Q4 1 hint. All cued (same session as teaching).
  Pattern: list-type answers come back with items missing; reasoning is sound when nudged.
- Lesson 1.3 taught, all 7 concepts. All checkpoints correct (two needed a retry: explicit context
  passing — tutor's scenario was ambiguous, learner said so; goal-oriented prompt — first rewrite
  lacked format/boundaries). Pattern again: gets the idea, drops parts of a multi-part answer.
- Glossary at 28 terms.
- L1.3 quiz: 5/5, no hints. Exact names: `description`, `prompt` right; said "fork" not
  `fork_session`. Listed all four goal-oriented prompt elements unaided — first complete list today.
  All cued (same session as teaching).

### 2026-09-22 — Session 1
- Onboarded. Style: lecture + checkpoints. Asked explicitly for short plain sentences.
- Started Module 1, Lesson 1.1. Concepts 1 and 2 taught; both checkpoints correct (just-taught).
- Grasped that "the code" means the harness — anything wrapping the model — and generalised it
  himself across claude.ai / Claude Code / own app.
- Asked for context ("what module are we in") early. Give a one-line locator at the top of a
  teaching block.
