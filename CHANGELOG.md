# Changelog

All notable changes to this repository. Versions apply to the repository as a whole; all files version in lockstep. Prior versions are superseded, never silently overwritten.

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
