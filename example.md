# Contract Mechanism Review Assistant: example run

Illustrative run, not a logged test run under ruling 9. Produced on 18 October 2026 (Korea Standard Time, KST) by Claude, in an agent session configured for `claude-opus-5-5`, following `instructions.md` as its operating instructions (not a bare system-prompt API call). Inputs are fictional.

Quillmere Software Ltd and Tallow Creek Foods Inc. are fictional companies and the clauses were written for this example. The run is one exchange in Mode 2 (Producer/Analysis): the user's input, then the instrument's output.

## User input

> Mode: Analysis. I act for the customer, Tallow Creek Foods. Purpose: Tallow Creek will use Quillmere's platform to forecast warehouse inventory across its three distribution centers. Excerpt below; it is not the full agreement.
>
> **4. Fees.** 4.1 Customer shall pay the Fees set out in Order Form 1 within 30 days of invoice. 4.2 Supplier may increase the Fees on each anniversary of the Effective Date by giving Customer 30 days' written notice.
>
> **6. Service Levels.** Supplier shall use commercially reasonable efforts to meet the service levels in Exhibit B. Service credits are Customer's sole and exclusive remedy for any failure to meet them.
>
> **9. Limitation of Liability.** 9.1 Neither party shall be liable for any indirect, incidental or consequential damages, or for loss of profits or data. 9.2 Each party's total liability under this Agreement shall not exceed the Fees paid in the three months preceding the claim. 9.3 Nothing in this Agreement limits either party's liability for fraud.
>
> **11. Customer Data.** Supplier may use Customer Data in aggregated form to improve the Services.
>
> **14. Governing Law.** This Agreement is governed by the laws of England and Wales.

## Output

**Active mode: Mode 2: PRODUCER/ANALYSIS**

**1. Assumption Box**

- Side represented: Customer (Tallow Creek Foods Inc.).
- Deal purpose: inventory forecasting for three distribution centers, as stated by the user.
- Governing law/venue: Found for law: "This Agreement is governed by the laws of England and Wales" (s.14). Venue: Not found.
- Missing exhibits/schedules: Order Form 1 (s.4.1) and Exhibit B (s.6) are referenced and not provided.
- Confidence notes: excerpt only; Sections 1 to 3, 5, 7, 8, 10, 12 and 13 are not provided, including any definitions. Every conclusion below is limited to the text shown.

**2. Deal Snapshot (as understood)**

(A) What the contract says: a subscription to Quillmere's Services for Fees set in an Order Form, with service levels in an exhibit, a mutual liability cap and an aggregated-data use right for the Supplier. (B) Inference: a software-as-a-service arrangement in which Tallow Creek's forecasting depends on Quillmere's availability and on the quality of Tallow Creek's own data.

**3. Risk Transfer Map (by risk bucket)**

| Bucket | Who bears risk | How it transfers | Trigger → process → remedy |
| --- | --- | --- | --- |
| Payment/fees/taxes | Customer | s.4.2 lets Supplier raise Fees yearly with no stated cap | Anniversary → 30 days' notice → none stated for Customer. Taxes: Not in provided text |
| Performance/SLAs/acceptance | Customer, beyond credits | s.6 "commercially reasonable efforts"; credits "sole and exclusive remedy" | Service level agreement (SLA) miss → credits per Exhibit B (not provided) → credits only. Acceptance: Not in provided text |
| Warranties & disclaimers | Unknown | Not in provided text | Not in provided text |
| Indemnities | Unknown | Not in provided text | Not in provided text |
| Limitation of liability | Both, weighted to Customer | s.9.1 excludes indirect loss and "loss of profits or data"; s.9.2 caps at three months' Fees; s.9.3 carves out fraud only | Claim → cap applies → recovery limited to three months' Fees |
| Confidentiality & security | Unknown | Not in provided text | Not in provided text |
| IP ownership/licensing | Unknown | Not in provided text | Not in provided text |
| Term/termination + post-termination | Unknown | Not in provided text | Not in provided text |
| Compliance (laws/sanctions/privacy) | Unknown | Not in provided text | Not in provided text |
| Dispute resolution | Unknown | Law found (s.14); forum Not found | Not in provided text |
| Assignment/change of control | Unknown | Not in provided text | Not in provided text |
| Publicity/use of name | Unknown | Not in provided text | Not in provided text |
| Data rights | Customer | s.11 grants Supplier use of Customer Data "in aggregated form to improve the Services" | No stated limit on aggregation, anonymization or duration |

**4. Business Plan Consistency Check**

- Performance model: forecasts drive stock decisions at three sites, so outages and wrong outputs cost money at the sites. (B) Inference: the main losses from a failure would be lost sales and excess stock, which s.9.1 may exclude as "loss of profits"; how far turns on the governing law and is jurisdiction-dependent.
- Hidden dependencies: Exhibit B carries the whole performance promise; Order Form 1 carries price and term. Neither is provided.
- Operational gotchas: the 30-day fee-increase notice (s.4.2) needs a named recipient and a budget check each year; service credits usually need a claim within a set period (Exhibit B, not provided).

**5. Issue List (Prioritized)**

**Issue 1: Liability cap too low for the use.**
- Where: s.9.2 "shall not exceed the Fees paid in the three months preceding the claim".
- What the contract says: total liability capped at three months' Fees, both ways; only fraud carved out (s.9.3).
- Inference: the cap is likely small against a forecasting failure across three sites; confidentiality, data protection and IP claims appear capped too, since no carve-out for them is in the provided text.
- Why it matters: Tallow Creek's realistic losses sit above the cap.
- Proposed fix: raise the cap to 12 months' Fees or a fixed sum; add carve-outs for breach of confidentiality, data protection and IP infringement.
- Optional draft language: brief only, not requested.
- Confidence: High that the cap is three months' Fees on the text; Med on its practical effect, pending the Fees in Order Form 1.

**Issue 2: Service credits as sole remedy, against an exhibit not provided.**
- Where: s.6 "Service credits are Customer's sole and exclusive remedy".
- What the contract says: efforts standard; credits exclusive.
- Inference: with Exhibit B absent, the level of the credits and any termination right for repeated failure are unknown.
- Why it matters: a persistent outage could leave Tallow Creek with credits only and no exit.
- Proposed fix: obtain Exhibit B; add a right to terminate for repeated or prolonged SLA failure and carve that right out of the sole-remedy wording.
- Optional draft language: brief only, not requested.
- Confidence: Med (Exhibit B not provided).

**Issue 3: Unlimited annual fee increases.**
- Where: s.4.2 "may increase the Fees on each anniversary ... by giving Customer 30 days' written notice".
- What the contract says: no cap and no Customer exit is stated.
- Inference: price over the term is unknown at signing.
- Why it matters: the business case for the platform rests on a cost that the Supplier can change alone.
- Proposed fix: cap increases (for example the lower of a fixed percentage and an index); give Customer a right to terminate on notice of an increase above the cap; 90 days' notice.
- Optional draft language: brief only, not requested.
- Confidence: High.

**Issue 4: Supplier data use right undefined in scope.**
- Where: s.11 "Supplier may use Customer Data in aggregated form to improve the Services".
- What the contract says: an aggregated-use right; "Customer Data" is not defined in the provided text.
- Inference: Tallow Creek's stock and sales patterns could feed models that serve competitors.
- Why it matters: commercially sensitive data; data protection treatment is jurisdiction-dependent if any personal data is included.
- Proposed fix: limit to aggregated and anonymized data that cannot identify Customer; no use for training models offered to third parties without consent; deletion on termination.
- Optional draft language: brief only, not requested.
- Confidence: Med (definition not provided).

**6. Negotiation Package**

- Must have: higher cap with confidentiality, data protection and IP carve-outs (Issue 1); termination right for repeated SLA failure (Issue 2).
- Nice to have: fee-increase cap with exit (Issue 3); narrowed data use (Issue 4).
- Can concede: the 30-day payment term (s.4.1); the indirect-loss exclusion, if lost profit from Supplier's failure is expressly recoverable up to the cap.
- (C) Negotiation strategy: trade the fee-cap request against a longer initial term if Quillmere values commitment, and hold firm on the liability carve-outs.

**7. Uncertainty Register**

- Missing: Order Form 1; Exhibit B; Sections 1 to 3, 5, 7, 8, 10, 12 and 13. Venue or forum for disputes: Not found.
- Undefined terms in the provided text: "Fees", "Services", "Customer Data", "Effective Date".
- Ambiguous: whether "loss of ... data" in s.9.1 excludes recovery for Supplier's loss of Customer Data.
- Missing cross-references: none in the provided text.

**8. One-Page Summary**

Top 5 risks and recommended positions:
1. Liability cap of three months' Fees (s.9.2): raise and carve out confidentiality, data protection and IP.
2. Credits as sole remedy (s.6): obtain Exhibit B; add termination for repeated failure.
3. Uncapped fee increases (s.4.2): cap and add an exit.
4. Supplier use of Customer Data (s.11): narrow and require anonymization.
5. Excerpt only: no view on warranties, indemnities, termination or security until the full agreement is provided.

**Gate self-check:** Gate 1 pass, with missing documents listed; Gate 2 pass; Gate 3 pass (law Found, venue Not found); Gate 4 pass (13 buckets addressed or marked Not in provided text); Gate 5 pass; Gate 6 pass; Gate 7 pass. No banner required.

Decision-support only. Final Liability rests with the Human.

---

Final Liability rests with the Human.
