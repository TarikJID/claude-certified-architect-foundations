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
- Last session: 2026-09-27
- Notes: "i'm rather into short straight forward sentences, long texts and complicated sentences make me zone out" — keep chunks small, plain sentences, check in often.
  Also: "it's a bit weird that you call it 'my' code" — say **the harness**, not "your code". He is
  reasoning about the architecture, not writing it.
- Glossary: https://claude.ai/artifact/DF2gqN4scYhQ6v9uyvVce6 (source: `progress/glossary.html`,
  republish with that `url`). Requested 2026-09-27. Add each concept's exact name, plain definition
  and tag (API / Tools / Loop / Design / Harness) as it is taught. Only taught material.

## Module status

<!-- Modules come from course-outline.md. Do not maintain a second list here —
     add a row the first time a module is touched. -->

| Module | Status | Notes |
|--------|--------|-------|
| Module 1 — The Agentic Loop and Multi-Agent Orchestration | in progress | Started 2026-09-22. Lesson 1.1 taught in full (2026-09-27); next: Lesson 1.2 |

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

## Quiz attempts

<!-- Written BEFORE quiz-answers.md is opened. This is what makes an answer leak
     visible after the fact — the only thing standing in for a control here. -->

| Date | Module | Question | Attempted | Outcome |
|------|--------|----------|-----------|---------|
| 2026-09-27 | 1 | L1.1 Q2 — why a tool result must be appended to history | yes: "so the next round of Claude's thinking can use it; otherwise it would never be used" | correct after 1 hint — retry: "Claude has no memory; it only works with what the harness provides". Right mechanism; didn't use the words *stateless* or `tool_result` |
| 2026-09-27 | 1 | L1.1 Q4 — model-driven vs pre-configured decision tree | yes: "decision tree: next step known in advance (do this, then that, if X else Y). Agentic loop: model decides next step based on how the previous went; path not known in advance" | correct, clean, no hints |

## Still open

<!-- Concepts with either axis shaky, and anything the learner asked to come back to.
     A concept that did not land belongs here until it does — never dropped quietly. -->

- All five Lesson 1.1 concepts: recall and application both shaky (see tracker).

## Session log

<!-- Newest first. What was taught, what landed, what did not, and anything about
     HOW to teach this learner that the next session should know. -->

### 2026-09-27 — Session 2
- Cold drill on two items. Both wrong on the exact word, right on the idea: `run_tool` for
  `tool_use`, "pipeline" for workflow. Pattern matches the profile: reasoning strong, vocabulary
  weak. Keep drilling exact names.
- Taught the last Lesson 1.1 concept (termination anti-patterns). Checkpoint correct
  (just-taught). Asked a sharp roles question: who sets vs who reads `stop_reason`.

### 2026-09-22 — Session 1
- Onboarded. Style: lecture + checkpoints. Asked explicitly for short plain sentences.
- Started Module 1, Lesson 1.1. Concepts 1 and 2 taught; both checkpoints correct (just-taught).
- Grasped that "the code" means the harness — anything wrapping the model — and generalised it
  himself across claude.ai / Claude Code / own app.
- Asked for context ("what module are we in") early. Give a one-line locator at the top of a
  teaching block.
