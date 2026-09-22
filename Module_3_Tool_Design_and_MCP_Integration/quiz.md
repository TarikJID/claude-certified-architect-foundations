# Module 3 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 2.1 (Tool Interfaces and Descriptions)

**Q1.** Why does a minimal tool description (name + one-line summary) cause
unreliable tool selection when several similar tools exist?

**Q2.** `analyze_content` and `analyze_document` have near-identical
descriptions and the agent keeps misrouting between them. Name the two repair
techniques from this lesson and give an example of each.

**Q3.** A system prompt says "always analyze the document thoroughly." Why might
this bias tool selection even if every tool description is well written?

---

## Quiz — Lesson 2.2 (Structured MCP Error Responses)

**Q1.** Name the four error categories this lesson describes, and state whether
each is typically retryable.

**Q2.** Why is a generic "Operation failed" response worse than one carrying
`errorCategory`, `isRetryable`, and a description?

**Q3.** A search subagent's primary API times out. What should it do before
reporting anything to the coordinator, and what must it include if it does end up
reporting?

**Q4.** `lookup_order("12345")` returns `{status: "success", results: []}`. Is
this a failure? Contrast it with what a timeout response should look like.

---

## Quiz — Lesson 2.3 (Tool Distribution and tool_choice)

**Q1.** Why does giving an agent 18 tools instead of 4-5 degrade tool selection
reliability, even if none of the 18 tools is individually poorly designed?

**Q2.** A synthesis agent, which should only combine already-gathered findings,
keeps firing off its own web searches when it has a `web_search` tool available.
What's the fix?

**Q3.** Explain the difference between `tool_choice: "auto"`, `"any"`, and
`{"type": "tool", "name": "..."}`, and give a scenario where you'd want to force
a specific named tool.

**Q4.** What is the middle-ground pattern between "give every agent every tool"
and "give every agent only its narrowest role-specific tools"?

---

## Quiz — Lesson 2.4 (MCP Server Integration)

**Q1.** A team wants a shared GitHub MCP server available to every teammate via
version control, and a developer separately wants to try an experimental server
just for themselves. Which scopes should each use?

**Q2.** Why shouldn't a committed `.mcp.json` contain a literal API token, and
what syntax solves this?

**Q3.** A generic MCP tool `search_code` is described only as "search the
codebase" and the agent keeps using the built-in Grep instead, even though
`search_code` does more capable semantic search. What's the fix?

**Q4.** When should a team build a custom MCP server instead of adopting an
existing community one?

**Q5.** What are MCP resources, and why would a database MCP server expose table
schemas as resources rather than requiring a tool call to fetch them?

---

## Quiz — Lesson 2.5 (Built-in Tools: Read, Write, Edit, Bash, Grep, Glob)

**Q1.** You need to find every place the string "DEPRECATED_API_KEY" appears in a
codebase. Which built-in tool, and why not the alternative?

**Q2.** `Edit` fails because its `old_string` matches five places in a file.
What's the reliable fallback, and why does it work when Edit doesn't?

**Q3.** Describe the "Grep-then-Read" incremental exploration strategy and why
it's preferable to reading every file in a codebase upfront.

**Q4.** A function `validateUser` is re-exported as `checkAuth` and re-wrapped as
`requireAuth` elsewhere. Why would a single Grep for `validateUser` under-count
its usages, and what's the correct technique?
