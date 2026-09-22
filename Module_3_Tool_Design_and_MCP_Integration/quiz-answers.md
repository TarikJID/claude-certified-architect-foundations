# Module 3 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 2.1 (Tool Interfaces and Descriptions)

**Q1.** The tool description is the primary — really the only — signal the model uses to
choose between tools. A minimal description gives too little information to
discriminate between similar tools, especially when purposes overlap.

**Q2.** (a) Rename and rewrite the description to be domain-specific (e.g.
`analyze_content` → `extract_web_results`, scoped to web content). (b) Split an
overly generic tool into purpose-specific tools with narrow contracts (e.g.
splitting `analyze_document` into `extract_data_points`, `summarize_content`,
`verify_claim_against_source`).

**Q3.** Tool selection is influenced by the whole context, not just tool descriptions.
The word "analyze" in the system prompt shares vocabulary with a tool named
`analyze_document`, creating an unintended keyword association that can steer
selection toward that tool even when a differently-named tool is the better fit.


## Quiz — Lesson 2.2 (Structured MCP Error Responses)

**Q1.** Transient (usually retryable), validation (not retryable as-is — needs corrected
input), business (not retryable — a policy rule, not a temporary condition),
permission (not retryable — needs escalation/different credentials).

**Q2.** A uniform message collapses all failure types into one, forcing the agent to
guess whether to retry, apologize, or escalate. Structured metadata lets the
agent make an evidence-based recovery decision instead.

**Q3.** It should attempt local recovery first (retry, fall back to an alternate source)
rather than immediately escalating. If it ultimately can't resolve the failure
locally, it should propagate to the coordinator along with what was attempted and
any partial results — not just a bare failure signal.

**Q4.** No — this is a valid empty result: the query executed successfully and
legitimately found nothing. A timeout is an access failure and should be reported
differently, e.g. `{isError: true, errorCategory: "transient"}`, since the two
require opposite agent responses (trust the empty result vs. consider retry).


## Quiz — Lesson 2.3 (Tool Distribution and tool_choice)

**Q1.** Every additional tool adds to the decision the model must make each turn — more
tools (especially similar ones) increases decision complexity and the chance of
choosing incorrectly, independent of any single tool's description quality.

**Q2.** Restrict the synthesis agent's tool set to only the tools relevant to its role
(e.g. `format_report`, `cite_source`), removing `web_search` entirely so
cross-specialization misuse isn't possible — rather than relying on prompting
alone to prevent it.

**Q3.** `auto` lets Claude decide whether to call a tool at all or respond in text.
`any` forces some tool call but leaves the choice of which tool to Claude.
`{"type":"tool","name":"..."}` forces one specific tool. You'd force a named tool
to guarantee a particular step (e.g. `extract_metadata`) always runs first in a
pipeline before other steps.

**Q4.** Scoped tool access with limited cross-role tools: keep the default tool set
scoped to the role, but add a small number of narrow, constrained cross-role
tools for specific high-frequency needs, routing anything more complex through
the coordinator instead of broadly expanding tool access.


## Quiz — Lesson 2.4 (MCP Server Integration)

**Q1.** The team's shared server goes in project-scoped `.mcp.json` (committed to version
control). The developer's experimental server goes in user-scoped
`~/.claude.json` (private to them, applies across their own projects).

**Q2.** Because the file is checked into version control, a literal secret would be
exposed to everyone with repo access. Environment variable expansion (`${VAR}`,
or `${VAR:-default}`) lets the file reference a variable name while each
developer supplies their own value locally.

**Q3.** Enhance the MCP tool's description to explicitly explain its capabilities and
what it returns in enough detail that the agent recognizes it as the stronger
choice — tool descriptions are the model's only window into a tool's
capabilities, so an under-described MCP tool loses to a well-documented built-in.

**Q4.** When the integration is genuinely team-specific — internal systems, proprietary
APIs, business logic no community server could reasonably cover — where the
value of a purpose-built integration outweighs the cost of owning a server. For
standard integrations (e.g. Jira), an existing community/vendor server should be
adopted instead.

**Q5.** Resources are read-only, URI-identified content a client can list and read
directly, without exploratory tool calls. Exposing table schemas as resources
lets the agent see the full schema catalog up front and plan a correct query
immediately, instead of first calling "list tables" then "describe table" for
each candidate.


## Quiz — Lesson 2.5 (Built-in Tools: Read, Write, Edit, Bash, Grep, Glob)

**Q1.** Grep — it searches file contents for a pattern. Glob would only match files by
name/path pattern and cannot search inside file contents.

**Q2.** Read the full file, then Write back a reconstructed version with the intended
change applied. It works because Write replaces the whole file rather than
needing to isolate one unique match, sidestepping Edit's uniqueness constraint.

**Q3.** Start narrow: Grep for entry points directly relevant to the question, then Read
only the specific files Grep surfaces to follow imports and trace flow, repeating
as understanding builds. This keeps context usage proportional to what's actually
needed, instead of front-loading the entire codebase regardless of relevance.

**Q4.** Call sites that reference the function only under its re-exported/aliased names
won't match a Grep for the original name. The correct technique: first identify
all the names the functionality is exported/re-exported under, then Grep for
each name in turn across the codebase.
