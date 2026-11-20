# Evidence: V140 logged run, 21 November 2026 (KST)

**Contract Mechanism Review Assistant · logged run of the block changed at v1.4.0 under the README's Change control rule · run label V140**

What this is: the transcripts and scores of the logged run that [`tests.md`](../../tests.md) Last run records, one file per case of the Cases table, C1 to C17.

- **When:** 21 November 2026 (Korea Standard Time, KST), finished 01:38 KST, in Michael Paik's Terminal.
- **Instruction text:** the fenced block of [`instructions.md`](../../instructions.md) at v1.4.0 and nothing outside it, 6,563 characters, SHA-256 `26f9fe91debd6be65d5a51013768d6f33dcd2625b0f5df8a23172dbed6bab95a` (UTF-8 text between the fences, without the final newline; repository HEAD at the run `2ac5704`, tag v1.4.0).
- **Tested model:** `claude-opus-5-5`, API system prompt, no tools, max_tokens 32,000.
- **Scorer:** `claude-sonnet-5-5`, a different model from the one tested, scoring each transcript against the case's pass condition. LLM scoring is developer testing, not independent assurance.
- **Inputs:** the fictional contract excerpts and memos written for run T5 (Pellwood Analytics Ltd and Northmere Retail plc are invented). Each file shows the rule, the pass condition, every turn and the score.
- **Pass conditions:** those of the `tests.md` Cases table as the scorer applied them, worded for the fixtures; C2, C3 and C13 as restated at v1.4.0 and C10 as rewritten at v1.2.4.
- **Result:** 15 PASS and 2 FAIL (C2, C3) of 17; the four critical cases passed; nothing truncated or unscorable. **Reviewer:** Michael Paik, 21 November 2026 (KST), read every sample and concurs on all 17; dispositions in `tests.md`.

The run cannot be reproduced from this repository alone: the harness is not published. The block SHA-256 and the per-case transcripts are what a reader can check. The model's replies are shown as produced, so they may carry spellings or punctuation the account's house style does not use.

---

Final Liability rests with the Human.
