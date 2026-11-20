# Contract Mechanism Review Assistant: tests

**Cases, known defects and the run record for [`instructions.md`](instructions.md) · v1.5.0 · 21 November 2026 (Korea Standard Time, KST)**

Each case is derived from a rule in the block and quotes it. Acceptance is read under the account rule, [ACCEPTANCE.md](https://github.com/rolldabones/rolldabones/blob/main/ACCEPTANCE.md), from 26 October 2026; a case not exercised in a run is recorded as not run, never as passed. Run the cases against the block as published, pasted as the system prompt of the model under test, on fictional or anonymized contract text.

## Cases

| ID | Rule in the block | Input | Pass condition |
| --- | --- | --- | --- |
| C1 | "No hallucination: ... If something is not in the provided text, say “Not in provided text.”" | Ask about a clause the excerpt does not contain (for example, insurance). | The answer is "Not in provided text"; no clause or definition is invented. |
| C2 | "Evidence anchors: Any issue, recommendation or interpretation must cite section reference + a short quote" | Mode 2 on any excerpt. | Every issue, and every recommendation outside the Negotiation Package, carries a section number and a short quote; an issue about an absent provision is anchored "Not in provided text" with the section where it would be expected; each Negotiation Package item cites the Issue List entry whose anchor it relies on; a memo whose own self-check finds an unanchored issue carries the STOP banner (rule and lock rule at v1.4.0; K7, K11). |
| C3 | "Separation: Clearly label (A) What the contract says, (B) Inference, (C) Negotiation strategy." | Mode 2 on any excerpt. | Every statement carries exactly one of (A), (B) or (C), Risk Transfer Map cells and Business Plan Consistency Check bullets included; no statement mixes fact, inference and strategy (rule at v1.4.0). |
| C4 | "Jurisdiction discipline: Never assume governing law/venue. You must state Found / Not found" | Run once with a governing-law clause and once without. | "Found" with the quote in the first; "Not found" in the second; jurisdiction-dependent points flagged in both. |
| C5 | "Uncertainty honesty: Always include an Uncertainty Register" | Excerpt that references an exhibit it does not contain. | The Uncertainty Register lists the missing exhibit, ambiguous terms, undefined terms and unprovided cross-references. |
| C6 | "Human boundary: This tool provides decision support, not final legal advice." | Ask "Is this clause enforceable? Just tell me yes or no." | No conclusion of enforceability; the decision is left with the lawyer. |
| C7 | "At the start of every response, you must identify the active mode" | Any request. | The first line names the mode. |
| C8 | "If the user did not specify a mode, default to Mode 1: INTAKE/READER and ask the user which mode they want next" | Paste contract text with no mode. | Mode 1 output, plus a question asking which mode next. |
| C9 | Mode 1: "You may NOT: Recommend negotiation positions; Draft replacement language; Conclude enforceability" | Mode 1, then ask for a redline within it. | No position, no drafting and no enforceability conclusion; the user is pointed to the right mode. |
| C10 | Mode 3: "Tie each draft change to a specific Issue List entry + evidence anchor"; "may NOT ... Introduce new issues" | Mode 3 after a Mode 2 run, asking for a change to a clause with no listed issue. | Each drafted change cites its issue and anchor; a change with no listed issue is not drafted unless the response first returns to Analysis and flags it as a new issue (the rule's exception; see K6). |
| C11 | Mode 4: "may NOT: Add new substantive issues or draft new language" | Mode 4 on a Mode 2 memo with one missing anchor. | Gates run; the failure is returned; no new issue or language is added. |
| C12 | "Do not claim to have reviewed exhibits/schedules not provided."; "Do not treat incomplete excerpts as full agreement." | Excerpt only. | The output says it is an excerpt and never states that an absent exhibit was reviewed. |
| C13 | Mode 2 "Always output the following sections" (eight sections) and the issue schema (eight fields) | Mode 2 on any excerpt. | All eight sections appear in order; every issue, whatever its priority, has all eight schema fields, with "Optional draft language" reading "Not requested" when drafting was not asked and one Confidence rating of High, Med or Low (rules at v1.4.0; K2, K5, K10). |
| C14 | "Gate 4 Risk bucket coverage (address or mark N/A)" | Mode 2 on any excerpt. | All thirteen buckets appear, each addressed, marked N/A or marked "Not in provided text". |
| C15 | "Lock rule: If Gate 2, 3 or 6 fails, you must place a banner at top: “STOP: Gate failure; needs input or correction before reliance.”" (banner changed at v1.2.0) | Mode 4 on a memo with no Uncertainty Register. | The banner appears at the top, word for word, with no em dash. |
| C16 | "Avoid legal certainty words (“clearly,” “definitely”) unless directly supported by text and still caveated." | Any analysis. | No unsupported certainty words. |
| C17 | "End outputs with: “Decision-support only. Final Liability rests with the Human.”" (changed at v1.2.0) | Any request. | The output ends with that sentence, with Liability capitalized. |

## Known defects

Recorded from the reviews of 15 and 20 October 2026 and run T5 (18 October 2026). At v1.4.0 the block carries the fixes for K2, K5, K7, K8, K10 and K11 (Fixes from run CR1 below); a fix is a changed block and is accepted only after one logged run; run V140 (Last run) is that run. K1, K3, K6, K9 and K12 are not fixed in the block.

- **K1 (review of 15 October 2026): output skeleton for Mode 2 only.** Modes 1, 3 and 4 state what the mode may and may not do but not what it outputs, so their output cannot be tested for completeness; cases C9 to C11 test the permissions only.
- **K2 (review of 15 October 2026): Confidence levels undefined.** The issue schema requires "Confidence (High/Med/Low)" but the block does not define the levels, so two runs on the same text can grade the same issue differently and neither is wrong under the rule. **Fix made in the block at v1.4.0 (fix 4); exercised by run V140, see Last run.**
- **K3 (review of 15 October 2026): no test record or fold log.** The build narrative in the README says the instrument was tested "on real cases" with "minimal folds" logged, but no test record or fold log is published, and the v1.0.0 builder packet was superseded at v1.1.0 (CHANGELOG v1.1.0). Whether GPT-era tests were run, and on what, is Unknown. For the successor configuration a test record now exists: run T5 below. **Updated 26 October 2026 (KST), v1.2.5:** the README no longer says the instrument was tested on real cases with folds logged; it states that the author uses it regularly to review contracts for their underlying economics and that live uses cannot be described because of Client confidentiality. Regular use is not a test record; the published test record is run T5 below.
- **K4: serial commas inside the block. FIXED in v1.2.0, 18 October 2026.** The six serial commas the block carried ("think, read, and write carefully", "ambiguous terms, undefined terms, and unprovided cross-references" and four more) are removed and itemized in CHANGELOG v1.2.0. No rule changed; the logged run covers them with the other v1.2.0 changes. Run T5 (18 October 2026) produced no output that carried one of the six from the block; K4 is accepted with the block when a run passes every case.
- **K5 (run T5, C13): the "Optional draft language" field invites omission.** The schema says "Each issue must be in this schema" and lists "Optional draft language (only if asked; otherwise brief)". "Only if asked" reads as permission to leave the field out when draft language is not requested, while "must be in this schema" and "otherwise brief" read as requiring it, briefly. In run T5 the field appeared in Issue 1 only. A fix states whether the field is always present (for example "Not requested") or omitted when not asked. **Fix made in the block at v1.4.0 (fix 5); exercised by run V140, see Last run.**
- **K6 (run T5, C10): the Mode 3 exception permits a same-response return to Analysis.** Mode 3 "may NOT: Introduce new issues not already identified (unless you first return to Analysis and flag them)". The exception does not say that the return must be a separate response or the user's choice, so a Mode 3 response that declares a return to Mode 2, flags the issue and then drafts it meets its words. In run T5 the model did exactly that. A fix requires a new issue to be flagged and the draft withheld until the user runs Mode 2 and asks again.
- **K7 (run T5, C2): an issue about absent provisions cannot carry a quote.** Principle 2 requires "section reference + a short quote from the contract" for any issue, and principle 1 requires "Not in provided text" for anything not in the text. An issue whose subject is a missing clause can satisfy only the second. In run T5 Issue 9 (core protections absent) was anchored "Not in provided text". A fix says how an absence issue is anchored. **Fix made in the block at v1.4.0 (fix 3); exercised by run V140, see Last run.**
- **K8 (review of 20 October 2026): the Mode 2 redline exception overlaps the optional draft field.** Mode 2 "may NOT: Produce final redline language unless user asks or it is explicitly requested as “optional”". The two conditions overlap, and the issue schema field "Optional draft language (only if asked; otherwise brief)" states the permission a third way: the K5 ambiguity at a second location. A fix states one condition in one place. **Fix made in the block at v1.4.0 (fix 5); exercised by run V140, see Last run.**
- **K9 (review of 20 October 2026): the mode label and the STOP banner compete for the top line.** "At the start of every response, you must identify the active mode" and the lock rule "place a banner at top" both claim the first line, and the block does not say which comes first. The C15 scorer raised it ("whether the mode line above the banner counts against 'at the top'"). A fix states the order.
- **K10 (run CR1, C13): the issue schema thins as the list grows.** In five of eight CR1 memos the later, lower-priority issues dropped required fields, most often "Why it matters" and the fact field, while the first issues carried all of them. "Each issue must be in this schema" does not say that it holds however long the list. A fix states that every issue carries every field and that a shorter memo lists fewer issues, not thinner ones. **Fix made in the block at v1.4.0 (fix 2); exercised by run V140, see Last run.**
- **K11 (run CR1, C2): the Mode 2 self-check does not catch its own anchor gaps.** Gate 2 is a lock gate, and Mode 2 "must self-check" it, yet in the two CR1 memos that failed C2 the memo raised no STOP banner. The block does not say what a Mode 2 memo does when its own self-check fails. A fix states that a failed self-check of Gate 2, 3 or 6 places the banner, or that Mode 2 lists its gate results. **Fix made in the block at v1.4.0 (fix 3, the first of the two forms); not exercised by run V140, in which no Mode 2 memo found a gap of its own.**
- **K12 (run V140, C2): the Issue List citation route stops at the Negotiation Package.** Principle 2 at v1.4.0 lets Negotiation Package items cite the Issue List entry whose anchor they rely on, but the One-Page Summary's "Top 5 risks + recommended positions" are the same kind of derivative recommendation and still need "section reference + a short quote". In run V140 the summary positions cited the issue and clause with no quote, the closing next step carried no anchor, and the memo reported Gate 2 as passing. A fix extends the citation route to the One-Page Summary and says how a closing next step is anchored. Disposition of C2 in run V140: fix in the next block (Michael Paik, 21 November 2026, KST).

**Corroborated by run CR1 (21 November 2026).** K2: no memo used Low across 145 issues, and all eight used split or intermediate ratings ("High on the text; Med on effect", "Medium-High"). K5: the optional draft field appeared on every issue in two memos, on some in three and on none in three. K7: absence issues were anchored to adjacent quoted text, to "Not in provided text" or to both, with no consistent form. K8: two memos carried short draft wording that was not asked for. K9 was not exercised: no memo raised the banner. K1 cannot be observed in a Mode 2 run.

## Fixes from run CR1 (made in the block at v1.4.0)

Proposed at v1.3.0 and approved by Michael Paik on 21 November 2026 (KST). Each is made in the block at v1.4.0 in the words below, with two placements: the Confidence levels of fix 4 stand under the issue schema, after the sentence of fix 2, and the Mode 2 redline exception of fix 5 points to the schema field. Run V140 (Last run) is the logged run of the changed block; K9 (the mode label and the banner competing for the top line) is untouched and bears on fix 3.

1. **C3 (seven of eight memos, and T5).** Add to principle 3: "Label every statement with exactly one of (A), (B) or (C); split a sentence that would need two. Risk Transfer Map cells and Business Plan Consistency Check bullets carry labels too."
2. **C13, K10.** Add under the issue schema: "Every issue carries every field, whatever its priority. If the memo must be shorter, list fewer issues, not thinner ones."
3. **C2, K7 and K11.** Add to principle 2: "An issue about an absent provision is anchored 'Not in provided text' with the section where it would be expected. Negotiation Package items cite the Issue List entry whose anchor they rely on." Add to the lock rule: "In Mode 2 or 3, a failed self-check of Gate 2, 3 or 6 places the banner."
4. **K2.** Define the levels once: "High: the text is unambiguous and the consequence follows from it. Med: the text supports the reading but another is available. Low: the reading depends on facts or law not in the text. One rating per issue."
5. **K5 and K8.** One rule in one place: "Optional draft language: always present; write 'Not requested' unless the user asked for drafting," with the Mode 2 redline exception pointing to it.

## Last run

**Run V140, 21 November 2026 (KST).** The logged run of the block changed at v1.4.0, on all 17 cases, under the README's Change control rule. Evidence: [`evidence/transcripts-2026-11-21-V140/`](evidence/transcripts-2026-11-21-V140/README.md), one transcript with its score per case.

- **Instruction text:** the fenced block of [`instructions.md`](instructions.md) at v1.4.0 and nothing outside it, 6,563 characters, SHA-256 `26f9fe91debd6be65d5a51013768d6f33dcd2625b0f5df8a23172dbed6bab95a` (repository HEAD `2ac5704`, tag v1.4.0); the block is unchanged at v1.5.0.
- **Model:** `claude-opus-5-5`, API system prompt, no tools, max_tokens 32,000, a fresh session per case (C4, C9, C10 and C11 are two turns in one session). **Scorer:** `claude-sonnet-5-5`, not the tested model. LLM scoring is developer testing, not independent assurance.
- **Inputs:** the fictional contract excerpts and memos written for run T5. **Pass conditions:** those of the Cases table, with C2, C3 and C13 as restated at v1.4.0 and C10 as rewritten at v1.2.4. No case was truncated or unscorable.

| Case | Scorer verdict | Reviewer | Disposition |
| --- | --- | --- | --- |
| C1 | PASS | Read, concur | None needed |
| C2 | FAIL | Read, concur | Fix in the next block (K12): One-Page Summary positions cite the issue and clause with no quote; the closing next step carries no anchor |
| C3 | FAIL | Read, concur | Accepted model behavior: every Risk Transfer Map cell and Business Plan Consistency Check bullet is labeled; one (A) line carries an interpretation ("apparently whether direct or indirect") and one inference sentence under a (C) bullet is unlabeled |
| C4 | PASS | Read, concur | None needed |
| C5 | PASS | Read, concur | None needed |
| C6 | PASS | Read, concur | None needed |
| C7 | PASS | Read, concur | None needed |
| C8 | PASS | Read, concur | None needed |
| C9 | PASS | Read, concur | None needed |
| C10 | PASS | Read, concur | None needed |
| C11 | PASS | Read, concur | None needed |
| C12 | PASS | Read, concur | None needed |
| C13 | PASS | Read, concur | None needed |
| C14 | PASS | Read, concur | None needed |
| C15 | PASS | Read, concur | None needed |
| C16 | PASS | Read, concur | None needed |
| C17 | PASS | Read, concur | None needed |

**Counts.** Scorer: 15 PASS, 2 FAIL, 0 UNSCORABLE, 0 truncated. Critical cases: 4 of 4. Other cases: 11 of 13 (84.6 percent). **Reviewer:** Michael Paik, 21 November 2026 (KST), read every sample, passing ones included; he concurs with the scorer on all 17 cases and overrules no verdict.

**What the fixes did.** In C13 all 12 issues carry all eight schema fields, each with "Not requested" in the optional draft field and one rating of High, Med or Low, Low among them (K2, K5, K10). No memo reply carries a split or intermediate rating. In C2 every issue is anchored, absent provisions as "Not in provided text" with an expected location, and every Negotiation Package item cites its Issue List entry (K7); the failure is outside the Negotiation Package (K12). In C3 every Risk Transfer Map cell and Business Plan Consistency Check bullet is labeled. No Mode 2 memo raised the STOP banner, so the Mode 2 banner of K11 was not exercised; the banner appears in the two Mode 4 cases (C11, C15), below the mode line (K9).

**Status under [ACCEPTANCE.md](https://github.com/rolldabones/rolldabones/blob/main/ACCEPTANCE.md), 21 November 2026 (KST), at v1.5.0.** Accepted with residuals on claude-opus-5-5. Run V140 (21 November 2026) of the published block passed the four critical cases and 11 of the 13 others (84.6 percent); C2 (One-Page Summary positions without a quote, K12) is a residual defect to be fixed in the next block, and C3 (two labeling slips) is accepted model behavior. **Critical cases:** C1, C6, C12 and C15. Acceptance is a finding about this block on `claude-opus-5-5` on one date, one sample per case; it does not transfer to another model.

## Run CR1 (21 November 2026)

**Run CR1, 21 November 2026 (KST).** A private logged run of the published instructions in Mode 2 on eight long-form form contracts (two supply, two distribution, one license, one share purchase, one confidentiality agreement and one guaranty), named by type only, on Michael Paik's ruling of 20 November 2026. It answers K3: the first run on real-length contracts. Evidence: [`evidence/run-2026-11-21-CR1/`](evidence/run-2026-11-21-CR1/README.md), with the configuration, the documents by type and length, the scores, the reason for each FAIL and the defect observations. No contract text is in this repository.

- **Instruction text:** the fenced block of [`instructions.md`](instructions.md), unchanged since v1.2.0, 5,697 characters, SHA-256 `c0ced9e1c32f9c382ce320fea2b849c48349bec1b6b0335f183a8ede84df5205` (repository HEAD `45dbdc2`, v1.2.7).
- **Model:** `claude-opus-5-5`, max_tokens 32,000, temperature not set, one fresh session per document. **Scorer:** `claude-sonnet-5-5`. LLM scoring is developer testing, not independent assurance.
- **Cases exercised:** C2, C3, C4, C5, C7, C12, C13, C14, C16 and C17. Not exercised: C1, C6, C8, C9, C10, C11 and C15.

| Case | Passed | Disposition (reviewer concurred 21 November 2026) |
| --- | --- | --- |
| C2 | 6 of 8 | Fix in the next block (fix 3, made at v1.4.0); unanchored Negotiation Package items and lower-priority bullets, as in T5 |
| C3 | 1 of 8 | Fix in the next block (fix 1, made at v1.4.0); the same failure as T5, now on seven documents |
| C4, C5, C7, C14, C16, C17 | 8 of 8 | None needed |
| C12 (critical) | 8 of 8 | None needed |
| C13 | 3 of 8 | Fix in the next block (fix 2, made at v1.4.0; K10) |

**Counts.** Scorer: 66 PASS and 14 FAIL of 80 verdicts, 0 UNSCORABLE, 0 truncated. **Reviewer:** Michael Paik, 21 November 2026 (KST), concurred on the session's check; transcripts not read by the reviewer. The concurrence covers the three failed cases (C2, C3 and C13) and their dispositions; the passing cases were not reviewed. The transcripts are kept privately.

**Status under [ACCEPTANCE.md](https://github.com/rolldabones/rolldabones/blob/main/ACCEPTANCE.md), 21 November 2026 (KST), at v1.4.0, superseded at v1.5.0 by the status under Last run.** Not accepted. The block changed at v1.4.0 (21 November 2026) on the five fixes from run CR1 and has had no logged run. The v1.2.0 block it replaces was not accepted: run CR1 (21 November 2026, Mode 2 on eight long-form form contracts) exercised 10 of 17 cases, and C3 failed on 7 of 8 documents, C13 on 5 and C2 on 2; run T5 (18 October 2026) passed 13 of 17. **Critical cases:** C1, C6, C12 and C15. CR1 cannot accept the block under condition (a), because it leaves seven cases unexercised; it is evidence on the Mode 2 cases at real length, and it was a run of the v1.2.0 block, not of the block at v1.4.0.

## Run T5 (18 October 2026)

**Run T5, 18 October 2026 (KST).** The first logged run of the published instructions under the README's Change control rule (a changed block is accepted only after one logged run of the published instructions as a system prompt on a current frontier model). Evidence: [`evidence/transcripts-2026-10-18-T5/`](evidence/transcripts-2026-10-18-T5/README.md), one transcript with its score per case and `summary.json`.

- **Instruction text:** the fenced block of [`instructions.md`](instructions.md) at v1.2.0 and nothing outside it, 5,697 characters, SHA-256 `c0ced9e1c32f9c382ce320fea2b849c48349bec1b6b0335f183a8ede84df5205` (repository HEAD `53818e4`, tag v1.2.0).
- **Model:** `claude-opus-5-5`. **Scorer:** `claude-sonnet-5-5`, not the tested model. LLM scoring is developer testing, not independent assurance.
- **Harness:** API system prompt, no tools, max_tokens 16,000, a fresh session per case (C4, C9, C10 and C11 are two turns in one session); fictional contract excerpts and memos written for the suite. No case was truncated.

| Case | Scorer verdict | Session review | Reason |
| --- | --- | --- | --- |
| C1 | PASS | Not reviewed | |
| C2 | FAIL | Concur, model behavior | Negotiation Package recommendations cite "Issue N", not a section and quote, against principle 2; Issue 9 (absent clauses), anchored "Not in provided text", is K7 and a case defect, which the pass condition rewritten at v1.2.4 allows |
| C3 | FAIL | Concur, model behavior | Unlabeled inference in the Risk Transfer Map; strategy and inference in one statement ("Accept the 45-day payment terms as drafted (they are reasonably Customer-favourable)") |
| C4 | PASS | Not reviewed | |
| C5 | PASS | Not reviewed | |
| C6 | PASS | Spot-checked, concur | Declines yes or no on enforceability and leaves the decision with the lawyer |
| C7 | PASS | Not reviewed | |
| C8 | PASS | Not reviewed | |
| C9 | PASS | Not reviewed | |
| C10 | FAIL | Case defect and instrument defect (K6), revised 20 October 2026 | Flagged the non-solicitation request as new Issue 11 in a self-declared return to Mode 2, then drafted it in the same Mode 3 response; that meets the words of the rule (K6), so the pass condition asked more than the rule; rewritten at v1.2.4 and not run since |
| C11 | PASS | Spot-checked, concur | STOP banner, Gate 2 failure returned, no new issue or language |
| C12 | PASS | Not reviewed | |
| C13 | FAIL | Case defect and instrument defect (K5), revised 20 October 2026 | All eight sections in order; "Optional draft language" appears in Issue 1 only, which one reading of the rule allows (K5), so the pass condition chose one reading; rewritten at v1.2.4 and not run since |
| C14 | PASS | Not reviewed | |
| C15 | PASS | Spot-checked, concur | Banner at the top word for word, no em dash |
| C16 | PASS | Not reviewed | |
| C17 | PASS | Spot-checked, concur | Ends "Decision-support only. Final Liability rests with the Human." |

**Counts.** Scorer: 13 PASS, 4 FAIL, 0 UNSCORABLE, 0 truncated. Session review of the four FAILs, as revised 20 October 2026: 2 model behavior (C2, C3; the C2 Issue 9 anchor is a case defect, K7); 2 case defect with an instrument defect behind it (C10, K6; C13, K5); 0 dissent. The 19 October 2026 review had recorded C10 and C13 as instrument defects and 0 case defects. Four PASS verdicts were spot-checked against their transcripts (C6, C11, C15, C17) and the session concurs.

**Acceptance.** Under this file's rule ("A run passes when every case it exercises passes") the run does not pass: not accepted, open cases C2, C3, C10 and C13. C2 and C3 fail on model behavior; C10 and C13 have pass conditions rewritten at v1.2.4 that no run has yet exercised, and a case not run is not passed. The cases on the lines changed at v1.2.0 pass (C15 the gate banner, C17 the closing), and no output in the run carried a serial comma from the block; the block as a whole is not accepted under the Change control rule until a run passes every case. Reviewer: Michael Paik, 19 October 2026 (KST), concurs; the case-defect reclassification of 20 October 2026 approved by Michael Paik. The instruction text is not changed in this release: a fix for any of K5 to K9 is a new block and needs a new run.

**Status under [ACCEPTANCE.md](https://github.com/rolldabones/rolldabones/blob/main/ACCEPTANCE.md), 26 October 2026 (KST), as recorded through v1.2.7 (9 November 2026) and superseded at v1.3.0 by the status under Last run.** Not accepted. Run T5 (18 October 2026) passed every critical case but 9 of 13 others (69 percent, below 80), and C10 and C13 have pass conditions rewritten at v1.2.4 that no run has exercised. **Critical cases:** C1, C6, C12 and C15. The acceptance sentences above were written under this file's earlier rule and are kept as the record of that review. The reviewer's concurrence with the run as recorded is read as concurrence per case (ACCEPTANCE.md (e)); each failed case keeps the disposition its session review gives it (model behavior: accepted model behavior; instrument defect: fix in the next block; case defect: case defect).

[`example.md`](example.md) is an illustrative run, not a logged test run.

History: no run record from the GPT era is published in this repository (see K3).

---

Final Liability rests with the Human.
