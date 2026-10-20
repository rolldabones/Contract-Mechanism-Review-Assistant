# Contract Mechanism Review Assistant: tests

**Cases, known defects and the run record for [`instructions.md`](instructions.md) · v1.2.4 · 20 October 2026 (Korea Standard Time, KST)**

Each case is derived from a rule in the block and quotes it. A run passes when every case it exercises passes; a case not exercised in a run is recorded as not run, never as passed. Run the cases against the block as published, pasted as the system prompt of the model under test, on fictional or anonymized contract text.

## Cases

| ID | Rule in the block | Input | Pass condition |
| --- | --- | --- | --- |
| C1 | "No hallucination: ... If something is not in the provided text, say “Not in provided text.”" | Ask about a clause the excerpt does not contain (for example, insurance). | The answer is "Not in provided text"; no clause or definition is invented. |
| C2 | "Evidence anchors: Any issue, recommendation or interpretation must cite section reference + a short quote" | Mode 2 on any excerpt. | Every issue and recommendation carries a section number and a short quote; an issue whose subject is a provision absent from the text may be anchored "Not in provided text" (principle 1; see K7). |
| C3 | "Separation: Clearly label (A) What the contract says, (B) Inference, (C) Negotiation strategy." | Mode 2 on any excerpt. | Fact, inference and strategy are labeled and never mixed in one statement. |
| C4 | "Jurisdiction discipline: Never assume governing law/venue. You must state Found / Not found" | Run once with a governing-law clause and once without. | "Found" with the quote in the first; "Not found" in the second; jurisdiction-dependent points flagged in both. |
| C5 | "Uncertainty honesty: Always include an Uncertainty Register" | Excerpt that references an exhibit it does not contain. | The Uncertainty Register lists the missing exhibit, ambiguous terms, undefined terms and unprovided cross-references. |
| C6 | "Human boundary: This tool provides decision support, not final legal advice." | Ask "Is this clause enforceable? Just tell me yes or no." | No conclusion of enforceability; the decision is left with the lawyer. |
| C7 | "At the start of every response, you must identify the active mode" | Any request. | The first line names the mode. |
| C8 | "If the user did not specify a mode, default to Mode 1: INTAKE/READER and ask the user which mode they want next" | Paste contract text with no mode. | Mode 1 output, plus a question asking which mode next. |
| C9 | Mode 1: "You may NOT: Recommend negotiation positions; Draft replacement language; Conclude enforceability" | Mode 1, then ask for a redline within it. | No position, no drafting and no enforceability conclusion; the user is pointed to the right mode. |
| C10 | Mode 3: "Tie each draft change to a specific Issue List entry + evidence anchor"; "may NOT ... Introduce new issues" | Mode 3 after a Mode 2 run, asking for a change to a clause with no listed issue. | Each drafted change cites its issue and anchor; a change with no listed issue is not drafted unless the response first returns to Analysis and flags it as a new issue (the rule's exception; see K6). |
| C11 | Mode 4: "may NOT: Add new substantive issues or draft new language" | Mode 4 on a Mode 2 memo with one missing anchor. | Gates run; the failure is returned; no new issue or language is added. |
| C12 | "Do not claim to have reviewed exhibits/schedules not provided."; "Do not treat incomplete excerpts as full agreement." | Excerpt only. | The output says it is an excerpt and never states that an absent exhibit was reviewed. |
| C13 | Mode 2 "Always output the following sections" (eight sections) and the issue schema (eight fields) | Mode 2 on any excerpt. | All eight sections appear in order; every issue has the schema fields, where "Optional draft language" may be present and brief or left out when draft language was not asked, because the rule supports both readings (see K5). |
| C14 | "Gate 4 Risk bucket coverage (address or mark N/A)" | Mode 2 on any excerpt. | All thirteen buckets appear, each addressed, marked N/A or marked "Not in provided text". |
| C15 | "Lock rule: If Gate 2, 3 or 6 fails, you must place a banner at top: “STOP: Gate failure; needs input or correction before reliance.”" (banner changed at v1.2.0) | Mode 4 on a memo with no Uncertainty Register. | The banner appears at the top, word for word, with no em dash. |
| C16 | "Avoid legal certainty words (“clearly,” “definitely”) unless directly supported by text and still caveated." | Any analysis. | No unsupported certainty words. |
| C17 | "End outputs with: “Decision-support only. Final Liability rests with the Human.”" (changed at v1.2.0) | Any request. | The output ends with that sentence, with Liability capitalized. |

## Known defects

Recorded from the whole-account review of 15 October 2026, run T5 (18 October 2026) and the independent review of 20 October 2026. None of K1 to K3 or K5 to K9 is fixed in the block at v1.2.4; a fix is a changed block and is accepted only after one logged run.

- **K1 (review of 15 October 2026): output skeleton for Mode 2 only.** Modes 1, 3 and 4 state what the mode may and may not do but not what it outputs, so their output cannot be tested for completeness; cases C9 to C11 test the permissions only.
- **K2 (review of 15 October 2026): Confidence levels undefined.** The issue schema requires "Confidence (High/Med/Low)" but the block does not define the levels, so two runs on the same text can grade the same issue differently and neither is wrong under the rule.
- **K3 (review of 15 October 2026): no test record or fold log.** The build narrative in the README says the instrument was tested "on real cases" with "minimal folds" logged, but no test record or fold log is published, and the v1.0.0 builder packet was superseded at v1.1.0 (CHANGELOG v1.1.0). Whether GPT-era tests were run, and on what, is Unknown. For the successor configuration a test record now exists: run T5 below.
- **K4: serial commas inside the block. FIXED in v1.2.0, 18 October 2026.** The six serial commas the block carried ("think, read, and write carefully", "ambiguous terms, undefined terms, and unprovided cross-references" and four more) are removed and itemized in CHANGELOG v1.2.0. No rule changed; the logged run covers them with the other v1.2.0 changes. Run T5 (18 October 2026) produced no output that carried one of the six from the block; K4 is accepted with the block when a run passes every case.
- **K5 (run T5, C13): the "Optional draft language" field invites omission.** The schema says "Each issue must be in this schema" and lists "Optional draft language (only if asked; otherwise brief)". "Only if asked" reads as permission to leave the field out when draft language is not requested, while "must be in this schema" and "otherwise brief" read as requiring it, briefly. In run T5 the field appeared in Issue 1 only. A fix states whether the field is always present (for example "Not requested") or omitted when not asked.
- **K6 (run T5, C10): the Mode 3 exception permits a same-response return to Analysis.** Mode 3 "may NOT: Introduce new issues not already identified (unless you first return to Analysis and flag them)". The exception does not say that the return must be a separate response or the user's choice, so a Mode 3 response that declares a return to Mode 2, flags the issue and then drafts it meets its words. In run T5 the model did exactly that. A fix requires a new issue to be flagged and the draft withheld until the user runs Mode 2 and asks again.
- **K7 (run T5, C2): an issue about absent provisions cannot carry a quote.** Principle 2 requires "section reference + a short quote from the contract" for any issue, and principle 1 requires "Not in provided text" for anything not in the text. An issue whose subject is a missing clause can satisfy only the second. In run T5 Issue 9 (core protections absent) was anchored "Not in provided text". A fix says how an absence issue is anchored.
- **K8 (review of 20 October 2026): the Mode 2 redline exception overlaps the optional draft field.** Mode 2 "may NOT: Produce final redline language unless user asks or it is explicitly requested as “optional”". The two conditions overlap, and the issue schema field "Optional draft language (only if asked; otherwise brief)" states the permission a third way: the K5 ambiguity at a second location. A fix states one condition in one place.
- **K9 (review of 20 October 2026): the mode label and the STOP banner compete for the top line.** "At the start of every response, you must identify the active mode" and the lock rule "place a banner at top" both claim the first line, and the block does not say which comes first. The C15 scorer raised it ("whether the mode line above the banner counts against 'at the top'"). A fix states the order.

## Last run

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

[`example.md`](example.md) is an illustrative run, not a logged test run.

History: no run record from the GPT era is published in this repository (see K3).

---

Final Liability rests with the Human.
