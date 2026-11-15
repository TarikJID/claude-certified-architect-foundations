CONTEXT REWORK BRIEF (learner feedback after Module 6)

The learner is NOT technical. Short blocks work, but he cannot build a mental picture: rules and traps arrive without the situation they come from.

Two real examples of the problem:
1. Lesson block: "Fields get dropped and phrasing drifts" - never says WHAT system produces the output. "Pair an acceptable pattern with a similar real issue" - he never sees either. One bullet silently switched from code review to invoice extraction. Traps were named ("confidence thresholds") but not explained.
2. Question: "A reviewer keeps flagging an intentional, common short-circuit coding pattern as a bug. The team also wants it to judge similar patterns it has never seen listed." - "short-circuit" never explained; and the deciding constraint (new variants not in any list must also be handled) was implied, not stated.

Rules for the revision:
A. fast-lesson.md, each block, in this order:
   - "Setting:" 2-3 plain sentences tied to ONE of the exam's scenarios: who uses what system, what it produces, what goes wrong.
   - One short before/after for that setting (plain words, no code; if code-ish, describe it in words).
   - "Exam rule:" then 3-5 bullets, each tied back to the setting. Each trap says what it would look like in practice and why it fails, in one line.
   - One scenario per block. If a bullet needs a different situation, give it its own one-line setting.
   - Every technical term gets a one-line plain explanation the first time it appears.
   - Max ~220 words per block (context is the point of the extra words, not more rules).
B. mcq.md: every setup says plainly what the system is and what each piece of data means, and states the deciding constraint as its own explicit sentence. No undefined jargon in setup or options. Keep A-D, one best answer, same tested ideas and bullet IDs, varied letter positions.
C. mcq-answers.md: keep in sync (letter, why, why each wrong option fails, bullet IDs), plain words.
D. Keep every bullet ID taught and tested. Do not touch lesson.md, quiz files, progress/ or any verdict file.
E. IMPORTANT: Read each file before writing it, and Read it back after writing. Earlier rounds lost edits because a Write failed silently. Report counts you verified from the re-read: words per block, bullets per block, questions and answers.
