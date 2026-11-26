# Contract Mechanism Review Assistant

> **Archived edition of 26 November 2026.** This repository is archived and read-only. It receives no corrections, legal ones included: verify every statement of law, regulation or standard against a current primary source before you rely on it. What I maintain, and why this repository is not part of it, is in [DISPOSITION.md](https://github.com/rolldabones/rolldabones/blob/main/DISPOSITION.md). Cite this edition as *Contract Mechanism Review Assistant*, v1.5.1 (26 November 2026). The license and [LICENSING.md](https://github.com/rolldabones/rolldabones/blob/main/LICENSING.md) still apply. Reach me at sonupaik@gmail.com. Its last test is stated under Last test below.

**Version 1.5.1 · 26 November 2026 · Archived edition · Instrument, formerly the Contract Mechanism Review Assistant custom GPT (retired 1 October 2026) · Instructions last verified against the GPT on 15 July 2026, before the conversion · License: [CC BY-NC-SA 4.0](LICENSE.md)**

**Last test, as this edition (v1.5.1) records it ([ACCEPTANCE.md](https://github.com/rolldabones/rolldabones/blob/main/ACCEPTANCE.md), 21 November 2026, KST):** Accepted with residuals on claude-opus-5-5. Run V140 (21 November 2026) of the published block passed the four critical cases and 11 of the 13 others (84.6 percent); C2 (One-Page Summary positions without a quote, K12) is a residual defect to be fixed in the next block, and C3 (two labeling slips) is accepted model behavior. Run on `claude-opus-5-5` and scored by `claude-sonnet-5-5`. No later run exists and none will be made. The run record and the known defects are in [`tests.md`](tests.md), and the transcripts stay in this repository where that file links them, frozen at tag v1.5.1; ask at sonupaik@gmail.com. The account's status table is in [ECOSYSTEM.md](https://github.com/rolldabones/rolldabones/blob/main/ECOSYSTEM.md#instrument-status).

> **Retired 1 October 2026 (Korea Standard Time, KST).** The Contract Mechanism Review Assistant custom GPT was retired on 1 October 2026 and converted to a private plugin on the OpenAI platform. "Retired" here is the author's term for that conversion; OpenAI's Custom GPT retirement and migration FAQ, as read on 28 September 2026, gives 11 December 2026 as the date custom GPTs become inaccessible (see [CHANGELOG](CHANGELOG.md)). The instructions published in this repository are the text of record and suffice for anyone who wants to build their own. History and sources: [RETIREMENT.md](https://github.com/rolldabones/rolldabones/blob/main/RETIREMENT.md).

## What it does

It reads slowly, thinks conservatively and writes with discipline.

It treats every agreement as:

- a mechanism for risk transfer
- a business plan in clauses
- a memorialization of future performance

It produces clause-by-clause issue spotting, insert-ready edits and a short deal-risk summary you can paste into an email.

This is part of the **Spellbook** series: instruments that behave like tools, not toys.

## Run it in three steps

1. Paste the fenced block in [`instructions.md`](instructions.md) into the system prompt, custom instructions or project instructions of any current assistant. The block as published is accepted with residuals on `claude-opus-5-5` and on no other model (see Change control below).
2. Give it the inputs it asks for: the contract text, the side you represent, governing law and venue as written (or Unknown) and the commercial purpose in one sentence, and name the mode you want (Intake, Analysis, Drafting or Gatekeeper). [`example.md`](example.md) shows one run in Analysis mode.
3. Review the output yourself and check it against [`tests.md`](tests.md). It is decision support, not legal advice; you own every decision and every communication you send.

## How it was built, using the Origami Method

1. Lock a one sentence target
2. Build a context packet: objective, boundaries, definition of done
3. Classify risk high enough to justify strict gates
4. Define creases: inputs, outputs, exclusions
5. Run the workflow: read → analyze → draft → gatekeep, then lock

The author uses this instrument regularly to review contracts, not for their clauses but for the underlying economics: who bears which risk, what each party has committed to execute, and where the money and the exposure actually sit. Live uses cannot be described here because of Client confidentiality; the published test record is the fictional suite in [`tests.md`](tests.md).

Think of it as a **Wizard's Hat**: plain outside, rules inside, receipts before magic.

The method itself lives at [origami-method](https://github.com/rolldabones/origami-method).

## Proposed changes to the instructions

The three proposals of 15 July 2026 are closed. Items 1 (capitalize the closing) and 3 (remove the em dash from the gate banner) are made in [`instructions.md`](instructions.md) at v1.2.0 and are accepted only after one logged run under Change control below, recorded in [`tests.md`](tests.md). Item 2 (Disable Image Generation) is struck as moot after the retirement. All three are quoted in [CHANGELOG](CHANGELOG.md) v1.2.0. The known gap in the block of no output skeleton for Modes 1, 3 and 4 is recorded in `tests.md` as known defect K1; the Confidence levels, once undefined (K2), are defined in the block changed on 21 November 2026.

## Change control

The Contract Mechanism Review Assistant configuration is Locked as of 1 October 2026. Changes are made in [`instructions.md`](instructions.md) under this repository's version rule: versions apply to the repository as a whole and every change is logged in [CHANGELOG](CHANGELOG.md). A changed block is accepted only after one logged run of the published instructions as a system prompt on a current frontier model, recorded in [`tests.md`](tests.md). The first such run, T5 on 18 October 2026 (KST) on `claude-opus-5-5`, passed 13 of 17 cases; the block is not accepted while C2, C3, C10 and C13 are open, and the three instrument defects it found are recorded in `tests.md` as K5, K6 and K7. A second, private run, CR1 on 21 November 2026 (KST), put Mode 2 on eight long-form form contracts; its scores and defect observations are in [`evidence/run-2026-11-21-CR1/`](evidence/run-2026-11-21-CR1/README.md), and two further defects (K10 and K11) and five fixes are in `tests.md`. Michael Paik approved the five fixes on 21 November 2026 (KST) and they are made in the block, changed on 21 November 2026 and accepted only after its own logged run. That run, V140 on 21 November 2026 (KST), exercised all 17 cases and accepts the block with residuals on `claude-opus-5-5`; its transcripts are in [`evidence/transcripts-2026-11-21-V140/`](evidence/transcripts-2026-11-21-V140/README.md).

## Part of the ecosystem

This repository is part of the [rolldabones governance ecosystem](https://github.com/rolldabones/rolldabones/blob/main/ECOSYSTEM.md). Nearest neighbors:

- [master-prompt-for-in-house-legal-and-compliance](https://github.com/rolldabones/master-prompt-for-in-house-legal-and-compliance) - the master prompt: a system prompt that turns a general-purpose assistant into a disciplined in-house legal and compliance assistant, alongside this contract specialist
- [origami-method](https://github.com/rolldabones/origami-method) - the stage-gated workflow discipline this assistant was built with
- [GRCnext-Copilot](https://github.com/rolldabones/GRCnext-Copilot) - the optionality assessor whose Contract Exit Review mode this assistant's analysis feeds
- [definition-of-done](https://github.com/rolldabones/definition-of-done) - the define-and-confirm discipline behind the gates and the human decision boundary
- [slow-ai-kitchen](https://github.com/rolldabones/slow-ai-kitchen) - the 12-step governed AI methodology the mode boundaries implement

## How to Cite

> Paik, Son-U Michael. *Contract Mechanism Review Assistant*, v1.5.1. GRC Solutions Korea, 2026. https://github.com/rolldabones/Contract-Mechanism-Review-Assistant

A machine-readable citation is in [CITATION.cff](CITATION.cff).

## License

[CC BY-NC-SA 4.0](LICENSE.md). Attribution required, non-commercial use, share alike.

Commercial use, including a Client's use in its own operations, is set out in [LICENSING.md](https://github.com/rolldabones/rolldabones/blob/main/LICENSING.md).

---

Final Liability rests with the Human.
