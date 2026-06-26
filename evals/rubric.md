# Eval Rubric

How to score an agent's performance against this guide. Use it for the cases in
[`cases/`](cases/) and for spot-checks on real documents. Scoring is per **dimension**;
report a score per dimension and an overall verdict, not a single blended number — the
dimensions fail in different ways and matter differently.

The five dimensions mirror the guide: vocabulary, voice, normative force, conformance, and
expression/structure.

---

## Scoring model

Each case ships with a key: the set of **expected findings** (rule ids the agent should
raise), and, for correction/authoring cases, a **reference output**. Score detection as a
classification problem, then judge any rewrite.

For each dimension, on a checking case:

- **True positives (TP):** expected findings the agent correctly raised.
- **False negatives (FN):** expected findings the agent missed. *(The costly error.)*
- **False positives (FP):** findings the agent raised that no rule supports, or that the
  case explicitly marks as acceptable.

Compute, per dimension:

- **Recall** = TP / (TP + FN) — did it catch the real problems?
- **Precision** = TP / (TP + FP) — did it avoid crying wolf?

A dimension **passes** a case when recall = 1.0 for **error-severity** findings (no missed
errors) and precision ≥ 0.8 overall (few false alarms). Missing a warning/info finding
lowers the score but does not fail the dimension.

## The five dimensions

| # | Dimension | What it measures | Backing rules |
|---|---|---|---|
| 1 | **Vocabulary fidelity** | Catches deprecated terms, wrong term for a concept, view/viewpoint and neighbouring-term confusion, casing, abbreviation expansion. | `AD-VOC-*`, `substitutions.yaml` deprecated/wrong-term |
| 2 | **Voice consistency** | Catches first/second person, self-production reference, rhetorical questions, register drift; on review cases, judges the single-voice property. | `AD-VOICE-*`, review-checklist A–F |
| 3 | **Normative correctness** | Catches non-`shall` obligation, diluted/inflated forms, emphasis-as-requirement, multiple obligations per sentence. | `AD-NORM-*` |
| 4 | **Conformance content** | Catches missing Clause-6 items, unframed concerns, decisions without rationale, views without a governing viewpoint, omitted known inconsistencies. | `AD-CONF-*`, conformance-checklist |
| 5 | **Expression & structure** | Catches agentless passive, over-long sentences, bad definition form, non-parallel lists, positional references, unquantified limits, hype/filler. | `AD-EXP-*`, `AD-REG-*` |

## Judging rewrites (correction and authoring cases)

When the agent edits or authors, score the output text on three more axes (0–2 each):

- **Correctness preserved (0–2):** Did the rewrite keep the original meaning and facts, and
  invent nothing? *(0 = fabricated architecture content — automatic case failure.)*
- **Conformance of the output (0–2):** Does the rewritten text now pass the prose checklist
  (and, for AD-level cases, the conformance checklist)?
- **Voice match (0–2):** Does the output read in the single voice — indistinguishable from
  the guide's reference samples and from other documents of the same entity?

**Fabrication is the cardinal sin.** An agent that invents a stakeholder, a quantity, or a
rationale to pass a check fails the case regardless of other scores. Flagging a gap
(`<TO SUPPLY: …>`) is the correct behaviour and scores full marks for that item.

## Per-case verdict

- **Pass** — all five detection dimensions pass, and (if applicable) every rewrite axis ≥ 1
  with Correctness = 2.
- **Pass with notes** — detection passes; a warning/info finding missed or a rewrite axis at
  1.
- **Fail** — any missed error-severity finding, any unsupported error-severity false
  positive, or any fabrication.

## Suite-level reporting

Report a table of cases × dimensions with pass/fail, plus aggregate recall and precision per
dimension across the suite. Track these over time; a regression in **recall on error-severity
findings** is the signal that matters most. Note any case where the agent's behaviour
revealed a gap in the rules themselves — that is a prompt to improve the guide, not just the
agent.
