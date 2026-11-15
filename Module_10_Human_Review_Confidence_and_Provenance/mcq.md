# Module 10 Multiple-Choice Questions

Pick the single best answer. Answers are in `mcq-answers.md`. Do not open it before you answer.

---

## Task statement 5.5

All 5.5 questions use the same system. A company uses Claude to read documents (invoices, contracts, receipts) and pull out fields. A field is one piece of data, such as "invoice date" or "total". Humans currently check the results.

**Q1 [5.5]** The system handles invoices, contracts and handwritten receipts. Measured across all documents together, 97% of extracted fields are correct. Handwritten receipts are only 3% of the documents. The deciding fact: nobody has yet measured accuracy for each document type on its own. What should the team do before removing human review?

A. Remove review everywhere, because 97% correct is above the team's target.
B. Raise the confidence cutoff (the minimum "how sure" score needed to skip review) by the same amount for every document type.
C. Measure accuracy separately for each document type and each field, then decide where review can stop.
D. Ask Claude for one "how sure" score per whole document instead of one per field.

**Q2 [5.5]** Claude gives each field a confidence score, which is its own rating of how sure it is. Today humans check only the low-confidence fields, and they fix most of the mistakes they find. After a model update, Claude starts making a new kind of mistake while still giving high confidence. The deciding fact: these new mistakes never reach a human, because only low-confidence fields are checked. Which change best catches them?

A. Each month, humans check a random sample from every document type and every confidence level, high-confidence fields included.
B. Lower the cutoff so that slightly fewer fields go to humans.
C. Ask Claude to re-check its own high-confidence answers.
D. Check only fields from the document type with the most documents.

**Q3 [5.5]** Claude gives each field a confidence score from 0 to 1. The team tested it on a labeled validation set, which is a set of documents where the correct answers are already known. When Claude says 0.9 on "invoice date", it is right 96% of the time. When it says 0.9 on "line-item total" (the price on one row of the invoice), it is right only 82% of the time. The deciding fact: the same score means different real accuracy for different fields. What should the team do?

A. Use one review cutoff of 0.9 for all fields, since Claude reports the same score for both.
B. Replace the model, because its scores are wrong.
C. Stop using field scores and use one score for each whole document.
D. Set a separate review cutoff for each field from the measured results, with a stricter one for line-item totals.

**Q4 [5.5]** The system is now reading contracts. Reviewers can check 50 fields today, but 120 have been sent to them. Type X: Claude is unsure about a field, but the contract states it clearly. Type Y: Claude is unsure about a contract end date, and page 2 and page 9 of the contract give different end dates. The deciding fact: there is not time to check everything, so the least trustworthy fields must go first. Which should go first?

A. Type X, because the clear contract makes it quick to check.
B. Type Y, because Claude is unsure and the contract contradicts itself.
C. Both equally, since both were sent for review.
D. Neither. Let Claude pick one of the two dates.

**Q5 [5.5]** The team wants to stop human review for fields Claude is highly confident about. They measured each group separately. High-confidence fields from digital PDFs (files created on a computer) are 99% correct. High-confidence fields from scanned PDFs (photos of paper pages) are 85% correct. The deciding fact: only the digital group has been shown to be accurate enough to skip review. What should they do?

A. Keep review for all high-confidence fields, because one group is weak.
B. Stop review for both groups, because high-confidence fields are accurate on average.
C. Stop review for digital PDFs and keep it for scanned PDFs.
D. Stop review for scanned PDFs, because reviewers spend too long on them.

---

## Task statement 5.6

All 5.6 questions use the same system. A research system has a coordinator agent (the one in charge) that sends subagents (helper agents) to search the web and read documents. A synthesis agent then combines what they found into one report that says where each fact came from.

**Q1 [5.6]** Three subagents each return a paragraph of plain text. The synthesis agent combines the paragraphs into one short report. Two sources gave different numbers for the same statistic, and the report now says only "estimates fall in this range". The deciding fact: no reader can tell which source gave which number, and the short report does not contain enough to work it out. What is the best fix?

A. Ask the synthesis agent to write longer summaries.
B. Have each subagent return every finding as claim + source + quoted excerpt, and have the synthesis agent keep those pairs.
C. Tell the synthesis agent to always report the highest number.
D. Add a last step where Claude guesses the sources from memory.

**Q2 [5.6]** The document-reading subagent finds two credible sources. Source A says a market was worth $4.2 billion in 2025. Source B says the same market was worth $5.1 billion in 2025. The deciding fact: both describe the same market in the same year, so this is a real disagreement, and settling it is the coordinator's job, not the subagent's. What should the subagent send back to the coordinator?

A. Only the larger number, because it is probably more complete.
B. The average of the two numbers.
C. Only the number from the source it read first.
D. Both numbers, each with its source, marked as conflicting.

**Q3 [5.6]** One report, published in 2023, says a company has 500 employees. Another report, published in 2026, says 1,200. The subagents passed on the numbers but not the publication dates, so the synthesis agent reported a contradiction between the two sources. The deciding fact: both numbers were true when they were published. What would have prevented the false contradiction?

A. Require each subagent to send the publication date or collection date (the date the data was gathered) with every number.
B. Require subagents to send shorter outputs.
C. Delete the older source before combining.
D. Tell Claude to always prefer the larger number.

**Q4 [5.6]** The final report contains findings backed by three independent sources that agree, and one finding backed by a single, weaker source. Every sentence is written in the same confident tone. The deciding fact: the reader cannot tell which findings are solid and which are doubtful. Which report design fixes this?

A. Delete the single-source finding.
B. Put the strongest findings first and say nothing about how well each is supported.
C. Use one section for well-established findings and another for contested (sources disagree) or single-source findings, keeping each source's own context and method.
D. Add the word "likely" to every sentence.

**Q5 [5.6]** The report must contain three kinds of content: quarterly revenue numbers from several sources, a short story of how the market developed, and a list of technical rules a product must meet. The deciding fact: each kind of content has a format that shows it best. Which layout is best?

A. Everything as paragraphs.
B. Everything as bullet points.
C. Everything in one large table.
D. A comparison table for the revenue, paragraphs for the story, and a list for the technical rules.
