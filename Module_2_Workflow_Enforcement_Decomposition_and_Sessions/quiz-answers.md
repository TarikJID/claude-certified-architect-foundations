# Module 2 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 1.4 (Workflows, Enforcement, Handoff)

**Q1.** The model can occasionally skip, misorder, or forget a stated rule under pressure
from other context — prompt-based guidance relies on the model reliably following
it every time. The deterministic alternative is programmatic enforcement: hooks
or prerequisite gates evaluated in code before a tool executes.

**Q2.** Because hooks are evaluated before deny rules, ask rules, permission mode, and
allow rules in the SDK's permission evaluation order, a hook's `deny` decision
cannot be overridden by any looser setting downstream — including
`bypassPermissions` mode.

**Q3.** Decompose into the constituent concerns (damage claim, double-charge claim),
investigate each using the same shared context (e.g., the already-verified
customer ID), then synthesize the individual findings into one unified
resolution — not two disconnected partial answers.

**Q4.** Customer identifying details, root-cause analysis, relevant amounts (e.g. a
proposed refund), and a recommended action — organized as discrete fields. It
matters because an unstructured note forces the human to reconstruct the
situation from scratch; a structured handoff lets them act immediately.


## Quiz — Lesson 1.5 (Hooks: Interception and Normalization)

**Q1.** `PostToolUse` fires after a tool returns its result and can transform/normalize
it before Claude sees it (e.g., unifying timestamp formats). `PreToolUse` fires
before a tool call executes and can deny/redirect it to enforce compliance rules
(e.g., blocking refunds over a threshold).

**Q2.** A `PostToolUse` hook normalizes both to one consistent representation before the
combined data reaches Claude. The discrepancy exists because the MCP spec lets
each tool declare its own `outputSchema` with no requirement that different tools
represent the same real-world data the same way.

**Q3.** It should redirect — the denial reason can instruct Claude toward an alternative
path, such as calling `escalate_to_human`, rather than merely failing silently,
so the agent has a productive next step instead of a dead end.

**Q4.** `isError: true` reports a failure inside the normal tool-result content channel,
letting the calling model see the failure as ordinary result content and
potentially self-correct or reason about it, rather than the call simply erroring
out at the transport level.


## Quiz — Lesson 1.6 (Task Decomposition Strategies)

**Q1.** Prompt chaining — the subtasks are known and predictable in advance (5 fixed
criteria, same sequence every time), which is exactly what fixed sequential
decomposition suits.

**Q2.** Attention dilution: a single call asked to review many files at high depth
produces inconsistent depth across files and misses issues, because effective
attention per file drops as total input grows. Splitting into per-file local
passes (full attention per file) plus a separate cross-file integration pass
(looking specifically for cross-file issues) avoids this.

**Q3.** First map the codebase's structure (directories, modules, dependencies); then
identify high-impact areas (most-used modules, historically buggy code,
untested critical paths) from that map; then create a prioritized plan — and let
that plan continue to adapt as dependencies and complications are discovered
during execution, rather than treating the initial plan as fixed.

**Q4.** In prompt chaining, the sequence of subtasks is fixed and known in advance. In
dynamic adaptive decomposition, a central orchestrator determines subtasks at run
time based on what earlier steps discover — the subtasks themselves aren't known
upfront.


## Quiz — Lesson 1.7 (Session State, Resumption, Forking)

**Q1.** `--resume <session-name>` (e.g., `claude --resume auth-refactor-investigation`).
"Continue" always picks up the most-recently-used session with no name/ID
required; `--resume` returns to one specific session among several.

**Q2.** `fork_session` — it creates an independent session copying the existing session's
full history from a shared baseline, leaving the original unchanged, so both the
fork and the original can be extended separately.

**Q3.** Inform the resumed session about the specific file change (ideally how it
changed), enabling targeted re-analysis of just that file — because the session
persists conversation history, not the filesystem, so its understanding of
`payment.py` is stale until told otherwise.

**Q4.** When the prior session's accumulated tool results are likely stale, or the
transcript is too large/noisy to be worth carrying forward — resuming risks the
model treating stale tool results in the long history as still current. Resume
instead when prior context is mostly still valid.
