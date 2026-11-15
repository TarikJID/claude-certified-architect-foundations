# Module 10 Fast Lesson

## 5.5 Human review and confidence calibration

**Setting:** Exam scenario "Structured Data Extraction". Claude reads invoices, contracts and handwritten receipts, pulling out fields (single pieces of data, like "invoice date"). Humans check the results. The team wants less checking without missing Claude's mistakes.

**Before/after:** Before: "97% correct overall, so stop all review." Inside: receipts are 60% correct. After: accuracy is measured per document type, and review stays only for receipts.

**Exam rule:** Measure accuracy per document type and field before removing human review.

- Stop review only for a segment (one slice, like "receipts") that checks out. Trap: trusting the 97% average. A small bad segment hides inside it.
- Humans check a random sample from every segment, high-confidence items included (stratified random sampling). Trap: checking only low-confidence items. A new mistake Claude is sure about is never seen.
- Give each field a confidence score (Claude's rating of how sure it is). Calibrate it on a labeled validation set (documents with known right answers). Trap: reading 0.9 as "90% correct". In tests, 0.9 meant 96% for dates but 82% for totals.
- Send an item to a human when calibrated confidence is low, or the document is unclear or contradicts itself (two pages, two end dates). Both together go first. Trap: equal priority for every flagged item wastes limited reviewer time.

## 5.6 Keeping sources attached in multi-source reports

**Setting:** Exam scenario "Multi-Agent Research System". A coordinator agent (the one in charge) sends subagents (helper agents) to search and read documents. A synthesis agent combines their results into one cited report. The risk: the link between each fact and its source (provenance) gets lost, and disagreements get hidden.

**Before/after:** Before: "Reports suggest the market is $4-5B." After: "$4.2B (Source A) and $5.1B (Source B), conflicting."

**Exam rule:** Every claim stays tied to its source into the report. When sources disagree, show both.

- Subagents return each finding as claim + source + quoted excerpt, and the synthesis agent keeps these pairs. Claude's citations feature does this. Trap: plain-text summaries. Claims merge and sources are lost.
- When credible sources disagree, keep both numbers with sources, marked as conflicting. The coordinator or reader decides. Trap: picking one, or averaging. Information is lost.
- Attach a publication date to every figure. 500 staff (2023) and 1,200 (2026) is growth, not conflict. Trap: no dates, so a false contradiction.
- Separate sections: well-established (several sources agree) and contested or single-source. Keep each source's own context and method. Trap: one confident tone hides weak claims.
- Tables for numbers, paragraphs for narrative, lists for technical requirements. Trap: all paragraphs. Numbers lose their columns.
