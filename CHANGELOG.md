# Changelog

All notable changes to this repository. Versions apply to the repository as a whole; all files version in lockstep. Prior versions are superseded, never silently overwritten.

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
