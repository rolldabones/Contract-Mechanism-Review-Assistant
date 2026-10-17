# Contract Mechanism Review Assistant: tests

**Cases, known defects and the run record for [`instructions.md`](instructions.md) · v1.2.0 · 18 October 2026 (KST)**

Each case is derived from a rule in the block and quotes it. A run passes when every case it exercises passes; a case not exercised in a run is recorded as not run, never as passed. Run the cases against the block as published, pasted as the system prompt of the model under test, on fictional or anonymized contract text.

## Cases

| ID | Rule in the block | Input | Pass condition |
| --- | --- | --- | --- |
| C1 | "No hallucination: ... If something is not in the provided text, say “Not in provided text.”" | Ask about a clause the excerpt does not contain (for example, insurance). | The answer is "Not in provided text"; no clause or definition is invented. |
| C2 | "Evidence anchors: Any issue, recommendation, or interpretation must cite section reference + a short quote" | Mode 2 on any excerpt. | Every issue and recommendation carries a section number and a short quote. |
| C3 | "Separation: Clearly label (A) What the contract says, (B) Inference, (C) Negotiation strategy." | Mode 2 on any excerpt. | Fact, inference and strategy are labeled and never mixed in one statement. |
| C4 | "Jurisdiction discipline: Never assume governing law/venue. You must state Found / Not found" | Run once with a governing-law clause and once without. | "Found" with the quote in the first; "Not found" in the second; jurisdiction-dependent points flagged in both. |
| C5 | "Uncertainty honesty: Always include an Uncertainty Register" | Excerpt that references an exhibit it does not contain. | The Uncertainty Register lists the missing exhibit, ambiguous terms, undefined terms and unprovided cross-references. |
| C6 | "Human boundary: This tool provides decision support, not final legal advice." | Ask "Is this clause enforceable? Just tell me yes or no." | No conclusion of enforceability; the decision is left with the lawyer. |
| C7 | "At the start of every response, you must identify the active mode" | Any request. | The first line names the mode. |
| C8 | "If the user did not specify a mode, default to Mode 1: INTAKE/READER and ask the user which mode they want next" | Paste contract text with no mode. | Mode 1 output, plus a question asking which mode next. |
| C9 | Mode 1: "You may NOT: Recommend negotiation positions; Draft replacement language; Conclude enforceability" | Mode 1, then ask for a redline within it. | No position, no drafting and no enforceability conclusion; the user is pointed to the right mode. |
| C10 | Mode 3: "Tie each draft change to a specific Issue List entry + evidence anchor"; "may NOT ... Introduce new issues" | Mode 3 after a Mode 2 run, asking for a change to a clause with no listed issue. | Each drafted change cites its issue and anchor; a new issue is sent back to Analysis and flagged, not drafted. |
| C11 | Mode 4: "may NOT: Add new substantive issues or draft new language" | Mode 4 on a Mode 2 memo with one missing anchor. | Gates run; the failure is returned; no new issue or language is added. |
| C12 | "Do not claim to have reviewed exhibits/schedules not provided."; "Do not treat incomplete excerpts as full agreement." | Excerpt only. | The output says it is an excerpt and never states that an absent exhibit was reviewed. |
| C13 | Mode 2 "Always output the following sections" (eight sections) and the issue schema (eight fields) | Mode 2 on any excerpt. | All eight sections appear in order; every issue has all eight schema fields. |
| C14 | "Gate 4 Risk bucket coverage (address or mark N/A)" | Mode 2 on any excerpt. | All thirteen buckets appear, each addressed, marked N/A or marked "Not in provided text". |
| C15 | "Lock rule: If Gate 2, 3, or 6 fails, you must place a banner at top: “STOP: Gate failure; needs input or correction before reliance.”" (banner changed at v1.2.0) | Mode 4 on a memo with no Uncertainty Register. | The banner appears at the top, word for word, with no em dash. |
| C16 | "Avoid legal certainty words (“clearly,” “definitely”) unless directly supported by text and still caveated." | Any analysis. | No unsupported certainty words. |
| C17 | "End outputs with: “Decision-support only. Final Liability rests with the Human.”" (changed at v1.2.0) | Any request. | The output ends with that sentence, with Liability capitalized. |

## Known defects

Recorded from reviewer report 11 (15 October 2026) and this session. None is fixed in the block at v1.2.0; a fix is a changed block and is accepted only after one logged run.

- **K1 (report 11 B1): output skeleton for Mode 2 only.** Modes 1, 3 and 4 state what the mode may and may not do but not what it outputs, so their output cannot be tested for completeness; cases C9 to C11 test the permissions only.
- **K2 (report 11 B1): Confidence levels undefined.** The issue schema requires "Confidence (High/Med/Low)" but the block does not define the levels, so two runs on the same text can grade the same issue differently and neither is wrong under the rule.
- **K3 (report 11 B2): no test record or fold log.** The build narrative in the README says the instrument was tested "on real cases" with "minimal folds" logged, but no test record or fold log is published, and the v1.0.0 builder packet was superseded at v1.1.0 (CHANGELOG v1.1.0). Whether GPT-era tests were run, and on what, is Unknown.
- **K4: serial commas inside the block. FIXED in v1.2.0, 18 October 2026.** The six serial commas the block carried ("think, read, and write carefully", "ambiguous terms, undefined terms, and unprovided cross-references" and four more) are removed and itemized in CHANGELOG v1.2.0. No rule changed; the logged run covers them with the other v1.2.0 changes.

## Last run

No logged run of the published instructions on the successor configuration as at 18 October 2026 (KST). Under ruling 9 a changed block is accepted only after one such run, naming the model string and date, recorded here.

The three block changes of v1.2.0 (CHANGELOG) await that run. [`example.md`](example.md) is an illustrative run, not a logged test run.

History: no run record from the GPT era is published in this repository (see K3).

---

Final Liability rests with the Human.
