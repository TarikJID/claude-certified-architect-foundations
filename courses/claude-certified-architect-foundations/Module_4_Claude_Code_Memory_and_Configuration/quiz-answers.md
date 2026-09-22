# Module 4 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 3.1 (CLAUDE.md Hierarchy)

**Q1.** Check whether the instruction was written to `~/.claude/CLAUDE.md` (user-level)
instead of the project-level `./CLAUDE.md`. User-level settings apply only to the
person who wrote them and are never shared via version control, so a new team
member cloning the repo simply never receives them.

**Q2.** It imports another file's content into context at launch. It resolves relative
to the file containing the import (not the working directory), and can
recursively import further files up to a depth of four hops.

**Q3.** Split it into topic-specific files in `.claude/rules/` (e.g. `testing.md`,
`api-conventions.md`, `deployment.md`). Rules without `paths` frontmatter still
load at launch like a CLAUDE.md, but the split makes the instructions modular and
easier to maintain (full token-savings benefit comes from adding path scoping —
covered in Lesson 3.3).

**Q4.** `/memory` lists locations (including files that don't yet exist) and lets you
toggle auto memory. `/context` shows which memory files actually loaded into the
current session.


## Quiz — Lesson 3.2 (Slash Commands and Skills)

**Q1.** `.claude/commands/` and `.claude/skills/` are project-scoped: committed to
version control and shared with the whole team. `~/.claude/commands/` and
`~/.claude/skills/` are user-scoped: available across that user's own projects
but not shared with teammates.

**Q2.** It runs the skill in a forked subagent context instead of the main conversation;
only the subagent's summarized result returns to the main session. For a
codebase-analysis skill, this keeps the verbose intermediate output (file reads,
greps) out of the main conversation's token budget.

**Q3.** It pre-approves a specific set of tools for the turn that invokes the skill, so
Claude can use exactly those without a permission prompt (the grant clears at the
end of that turn). It does NOT block other tools from being used — those still
follow normal permission settings.

**Q4.** Create a personal skill in `~/.claude/skills/<different-name>/SKILL.md` (a
different name than the team's shared skill, so it doesn't collide with or
override it). It lives outside the repository and is invisible to teammates.

**Q5.** No — it should move to a skill. CLAUDE.md loads into every session automatically
and costs tokens whether or not it's relevant to the current task; a multi-step
procedure needed only occasionally belongs in a skill, which loads only on
demand.


## Quiz — Lesson 3.3 (Path-Specific Rules)

**Q1.** Having a `paths` field in its YAML frontmatter containing one or more glob
patterns. A rule with `paths` only applies (loads) when Claude works with files
matching one of those patterns; a rule without `paths` is unconditional and loads
at launch for every session.

**Q2.** A path-scoped rule only enters context when Claude reads a file matching its
pattern, so irrelevant conventions stay out of the context window on tasks that
never touch those files — unlike an unconditional CLAUDE.md, which is loaded
regardless of relevance on every session.

**Q3.** A path-specific rule with `paths: ["**/*.test.tsx"]`. The convention is defined
by file type, not by directory — a glob pattern applies it everywhere the file
type appears, whereas directory-level CLAUDE.md files would each need a nearly
identical copy placed in every directory that happens to contain test files.
