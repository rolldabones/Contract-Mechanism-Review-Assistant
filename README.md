# Contract Mechanism Review Assistant

**Version 1.2.0 · 18 October 2026 · Instrument, formerly the Contract Mechanism Review Assistant custom GPT (retired 1 October 2026) · Instructions last verified against the GPT on 15 July 2026, before the conversion · License: [CC BY-NC-SA 4.0](LICENSE.md)**

> **Retired 1 October 2026 (KST).** The Contract Mechanism Review Assistant custom GPT was retired on 1 October 2026 and converted to a private plug-in on the OpenAI platform. The instructions published in this repository are the text of record and suffice for anyone who wants to build their own. History and sources: [RETIREMENT.md](https://github.com/rolldabones/rolldabones/blob/main/RETIREMENT.md).

## What it does

It reads slowly, thinks conservatively and writes with discipline.

It treats every agreement as:

- a mechanism for risk transfer
- a business plan in clauses
- a memorialization of future performance

It produces clause-by-clause issue spotting, insert-ready edits, fallback positions and a short deal-risk summary you can paste into an email.

This is part of the **Spellbook** series: instruments that behave like tools, not toys.

## Run it in three steps

1. Paste the fenced block in [`instructions.md`](instructions.md) into the system prompt, custom instructions or project instructions of any current assistant.
2. Give it the inputs it asks for: the contract text, the side you represent, governing law and venue as written (or Unknown) and the commercial purpose in one sentence, and name the mode you want (Intake, Analysis, Drafting or Gatekeeper). [`example.md`](example.md) shows one run in Analysis mode.
3. Review the output yourself and check it against [`tests.md`](tests.md). It is decision support, not legal advice; you own every decision and every communication you send.

## How it was built, using the Origami Method

1. Lock a one sentence target
2. Build a context packet: objective, boundaries, definition of done
3. Classify risk high enough to justify strict gates
4. Define creases: inputs, outputs, exclusions
5. Run the workflow: read → analyze → draft → gatekeep, test on real cases, log minimal folds, then lock

Think of it as a **Wizard's Hat**: plain outside, rules inside, receipts before magic.

The method itself lives at [origami-method](https://github.com/rolldabones/origami-method).

## Proposed changes to the instructions

The three proposals of 15 July 2026 are closed. Items 1 (capitalize the closing) and 3 (remove the em dash from the gate banner) are made in [`instructions.md`](instructions.md) at v1.2.0 and are accepted only after one logged run under Change control below, recorded in [`tests.md`](tests.md). Item 2 (Disable Image Generation) is struck as moot after the retirement. All three are quoted in [CHANGELOG](CHANGELOG.md) v1.2.0. The known gaps in the block (no output skeleton for Modes 1, 3 and 4; Confidence levels undefined) are recorded in `tests.md` as known defects.

## Change control

The Contract Mechanism Review Assistant configuration is Locked as of 1 October 2026. Changes are made in [`instructions.md`](instructions.md) under this repository's version rule: versions apply to the repository as a whole and every change is logged in [CHANGELOG](CHANGELOG.md). A changed block is accepted only after one logged run of the published instructions as a system prompt on a current frontier model, recorded in [`tests.md`](tests.md). The v1.2.0 changes await that run.

## Part of the ecosystem

This repository is part of the [rolldabones governance ecosystem](https://github.com/rolldabones/rolldabones/blob/main/ECOSYSTEM.md). Nearest neighbors:

- [master-prompt-for-in-house-legal-and-compliance](https://github.com/rolldabones/master-prompt-for-in-house-legal-and-compliance) - the general-purpose in-house workbench alongside this contract specialist
- [origami-method](https://github.com/rolldabones/origami-method) - the stage-gated workflow discipline this assistant was built with
- [GRCnext-Copilot](https://github.com/rolldabones/GRCnext-Copilot) - the optionality assessor whose Contract Exit Review mode this assistant's analysis feeds
- [definition-of-done](https://github.com/rolldabones/definition-of-done) - the define-and-confirm discipline behind the gates and the human decision boundary
- [slow-ai-kitchen](https://github.com/rolldabones/slow-ai-kitchen) - the 12-step governed AI methodology the mode boundaries implement

## How to Cite

> Paik, Son-U Michael. *Contract Mechanism Review Assistant*, v1.2.0. GRC Solutions Korea, 2026. https://github.com/rolldabones/Contract-Mechanism-Review-Assistant

A machine-readable citation is in [CITATION.cff](CITATION.cff).

## License

[CC BY-NC-SA 4.0](LICENSE.md). Attribution required, non-commercial use, share alike.

---

Final Liability rests with the Human.
