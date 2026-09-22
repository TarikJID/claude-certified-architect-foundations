# Module 5 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 3.4 (Plan Mode vs Direct Execution)

**Q1.** Plan mode — this is a large-scale, multi-file change with architectural
implications and possibly multiple valid approaches, exactly what plan mode is
designed for. Jumping straight to editing risks committing to a poor approach
before the tradeoffs are understood.

**Q2.** Plan mode is read-only until the plan is approved — Claude can read files and run
read-only commands but cannot make changes — so there's no risk of a premature or
wrong edit landing in the working tree while the approach is still being decided.

**Q3.** Explore is a built-in, read-only subagent (denied Write and Edit) used for
codebase search/discovery. Delegating to it keeps the volume of intermediate
search results in the subagent's own isolated context rather than the main
conversation's, since only a summary returns — preventing context window
exhaustion during later implementation phases.

**Q4.** Use plan mode to investigate an uncertain, high-stakes part of a task (e.g.
mapping call sites for a library migration) and get an approved plan; then exit
plan mode and use direct execution to apply that established pattern across the
identified files. You wouldn't use plan mode for everything because it adds an
approval round-trip overhead not worth paying once the implementation steps are
well-defined.


## Quiz — Lesson 3.5 (Iterative Refinement)

**Q1.** Provide 2-3 concrete input/output example pairs instead of more prose — e.g.
`user@example.com` → `true`, `invalid` → `false`, `user@.com` → `false`. Examples
remove ambiguity that natural-language descriptions leave open.

**Q2.** Write a test suite covering expected behavior, edge cases, and performance
requirements before implementation. Claude then implements, runs the tests, reads
which fail, and iterates until the suite passes — the executable pass/fail check
is what lets the loop close without a human manually re-verifying correctness
after every change.

**Q3.** Having Claude ask the developer clarifying questions (typically via
`AskUserQuestion`) about implementation, UI/UX, edge cases, and tradeoffs before
any implementation begins. Most useful for larger or unfamiliar-domain features,
where it surfaces considerations the developer may not have anticipated.

**Q4.** The two interacting bugs (same function) should be reported together in one
detailed message, so Claude designs one coherent fix accounting for both
constraints simultaneously. The unrelated footer typo is independent and should
be fixed separately/sequentially, keeping that change small and easy to verify in
isolation.


## Quiz — Lesson 3.6 (CI/CD Integration)

**Q1.** An interactive session waits for input a CI runner can never supply. The `-p`
(or `--print`) flag runs it non-interactively: Claude Code executes the prompt,
prints the result, and exits, returning an exit code the pipeline can branch on.

**Q2.** Add `--output-format json` (returns a structured JSON object) together with
`--json-schema` (a JSON Schema document constraining the response). Claude Code
validates the schema at startup and returns the payload in a `structured_output`
field.

**Q3.** The generating session retains the reasoning and assumptions that produced any
mistakes in the first place, making it less likely to question its own design
choices. An independent review instance, with no memory of that reasoning,
evaluates the diff on its own merits and is more likely to catch subtle issues.

**Q4.** Include the prior review's findings in the new invocation's context and instruct
Claude to report only new or still-unaddressed issues. Separately, a CI-invoked
`claude -p` run (without `--bare`) still loads the same CLAUDE.md files an
interactive session would, so documenting testing standards, fixture
conventions, and review criteria there improves CI-generated output quality.
