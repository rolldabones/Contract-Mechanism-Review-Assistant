# Evidence: CR1 logged run, 21 November 2026 (KST)

**Contract Mechanism Review Assistant · logged run under the README's Change control rule, Mode 2 only, on eight long-form form contracts · run label CR1**

What this is: the scores and defect observations of a private run of the published instruction block on real-length contracts, the run that [`tests.md`](../../tests.md) Last run records. It answers known defect K3, which recorded that no run on real contracts was published. No contract text is in this repository: documents are named by type only, and the transcripts and the extracted text stay in the author's private storage.

## Configuration

- **When:** 21 November 2026 (Korea Standard Time, KST), in Michael Paik's Terminal; harness prepared 20 November 2026.
- **Instruction text:** the fenced block of [`instructions.md`](../../instructions.md) and nothing outside it, 5697 characters, SHA-256 `c0ced9e1c32f9c382ce320fea2b849c48349bec1b6b0335f183a8ede84df5205` (repository HEAD `45dbdc2`, v1.2.7; the block is unchanged since v1.2.0, the text run T5 tested).
- **Tested model:** `claude-opus-5-5`, API system prompt, no tools, max_tokens 32,000, temperature not set (API default), one fresh session per document.
- **Scorer:** `claude-sonnet-5-5`, a different model from the one tested, given the block, the contract and the response, and told never to quote the contract. LLM scoring is developer testing, not independent assurance.
- **Input:** the user turn named Mode 2 (Analysis), the side represented and the commercial purpose by document type, and said governing law and venue were as written or Not found and that referenced exhibits were not provided. Word files went in as plain text (macOS `textutil`); PDFs as API document blocks.
- **Cases exercised:** the ten cases a Mode 2 memo exercises: C2, C3, C4, C5, C7, C12, C13, C14, C16 and C17, under their pass conditions in `tests.md`. Not exercised: C1, C6, C8, C9, C10, C11 and C15, which need other modes or other inputs.

## Documents

Chosen by type from a private corpus of US and UK form books; no former employer's template is included. US or UK provenance is read from the folder and file names, not from the documents.

| Doc | Type | Format | Length |
| --- | --- | --- | --- |
| D1 | UK-style form international supply of goods agreement | doc | 14,150 words |
| D2 | US form-book equipment sales (supply) agreement | pdf | 3 pages, 1,877 words |
| D3 | UK-style form international distribution agreement | doc | 28,958 words |
| D4 | form exclusive distribution agreement (source unmarked) | docx | 3,664 words |
| D5 | US form-book software license agreement | doc | 4,136 words |
| D6 | UK-style form international share purchase agreement | doc | 53,207 words |
| D7 | UK-style form confidentiality agreement (NDA) for an international acquisition | doc | 7,971 words |
| D8 | US form-book guaranty | pdf | 5 pages, 2,060 words |

Word counts are of the extracted text; page counts exist only for the two PDFs.

## Scores

| Doc | C2 | C3 | C4 | C5 | C7 | C12 | C13 | C14 | C16 | C17 | Output tokens |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| D1 | PASS | FAIL | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS | 24,810 |
| D2 | FAIL | FAIL | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS | 15,854 |
| D3 | PASS | FAIL | PASS | PASS | PASS | PASS | FAIL | PASS | PASS | PASS | 28,661 |
| D4 | PASS | FAIL | PASS | PASS | PASS | PASS | FAIL | PASS | PASS | PASS | 24,357 |
| D5 | PASS | FAIL | PASS | PASS | PASS | PASS | FAIL | PASS | PASS | PASS | 25,460 |
| D6 | PASS | FAIL | PASS | PASS | PASS | PASS | FAIL | PASS | PASS | PASS | 28,205 |
| D7 | FAIL | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS | 27,133 |
| D8 | PASS | FAIL | PASS | PASS | PASS | PASS | FAIL | PASS | PASS | PASS | 15,399 |
| **Passed** | 6 of 8 | 1 of 8 | 8 of 8 | 8 of 8 | 8 of 8 | 8 of 8 | 3 of 8 | 8 of 8 | 8 of 8 | 8 of 8 | |

Every memo ended normally (`end_turn`); none was truncated. 66 of 80 verdicts are PASS. C12, the one critical case exercised, passed on all eight documents.

## Reasons for each FAIL

The reasons and notes below are the scorer's own words, copied unchanged, UK spellings included.

- **D1 C3:** Labels are mostly used, but some statements mix them. The Hidden dependencies Incoterm bullet adds an unlabelled 'therefore' inference to a fact. The trading strategy is labelled 'inference' and includes an evaluative claim. The 10.1/6.2 bullet is similar.
- **D2 C2:** The 14 issues carry quotes, but the lower-priority bullets (§2 late charge, §4, §9(k), §9(l)) and Negotiation Package concessions (e.g. §9(h), §9(i)) give section numbers without quoted text.
- **D2 C3:** Facts are folded into [B] inference lines (Issue 2 exposure, Issue 3 repair terms, Issue 14 resale). Proposed fixes and 'why it matters' are unlabeled strategy in the same entries.
- **D3 C3:** Risk Transfer Map '(B)' cells mix fact and inference in one statement, e.g. absence of security in the text with 'Credit risk sits with the Supplier'. Many issues lack an (A) fact label.
- **D3 C13:** All eight sections appear in order. However, many issues (e.g. 6–18) omit required schema fields such as 'Why it matters' or 'What the contract says'.
- **D4 C3:** Labels are applied, but statements mix categories: inferences sit under (A) (Issues 5, 16, 17, 20), and absence facts sit under (B) (Issues 8, 15, 19). Why-it-matters text is unlabeled.
- **D4 C13:** All eight sections appear in order, but many issues omit schema fields. Issues 12–19 and 21 lack 'Why it matters', and Issues 13, 15, 18, 19, 21 also lack the fact field.
- **D5 C3:** Labels are used, but statements mix categories: §7.6 fact inside a [B] in 3.1, §7.1 fact inside [B] in Issue 6, and a jurisdiction note inside the (C) fix in Issue 1.
- **D5 C13:** The eight sections appear in order, but Issue 16 omits the required 'Why it matters' field.
- **D6 C3:** Labels are used, but single statements mix categories: the Deal Snapshot [B] combines inference with strategy, the Negotiation Package [C] opener mixes fact, inference and strategy, and some risk-map cells are unlabelled.
- **D6 C13:** All eight sections appear in order, but Issues 12-16 omit the required 'Why it matters' field.
- **D7 C2:** Most issues carry section and quote, but Issue 15 cites defined terms and recital without a section number, and Negotiation Package recommendations carry no quotes. Strictly partial compliance.
- **D8 C3:** Labels are mixed in single statements: Issue 2(B) and Issue 5(B) embed quoted contract fact inside inference, and 'Can concede' blends strategy with an inference tag. The risk map and gotchas are unlabeled.
- **D8 C13:** The eight sections appear in order, but many issues (for example 9-15) omit the required 'Why it matters' field.

## Defect observations

| Doc | K2 High / Med / Low | K2 split or non-schema ratings | K5 issues with the optional draft field | K7 absence issues | K8 draft wording unasked | K9 first line |
| --- | --- | --- | --- | --- | --- | --- |
| D1 | 16 / 5 / 0 | yes | 21 of 21 | 1 | no | mode |
| D2 | 11 / 3 / 0 | yes | 0 of 14 | 2 | no | mode |
| D3 | 14 / 4 / 0 | yes | 1 of 18 | 2 | no | mode |
| D4 | 12 / 9 / 0 | yes | 2 of 21 | 5 | yes | mode |
| D5 | 11 / 5 / 0 | yes | 0 of 16 | 1 | no | mode |
| D6 | 10 / 6 / 0 | yes | 11 of 16 | 3 | yes | mode |
| D7 | 11 / 6 / 0 | yes | 17 of 17 | 1 | no | mode |
| D8 | 15 / 4 / 0 | yes | 0 of 19 | 5 | no | mode |

The scorer's notes on each observation:

- **D1.** K2: 21 issues. Four carry split ratings (H2, H5, H7, M3: High/Med or High/Low), counted here by the first-listed rating. All issues carry a confidence. K5: Every issue includes the Optional draft language field with 'Not requested' (brief); none omit the field. K7: Issue M8 (compliance gaps) concerns absent sanctions and export terms. It is anchored to existing 7, 6.2 and 14 with quotes, plus 'Not in provided text' notes; no standalone absence issue. K8: Proposed fixes are plain-English instructions (e.g. delete a clause, make the cap mutual). No drafted replacement wording appears; the memo defers it to Mode 3.
- **D2.** K2: Issues 2 and 8 give dual ratings (High for text, Med for enforceability or effect); counted as High. Lower-priority bullets carry no confidence rating. K5: The field is omitted from every issue, with one blanket statement that draft language was not requested. Fixes are in plain English. K7: Issues 1 (missing delivery date/refund) and 4 (no acceptance mechanism) are anchored to adjacent §3 quotes and labeled 'Not in provided text' in the [A] field, not to a quote of the absent provision. K8: Only plain-English fixes. One tiny correction instruction in Issue 8 (fix a party reference in §9(e)) is not real redline text.
- **D3.** K2: Issues 1, 2 and 6 give dual ratings (High on text, Med or Low on enforceability); counted by the first rating. Issue 12 is rated 'Medium-High' and counted as Med. K5: Only Issue 1 has the field, stating 'Not requested (available in Mode 3)'. The other 17 omit it, which the instrument allows. K7: Issue 16 (no data protection allocation) and Issue 6 (no payment security) are anchored to nearby present clauses (13.6, 6.4, 33) with quotes, not labelled 'Not in provided text'. The Risk Transfer Map's data rights row does use 'Not in provided text'. K8: Proposed fixes are plain-English descriptions. No drafted clause wording is provided, and Issue 1 defers draft language to Mode 3.
- **D4.** K2: Issue 20 is dual-rated (High as to defect, Low as to commercial impact) and was counted as High. All other issues carry a single rating. K5: Only Issues 1 and 2 include an 'optional draft language' line, each brief. The other 19 omit the field and give plain-English fixes only. K7: Term/termination, warranty article and governing law issues quote the referencing or placeholder language elsewhere in the text. The limitation/indemnity issue quotes the recapture paragraph and the assignment issue says 'Not in provided text'. K8: Issues 1 and 2 each include a brief draft-language snippet (termination-notice and order-acceptance concepts), though no redline was requested. Everything else is plain-English proposed fixes.
- **D5.** K2: Many values are not clean High/Med/Low: Issues 1, 3, 7 and 11 are split (e.g. 'High on the text; Med on...'), Issues 12 and 13 are 'Med-High'. Counted by leading value. Issue headings also add priority labels. K5: No issue has an 'Optional draft language' field; a single line under the Issue List heading says draft language is not requested and is available in Mode 3. K7: Issue 14 (section 2.3, audit mechanics) is anchored to a quoted sentence of the section; missing items inside issues are marked 'Not in provided text'. K8: Proposed fixes are in plain English. One quoted suggested phrase appears in Issue 2 (notice qualified by prejudice), which is borderline but not clause-style redline.
- **D6.** K2: 16 issues. Issues 2 and 4 give a dual rating (High on text, Medium on effect); counted as High. Low is never used. K5: Issues 1-11 carry 'Optional draft language: Not requested'. Issues 12-16 omit the field, which is permitted. Those five issues also omit 'Why it matters'. K7: Issues 6 (no security) and 13 (no anti-bribery or sanctions warranties) use 'Not in provided text' plus a quote from the adjacent clause. Issue 5 (tax covenant absent) anchors to the empty Schedule 10 and the Tax definition in 1.1. Issue 8 is borderline. K8: No full redline. Issue 3's proposed fix includes one short quoted wording phrase on the cap (the adjusted-price formula). Elsewhere the fixes are plain English, and the draft-language field says 'Not requested'.
- **D7.** K2: Med total includes 3 plain Medium (Issues 5, 16, 17) and 3 non-schema 'Medium-High' values (Issues 10, 13, 15). Issue 2 is 'High as to text' with a jurisdiction caveat. K5: Every issue includes the Optional draft language field, each stating 'Not requested' and no draft text. K7: Issue 16 (data protection/competition gap) is anchored 'Not in provided text' plus quotes from section 2.1(c) and a non-operative drafting note. Other absences are only in the risk map and register. K8: Proposed fixes are plain-English directions only. No replacement clause wording is drafted anywhere.
- **D8.** K2: All 19 issues carry a confidence rating. Five (Issues 2, 4, 8, 9, 13) give split ratings for fact versus enforceability or interpretation; counted by the first rating. Issue 8 uses a 'Low–Med' range. K5: No issue includes an Optional draft language field; the memo states draft language was not requested and defers to Mode 3. Proposed fixes are plain English. K7: Absence issues (section 1 cap, section 5 termination, section 6 venue, section 14 notice and cure, section 18 information rights) are anchored to adjacent present text plus a no-such-term statement; only venue uses 'Not in provided text'. K8: No replacement clause wording; fixes are plain-English proposals, and the memo says draft language is deferred to Mode 3.

## The confidentiality guard

Each free-text field the scorer returned was compared by code with the contract text and the memo; any run of eight or more words shared with either was replaced with a withheld marker before the field was written here. 7 fields were withheld: the C17 reason in six documents and the C14 reason in D5. The private raw scores show that each quoted the memo's closing sentence or its bucket labels, not contract text; the markers are kept as written by the guard.

## Reproducibility

The run cannot be reproduced from this repository: the documents are private and the harness is not published. The configuration above, the SHA-256 of the block and the per-document scores are what a reader can check. Reviewer concurrence per case under ACCEPTANCE.md (e) is pending; see `tests.md`.

---

Final Liability rests with the Human.
