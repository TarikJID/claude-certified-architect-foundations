# Evaluation — course-builder fast-track Module 10 (5.5, 5.6) — round 4

- Output evaluated: /home/user/claude-certified-architect-foundations/Module_10_Human_Review_Confidence_and_Provenance/{fast-lesson.md, mcq.md, mcq-answers.md}
- Checklist: the 8 items given by the orchestrator (unchanged from round 3). Items 2, 6, 7, 8 judged against runs/claude-certified-architect-foundations/dispatch/fast-track-context-rework-brief.md.
- Source of truth used: research/context-management-reliability.md (5.5 and 5.6 concepts, 5.6 lines 308-358 re-read this round), domain-map.md and sources/exam-guide.txt as used in round 3 (bullet IDs and wording unchanged). Round-3 verdict read. No web fetch needed.
- Repeat round: yes
- Verdict: PASS

## Checklist results

| # | Checklist item | Result | Evidence or issue |
|---|----------------|--------|-------------------|
| 1 | Every 5.5/5.6 bullet ID taught and tested (totals) | PASS | 17 bullets (8 for 5.5, 9 for 5.6): 17 taught, 17 tested, 0 gaps. The Tests lines are unchanged from round 3 and cover K1, K2, K3, K4, S1, S2, S3, S4 for 5.5 and K1-K4, S1-S5 for 5.6. Each is taught in a lesson bullet. |
| 2 | fast-lesson blocks follow rule A, about 220 words | PASS | Exact counts, from "Setting:" to the last bullet, heading excluded. 5.5 = 218 (36 + 24 + 13 + bullets 25, 29, 52, 39). 5.6 = 219 (49 + 17 + 17 + bullets 44, 25, 24, 26, 17), or 217 if "+" is not counted. Both are within 220. Order is Setting, Before/after, Exam rule, bullets. 5.5 has 4 bullets and 5.6 has 5. One scenario per block. Each trap says what it looks like and why it fails. As in round 3, I read the scenario label as a name and not a sentence. |
| 3 | mcq.md: 4-5 Qs per statement, tagged, A-D, one best answer, no answer text | PASS | 5 questions for 5.5 and 5 for 5.6, 10 in total. All tagged, all have options A-D, and each has one best answer. The file has no answer text. |
| 4 | mcq and answers match as sets; each answer has letter, why, why each wrong option fails, bullet IDs | PASS | 10 questions and 10 answers, matching 1:1. Each has a Correct letter, a Why line, 3 wrong-option lines and a Tests line. Letters: 5.5 C, A, D, B, C and 5.6 B, D, A, C, D. |
| 5 | Answer keys correct; re-check 5.6 Q1, Q3, Q4 | PASS | 5.6 Q1 B matches the claim-source-excerpt mapping and the citations concept (research lines 313-322). 5.6 Q3 A matches the temporal-metadata concept (2023 with 500 and 2026 with 1,200 is growth, not conflict; lines 334-335). The "collection date" gloss is consistent with "publication or data-collection date". 5.6 Q4 C matches the well-established vs contested/single-source sections with each source's own context and method (lines 341-342). The wrong-option reasons are sound. The other 7 keys are unchanged and still match: 5.5 Q1 C, Q2 A, Q3 D (96% for date vs 82% for line-item total), Q4 B, Q5 C; 5.6 Q2 D, Q5 D. |
| 6 | Setups say plainly what the system is and what the data means | PASS | The 5.5 preamble says Claude reads documents and pulls out fields, and defines a field. The 5.6 preamble defines the coordinator, subagents and synthesis agent. Each question also defines its own data (confidence score, labeled validation set, line-item total, Type X/Y, digital and scanned PDFs, the dated reports). |
| 7 | Every question has an explicit deciding-constraint sentence | PASS | All 10 questions contain a sentence beginning "The deciding fact:". |
| 8 | Every technical term explained on first appearance; check calibrate, citations feature, contested, collection date | PASS (with note) | Calibrate: the heading carries "(testing what Claude's 'how sure' score really means)". Bullet 3 then says "Calibrate it: compare the scores with a labeled validation set (documents with known right answers) to learn what each score really means". "Calibrated confidence" in bullet 4 comes after that. Citations feature: 5.6 bullet 1 now says "it tags each sentence with the exact document text it came from". The same gloss appears in the 5.6 Q1 answer. Contested: glossed in 5.6 bullet 4 as "(sources disagree)" and in 5.6 Q4 option C. Collection date: glossed in 5.6 Q3 option A as "(the date the data was gathered)". Also explained: field, confidence score, validation set, segment, stratified random sampling, coordinator, subagent, synthesis agent, provenance, confidence cutoff (in 5.5 Q1 option B), digital and scanned PDF, high-confidence. Note, not a fail: "cutoff" in 5.5 Q2 option B and "review cutoff" in Q3 options A and D are not re-glossed. The gloss is in Q1 option B, and Q3's "separate review cutoff for each field" makes the meaning clear from context. The tutor may want to restate it if Q2 or Q3 is asked first. |

## Persisting issues

None. The round-3 item 8 failures (calibrate, citations feature, contested, collection date) are fixed. The round-1 issue (too many bullets per block) does not recur. No round 2 issue recurs.

## Not checked

- No web sources were fetched. The local research file and exam guide were treated as the source of truth.
- The builder's claimed counts were not used. I counted from the files directly.
