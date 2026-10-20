# Evidence: T5 logged run, 18 October 2026 (KST)

**Contract Mechanism Review Assistant · logged run under ruling 9 · run label T5**

What this is: the transcripts and scores of the first logged run of the published instruction block, the run that [`tests.md`](../../tests.md) Last run records.

- **When:** 18 October 2026 (Korea Standard Time, KST), finished 10:25 KST, in Michael Paik's Terminal (session T5 Block A).
- **Instruction text:** the fenced block of [`instructions.md`](../../instructions.md) at v1.2.0 and nothing outside it, 5,697 characters, SHA-256 `c0ced9e1c32f9c382ce320fea2b849c48349bec1b6b0335f183a8ede84df5205` (recorded in `summary.json`; the repository HEAD at the run was `53818e4`, tag v1.2.0).
- **Tested model:** `claude-opus-5-5`, API system prompt, no tools, max_tokens 16,000.
- **Scorer:** `claude-sonnet-5-5`, a different model from the one tested, scoring each transcript against the case's pass condition. LLM scoring is developer testing, not independent assurance.
- **Inputs:** fictional contract excerpts and memos written for the suite (Pellwood Analytics Ltd and Northmere Retail plc are invented); one case per row of the `tests.md` Cases table, C1 to C17.
- **How produced:** the session tool `t5_run.py` (not shipped in this repository) ran each case in a fresh API session, multi-turn where the case needs prior output, and wrote one transcript with its score per case and `summary.json`.

Files: `C1.md` to `C17.md` (one per case: rule, pass condition, every turn, the scorer's verdict and reasoning) and `summary.json` (HEAD, system-file digest, models, max_tokens, per-case verdicts).

Each transcript is copied byte for byte from the run output; only the closing line below is appended. `summary.json` is copied unchanged; its `system_files` key, `../Claude outputs/T5-runs/suites/blocks/cmra-block.txt`, is the maintainer's local path to the extracted block, not a file in this repository, and the digest is that of the fenced block of `instructions.md` at v1.2.0. Model output is verbatim: its em dashes, serial commas and UK spellings are the model's and are not edited. The scorer text is the verdict and reasoning only: where it refers to other scorer fields, as in C8 ("The two flaws noted above") and C11 ("noted in judgment_calls"), those fields are not in the files.

---

Final Liability rests with the Human.
