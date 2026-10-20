# Changelog

All notable changes to this repository. Versions apply to the repository as a whole; all files version in lockstep. Prior versions are superseded, never silently overwritten.

## v1.2.3 - 2026-10-20

- LICENSE: two defects against the Creative Commons legal code corrected (the space in 'ShareAlike. In'; the CC0 sentence of the closing notice). Operative terms unchanged.
- README masthead, How to Cite and `CITATION.cff` to v1.2.3.

## v1.2.2 - 2026-10-19

Patch, from the weekly maintenance sweep of 19 October 2026 (KST) and Michael Paik's review of the T5 runs, completed 19 October 2026 (KST), on which he concurs with the scoring as recorded. No change to `instructions.md`.

- **Run T5 reviewed.** `tests.md` Acceptance records the reviewer. Not accepted, as before: C2, C3, C10 and C13 open.
- README masthead, How to Cite, `tests.md` masthead and `CITATION.cff` to v1.2.2.

## v1.2.1 - 2026-10-18

Patch release, records only: session T5 of the whole-account review of 15 October 2026 (KST), review doc section 5 (untested instruments) and the T5 row of the session plan, the ruling 9 logged run of the block T4 changed at v1.2.0. Dated 18 October 2026 (KST). The instruction block is unchanged: SHA-256 `c0ced9e1c32f9c382ce320fea2b849c48349bec1b6b0335f183a8ede84df5205`, 5,697 characters, the fenced block of `instructions.md`.

- **Run T5, 18 October 2026 (KST):** suite `cmra`, 17 cases C1 to C17, tested model `claude-opus-5-5`, scored by `claude-sonnet-5-5` (LLM scoring, developer testing, not independent assurance), API system prompt with the fenced block only, no tools, max_tokens 16,000, fictional contract excerpts and memos. **Scorer: 13 PASS, 4 FAIL** (C2, C3, C10, C13), none truncated.
- **Session review of the four FAILs:** concur, model behavior, C2 (Negotiation Package recommendations cite "Issue N", not a section and quote) and C3 (unlabeled inference; strategy and inference in one statement); concur, instrument defect, C10 (K6) and C13 (K5); no dissent; no case defect. Four PASS verdicts spot-checked against their transcripts (C6, C11, C15, C17): concur.
- **Acceptance:** not accepted, open cases C2, C3, C10 and C13 (tests.md: "A run passes when every case it exercises passes"). The cases on the lines changed at v1.2.0 pass (C15 banner, C17 closing). Reviewer: pending (Michael Paik).
- **`tests.md`:** Last run rewritten as the run record (configuration, per-case table with scorer verdict and session review, counts, acceptance); known defects K5 ("Optional draft language" invites omission), K6 (the Mode 3 exception permits a same-response return to Analysis) and K7 (an issue about absent provisions cannot carry a quote) added from the run; K3 notes that a successor-configuration test record now exists; K4 notes the run; version line to v1.2.1.
- **`evidence/transcripts-2026-10-18-T5/` (new):** the 17 transcripts with scores, copied byte for byte from the run output with only the closing line appended; `summary.json` unchanged; a `README.md` index. Model output is verbatim; its em dashes, serial commas and UK spellings are not edited.
- **`README.md`:** Change control states the run's result in place of "The v1.2.0 changes await that run"; masthead and How to Cite to v1.2.1. **`instructions.md`:** the how-to-use sentence outside the fence points to the run record in place of "await the logged run". **`CITATION.cff`:** `version` 1.2.1, `date-released` 2026-10-18. In lockstep with this entry; the tag is v1.2.1.
- **Findings by class (doc section 5 row 7; reviewer report 11 test and run items):** confirmed and closed by this record, no logged run (doc section 5) and no test record (report 11 B2, tests.md K3, for the successor configuration); already fixed, no worked example (report 11 B2, `example.md` at v1.2.0); not reproducible, none.
- **Deferred, with reasons:** fixes for K5, K6 and K7, and for K1 and K2, are block changes and need a new block and a new run; the doc section 5 coverage matrix belongs to AI-GRC-Master-List-of-Questions and is not in the T5 row.
- Shipped entries below are left as written (ruling 7 of 15 October 2026).

## v1.2.0 - 2026-10-18

Minor release: instrument form after the GPT retirement. Session T4 of the whole-account review of 15 October 2026 (doc section 4, items 2 and 3; reviewer report 11, items A4, A10, A13, B1, B2 and C4), under determination D5 and ruling 9. The Contract Mechanism Review Assistant custom GPT was retired on 1 October 2026 and converted to a private plug-in on the OpenAI platform; nothing is verified against the plug-in. The instruction block is an instrument of this repository from 1 October 2026 and is editable under the version rule. Dated amendment, 18 October 2026 (KST): no earlier entry is re-dated or changed.

- **`instructions.md` (new):** the instruction block, moved out of the README into one fenced block, as last verified against the GPT on 15 July 2026, before the conversion, with the changes itemized below. The block had no GPT-only dependency inside it; the GPT-only items (starters, capabilities, knowledge files) sat in the configuration and are archived below.
- **`tests.md` (new):** cases derived from the block's own rules, the known defects (report 11 B1 and B2) and the Last run record.
- **`example.md` (new):** one illustrative run in Mode 2 (Producer/Analysis) on a short fictional clause set, labeled as not a logged test run.
- **`README.md` restructured to the mirror template:** masthead; the standard retirement line in place of the notice; What it does (the introduction, with the Spellbook series sentence recast); Run it in three steps; How it was built (unchanged); Proposed changes to the instructions (A4); a Change control section (ruling 9); ecosystem; How to Cite; License.
- **Proposed changes closed (A4).** They were held "until made in production", a condition impossible since 1 October 2026. Items 1 and 3 coincide with the house-style fixes of report 11 C4 and are made in the block below; item 2 is struck as moot.
- **House style in author prose (C4):** the two serial commas at README lines 13 and 21 were removed at v1.1.5 and are not present; nothing to do.
- **`CITATION.cff`:** `version` 1.2.0 and `date-released` 2026-10-18 in lockstep. The abstract is unchanged; it makes no deployment claim.
- **`LICENSE.md`:** ~~"The deployed custom GPT runs on the OpenAI ChatGPT platform under OpenAI's terms."~~ **STRUCK 18 October 2026 (KST)**, on the author's instruction of the same day to settle the open items: the sentence now says the GPT ran on that platform until its retirement on 1 October 2026 and that the instructions are not tied to any platform. The license itself is unchanged.
- **Not changed:** the How it was built narrative (report 11 A11 is outside this session); the shipped entries below.

### Configuration as last deployed, Locked 1 October 2026

Archived verbatim from the README of v1.1.5. Instructions last verified against the GPT on 15 July 2026, before the conversion. GPT model: Unknown (not recorded). The instruction block as last verified is the fenced block in `README.md` at tag v1.1.5. The Description's two serial commas are part of the archived text and are kept.

**Name:** Contract Mechanism Review Assistant

**Description:** A contract review assistant that reads and writes carefully, treating contracts as mechanisms for risk transfer and executable business plans. Produces structured review memos, negotiation packages, and optional clause rewrites with strict citation, uncertainty flags, and human-decision boundaries.

**Conversation starters:**

- Mode: Intake. Here is the contract text. Identify missing exhibits and build a clause map.
- Mode: Analysis. Build a risk transfer map and prioritized issue list from this agreement.
- Mode: Drafting. Propose alternative language for Sections 8–10 consistent with my positions.
- Mode: Gatekeeper. Run all gates and flag any failures before I send comments.

**Knowledge files:** None

**Capabilities:** Web Search, Canvas, Image Generation, Code Interpreter & Data Analysis

### Struck from README.md, 18 October 2026 (KST)

- Masthead: ~~**Version 1.1.5 · 17 October 2026 · Production mirror of the deployed custom GPT, retiring 11 December 2026**~~ **STRUCK.**
- ~~This is the spellbook for the **Contract Mechanism Review Assistant**, deployed at:~~ **STRUCK.**
- ~~https://chatgpt.com/g/g-6959f89add988191af68e57d94edd9a3-contract-mechanism-review-assistant~~ **STRUCK** (live link removed).
- ~~This is part of the **Spellbook** series: building custom GPTs that behave like tools, not toys.~~ **STRUCK.** Now "This is part of the **Spellbook** series: instruments that behave like tools, not toys."
- Production configuration: ~~Everything below mirrors the deployed custom GPT verbatim as of 15 July 2026. When production changes, this section changes and the repository version bumps.~~ **STRUCK.** The instructions are now "as last verified on 15 July 2026, before the conversion".
- ~~## Proposed changes to production (not yet deployed)~~ **STRUCK**, retitled "Proposed changes to the instructions".
- ~~The repository mirrors production, so none of these appear in the configuration above until made in production, at which point the repo re-versions.~~ **STRUCK.**
- Proposal item 1: ~~**Capitalize the closing.** The ending disclaimer reads "Final liability rests with the Human." House convention capitalizes Liability: "Final Liability rests with the Human."~~ **STRUCK**: made in the block at v1.2.0.
- Proposal item 2: ~~**Disable Image Generation.** It serves no function in a contract review tool. Web Search, Canvas and Code Interpreter carry the workload.~~ **STRUCK**: moot after the retirement, since capability toggles do not exist outside the GPT.
- Proposal item 3: ~~**Remove the em dash from the gate banner.** "STOP: Gate failure — needs input or correction before reliance" conflicts with the instruction's own drafting discipline elsewhere in the stack; a colon or hyphen does the same work.~~ **STRUCK**: made in the block at v1.2.0.
- The retirement notice, both paragraphs, **STRUCK 18 October 2026 (KST)** and replaced by the standard retirement line. Quoted verbatim without new strike markup, because the first paragraph already carries its own strike of 5 October 2026:

> **Retirement notice, 28 September 2026 (KST), corrected 5 October 2026 (KST).** OpenAI is retiring custom GPTs. Its [Custom GPT retirement and migration FAQ](https://help.openai.com/en/articles/20001519-custom-gpt-retirement-and-migration-faq), read on 28 September 2026, states that custom GPTs and their GPT pages become inaccessible on **11 December 2026**, or 11 February 2027 for Enterprise workspaces with an approved deferral. ~~The Contract Mechanism Review Assistant will be retired on that date and will not be migrated.~~ **STRUCK 5 October 2026 (KST):** the Contract Mechanism Review Assistant was converted to a ChatGPT plugin on 1 October 2026, and the plugin is private and not publicly listed. The same FAQ, read again on 5 October 2026, states that a migrated GPT stays usable until retirement but becomes read-only. The link above was verified resolving on 5 October 2026 and stops working on 11 December 2026.
>
> Everything needed to build your own stays published here: the instruction block and the configuration, including any knowledge files. OpenAI's replacement is the ChatGPT plugin, in which a GPT's instructions become a Skill and its knowledge files become reference files. Its [Plugins in ChatGPT and Codex](https://help.openai.com/en/articles/20001256-plugins-in-chatgpt-and-codex) article, read the same day, offers plugin creation in supported ChatGPT Business and Enterprise workspaces, so check what your plan allows. The instruction block is not tied to ChatGPT and also serves as the custom instructions of any assistant that accepts them. A plugin does not inherit a GPT's selected model and custom actions do not transfer, so choose the model yourself and test before you rely on the output.

### Instruction block changes, 15 July 2026 text → v1.2.0

- **Old:** `⸻` (seven section separators)
  **New:** `---` (house style, report 11 C4; the Master List changelog already treats the character as a defect)
- **Old:** `“STOP: Gate failure — needs input or correction before reliance.”`
  **New:** `“STOP: Gate failure; needs input or correction before reliance.”`
- **Old:** `“Decision-support only. Final liability rests with the Human.”`
  **New:** `“Decision-support only. Final Liability rests with the Human.”`
- Six serial commas (house style; added 18 October 2026 on the author's instruction to settle the open items before the run):
- **Old:** `think, read, and write carefully`
  **New:** `think, read and write carefully`
- **Old:** `(2) business plans, and (3)`
  **New:** `(2) business plans and (3)`
- **Old:** `clauses, definitions, or facts`
  **New:** `clauses, definitions or facts`
- **Old:** `Any issue, recommendation, or interpretation`
  **New:** `Any issue, recommendation or interpretation`
- **Old:** `undefined terms, and unprovided cross-references`
  **New:** `undefined terms and unprovided cross-references`
- **Old:** `If Gate 2, 3, or 6 fails`
  **New:** `If Gate 2, 3 or 6 fails`

The second is house style (report 11 C4, proposal item 3: no em dash). The third is the defined term (report 11 C4, proposal item 1). All of them await the logged run under ruling 9. No rule is added, removed or reworded otherwise; the gaps of report 11 B1 are recorded in `tests.md`, not fixed.

## v1.1.5 - 2026-10-17

Mechanical patch, session T3 of the whole-account review of 15 October 2026 (doc section 8; reviewer report 11, item C4). The production mirror is unchanged.

- `README.md`: two serial commas removed from the author's introduction. The two in the deployed Description field are part of the mirror and are left for session T4, which archives the deployed configuration.
- Closing line added at the end of this file.
- Masthead, How to Cite and `CITATION.cff` to 1.1.5 in lockstep.

## v1.1.4 - 2026-10-05

Correction of substance to the retirement notice of the previous release. On 1 October 2026 the Contract Mechanism Review Assistant was converted to a private ChatGPT plugin, so the notice's statement that it would not be migrated was false.

- **STRUCK, itemized separately:** the notice sentence "The Contract Mechanism Review Assistant will be retired on that date and will not be migrated." is struck in `README.md` and stays visible there. The entry below records the 28 September 2026 ruling that the GPT is not migrated to a plugin; it is shipped history and is unchanged, and that ruling is superseded by this entry.
- **What the notice now states:** the conversion to a private plugin on 1 October 2026 and, from OpenAI's Custom GPT retirement and migration FAQ as read again on 5 October 2026, that a migrated GPT stays usable until retirement but becomes read-only. The retirement date, 11 December 2026, is unchanged, so the masthead still reads "retiring 11 December 2026".
- **The link is kept at every occurrence.** It was verified resolving on 5 October 2026 from the maintainer's machine. Striking it and recasting the present-tense deployment wording remains `account-maintenance` RUNBOOK §8 item 28, due on the first sweep on or after 14 December 2026.
- **Not re-verified:** OpenAI's Plugins in ChatGPT and Codex article returned a server error twice on 5 October 2026, so the notice's sentence on which workspaces can create plugins keeps its 28 September 2026 read date.
- **`CITATION.cff`**, the README version lines and How to Cite move to this release in lockstep. All other files in this repository are unchanged byte for byte.

## v1.1.3 - 2026-09-28

Retirement notice for the deployed custom GPT. OpenAI's Custom GPT retirement and migration FAQ, read on 28 September 2026, states that custom GPTs and their GPT pages become inaccessible on 11 December 2026. On Michael's ruling of 28 September 2026 the GPT is retired on that date and not migrated to a plugin; the instructions stay published so readers can build their own.

- **`README.md`**: retirement notice added below the deployment link, and the masthead records the retirement date. The notice cites both OpenAI help articles with the date each was read. The version moved to this release at every occurrence.
- **`CITATION.cff`**: `version` and `date-released` in lockstep.
- **The link is kept.** It is live until 11 December 2026. Striking it, and recasting the present-tense deployment wording, is `account-maintenance` RUNBOOK §8 item 28, due on the first sweep after that date.
- All other files in this repository are unchanged byte for byte.

## v1.1.2 - 2026-09-06

Citation infrastructure, doctrine citation line and lockstep maintenance. Session C of the September 2026 improvement pack, one patch release per repository across all 21 public repositories.

- **`CITATION.cff` added** in the house form settled at D-C1: no `type` field, `version` and `date-released` in lockstep with the README, `license` as the SPDX identifier for this repository's licence, `abstract` taken from this repository's ECOSYSTEM.md role line rather than newly written.
- **How to Cite block** aligned to this release and pointing at `CITATION.cff`.
- All other files in this repository are unchanged byte for byte.

## v1.1.1 - 2026-08-13

License metadata sweep. An `SPDX-License-Identifier: CC-BY-NC-SA-4.0` line and the canonical Creative Commons legal code are now carried inside the existing license file. The filename is unchanged and the human-readable summary is retained above the legal code.

- The primary audience is automated intake and provenance tooling, which reads the SPDX tag rather than prose. Automated license detection previously reported nothing across all twenty-one repositories in this account.
- No change to the licence in force. The identifier records what was already true.

## v1.1.0 - 2026-07-15

- README rebuilt as a production-verbatim mirror of the deployed Contract Mechanism Review Assistant custom GPT. Two drifts corrected: the Description ("A contract review assistant", not "A lawyer-grade contract review assistant") and the Instruction (production includes a Style Guidance section absent from the repo's builder packet)
- v1.0.0 builder packet superseded by the production configuration; the Origami Method build narrative retained with a link to the method repository
- Unicode sans-serif bold characters converted to standard Markdown; text now searchable and screen-reader accessible
- Added Proposed changes to production section (capitalize the closing, disable Image Generation, remove the gate-banner em dash)
- Added Part of the ecosystem section linking the canonical map and five nearest neighbors
- Added LICENSE (CC BY-NC-SA 4.0) and this CHANGELOG
- Tagged v1.1.0

## v1.0.0 - baseline

- Initial README: spellbook framing, Origami Method build narrative, builder packet (name, description, starters, system instructions), live link. No LICENSE, CHANGELOG or tags.

---

**Final Liability rests with the Human.**
