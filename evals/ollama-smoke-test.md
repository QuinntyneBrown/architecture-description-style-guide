# Ollama smoke test — is my local model good enough?

A one-minute go/no-go for a local model before you trust it on real documents. Four tiny
cases with obvious right answers — you can eyeball pass/fail without a harness. Unlike the
full suite in [`cases/`](cases/) (built for capable agents), this is tuned so that a
*usable* local model can pass it.

## How to run it

1. Set the model up with the pack in context — easiest is the custom model from
   [`../docs/using-with-ollama.md`](../docs/using-with-ollama.md) (Option 3 or 4). Otherwise
   attach/paste [`../resources/ollama/context-pack.md`](../resources/ollama/context-pack.md).
2. Send each test below **in CHECK mode**, one at a time. Do **not** show the model the
   "Expected" block.
3. Compare to the expected result. Score with the rubric at the bottom.

---

## Test 1 — deprecated term (vocabulary)

**Prompt:** `CHECK mode, per the pack: "The system of interest exposes three services."`

**Expected:** one finding — `VOC [error]` — "system of interest" is deprecated; use **entity
of interest**. Verdict: `needs fixes (1)`. *(Exact verdict wording doesn't matter; the
finding does.)*

**Pass if:** the model flags "system of interest" and names "entity of interest" as the fix.

---

## Test 2 — normative force

**Prompt:** `CHECK mode, per the pack: "The gateway must authenticate every request."`

**Expected:** one finding — `NORM [error]` — "must" is not a 42010 verbal form; a
requirement uses **shall** → "The gateway shall authenticate every request."

**Pass if:** the model flags "must" and proposes "shall".

---

## Test 3 — voice (person)

**Prompt:** `CHECK mode, per the pack: "We chose PostgreSQL because we needed strong consistency."`

**Expected:** finding(s) — `VOICE [error]` — first person ("We … we"); state impersonally
and record as a decision, e.g. "The architecture selects PostgreSQL to obtain strong
consistency (see ADR-…)."

**Pass if:** the model flags the first person and recasts it impersonally (it need not
invent an ADR number).

---

## Test 4 — clean control (precision)

**Prompt:** `CHECK mode, per the pack: "The gateway shall authenticate every request before any service processes it."`

**Expected:** **no findings.** Verdict: `clean`. (Correct vocabulary, a proper "shall",
third person, a named actor.)

**Pass if:** the model reports zero problems. Flagging anything here is a **false positive**
— the model is over-triggering.

---

## Scoring

| Result | Verdict |
|---|---|
| Passes all four (catches 1–3, clean on 4) | **Good** — trust it for CHECK and CORRECT; spot-check CORRECT output. |
| Passes 1–3 but flags something on 4 | **Usable, over-eager** — fine for CHECK (you filter), be cautious in CORRECT. Lower temperature. |
| Misses test 1 or 2 (the error-level basics) | **Not ready** — try a larger model, confirm the pack is actually in context, lower temperature, and re-run. |
| Invents facts anywhere (e.g. a made-up latency in a CORRECT variant) | **Reject for CORRECT/AUTHOR** — it violates the no-fabrication rule; use only for CHECK, or switch models. |

If the model fails, the most common cause is that **the pack is not in its context** — verify
with: *"Which rule set are you following?"* It should name the Architecture Description Style
Guide Context Pack. Then re-test.

## Optional: stronger check

If your model passes all four, run the real cases [`01`](cases/01-deprecated-terms.md),
[`02`](cases/02-normative-force.md), and [`08`](cases/08-clean-passes.md) and score with
[`rubric.md`](rubric.md). A model that handles those is ready for paragraph-level work on
real documents.
