# Evaluation — course-builder fast-track Module 7 (4.4, 4.5, 4.6) — round 2

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_7_Extraction_Quality_Batching_and_Review_Architectures/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: course-builder fast-track checklist (7 items, unchanged from round 1)
- Source of truth used: round-1 verdict (read); current fast-lesson.md (read in full). mcq.md and mcq-answers.md were reported unchanged, and I did not re-read them. I carried the round-1 results for them forward.
- Repeat round: yes
- Verdict: REWORK

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every bullet ID taught and tested (totals) | PASS | Totals are unchanged from round 1: 22 bullets in the map, 22 tested. The merge was supposed to cut bullets. The current fast-lesson.md still has every concept a bullet ID needs: retry with specific error, absent info, semantic vs syntax, calculated_total, conflict_detected, detected_pattern, batch vs sync, no tool loop, custom_id, resubmit failures, SLA maths, sample test, self-review, per-file plus cross-file, confidence routing. |
| 2 | One block per statement, <=150 words, Exam rule, 3-5 bullets, <=1 tiny example, short plain sentences | FAIL | The 4.4 block still has 6 bullets (lines 7-12: Pick, Reject, Do not retry, Tool use, calculated_total, detected_pattern). The 4.5 block still has 7 bullets (lines 22-28: Pick batch, Pick synchronous, Batch cannot, custom_id, On failures, SLA maths, Test the prompt). Only 4.6 has 5 bullets. The file does not show the claimed merge to 5 per block. Each block has an Exam rule, and at most one example each. I did not complete an exact word count, because the bullet failure already decides the item. |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, no answers, no code/wording recall | PASS | Carried from round 1 (15 questions, 5 per statement). The file is reported unchanged. |
| 4 | mcq.md and mcq-answers.md match as sets; answer format | PASS | Carried from round 1 (15 and 15, matching labels, full format). The files are reported unchanged. |
| 5 | Every tested concept taught | PASS | Every concept the questions test is still present in the current fast-lesson.md (see item 1). |
| 6 | Facts faithful; keys correct | PASS | Carried from round 1. The fast-lesson wording is the same as before, including the SLA line "6 hours or less (the guide uses 4)". |
| 7 | UNSOURCED concepts marked unverified | PASS | The research file has no UNSOURCED markers (round 1). |

## Persisting issues

- Item 2, bullet count above 5 in the 4.4 block (6) and the 4.5 block (7). It was first raised in round 1 and is unchanged in the file I read. The builder's report of merging to 5 bullets per block does not match this file.

## Not checked

- Exact word counts per block, because the bullet failure already decides item 2.
- mcq.md and mcq-answers.md were not re-read. I relied on the report that they were unchanged.
- I did not check git history to see whether the fast-lesson.md edit was saved.

## Fix required for rework

Reduce the 4.4 block to 5 or fewer bullets (now 6) and the 4.5 block to 5 or fewer (now 7). Keep every block at or under 150 words, and keep every concept taught.
