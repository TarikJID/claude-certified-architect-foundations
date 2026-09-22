# Module 4 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 3.1 (CLAUDE.md Hierarchy)

**Q1.** A new team member says "Claude never applies our lint standards." Where
should you check first, and why is this the most common cause of that complaint?

**Q2.** What does `@path/to/file` do inside a CLAUDE.md file, and relative to
what does the path resolve?

**Q3.** A 400-line CLAUDE.md covers testing, API conventions, and deployment.
What's the recommended restructuring, and what's the token-budget benefit?

**Q4.** Which command lists every CLAUDE.md/memory-file location Claude Code
recognizes, and which command confirms what actually loaded in the current
session?

---

## Quiz — Lesson 3.2 (Slash Commands and Skills)

**Q1.** What's the difference between a command/skill in `.claude/commands/` (or
`.claude/skills/`) versus `~/.claude/commands/` (or `~/.claude/skills/`)?

**Q2.** What does `context: fork` do when added to a skill's frontmatter, and why
would you use it for a codebase-analysis skill?

**Q3.** What does `allowed-tools` in skill frontmatter actually restrict, and
what does it NOT do?

**Q4.** An engineer wants a personal variant of the team's shared `/deploy`
skill without affecting teammates. What should they do?

**Q5.** A CLAUDE.md section has grown into a 40-step "migrate a service" procedure
needed only occasionally. Should it stay in CLAUDE.md? Why or why not?

---

## Quiz — Lesson 3.3 (Path-Specific Rules)

**Q1.** What makes a rule file in `.claude/rules/` "conditional" rather than
always-loaded?

**Q2.** Why does path-scoped loading save tokens compared to an unconditional
CLAUDE.md covering the same content?

**Q3.** All `*.test.tsx` files across a codebase (in `src/`, `lib/`, and `tools/`)
must follow the same testing convention. Should you use directory-level
CLAUDE.md files or a path-specific rule? Why?
