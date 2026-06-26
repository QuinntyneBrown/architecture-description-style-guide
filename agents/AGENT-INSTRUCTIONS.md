# Agent Instructions

Operating instructions for a coding agent that uses this guide to **check**, **correct**, or
**author** architecture description (AD) prose. Treat this file as your task contract: when a
user asks you to review or write an AD under this guide, follow it.

Your single objective: every document you touch must read as though **one entity wrote it
for one audience**, use the controlled vocabulary of ISO/IEC/IEEE 42010:2022 exactly, and —
when it claims conformance — contain everything Clause 6 requires.

---

## 1. What to load before you start

Load these as your source of truth, in this order of authority:

1. [`../resources/data/terminology.yaml`](../resources/data/terminology.yaml) — the 19
   defined terms, deprecated terms, and neighbouring-term distinctions.
2. [`../resources/data/substitutions.yaml`](../resources/data/substitutions.yaml) — the
   find→replace map with severities.
3. [`../resources/data/style-rules.yaml`](../resources/data/style-rules.yaml) — the lint
   rules (regex + heuristic), each with a stable `id`.
4. The checklists in [`../checklists/`](../checklists/) — your review passes.
5. The prose chapters in [`../docs/`](../docs/) — the reasoning behind the rules, for when a
   rule needs judgement.

**Precedence when sources conflict:** the standard governs → then this guide's prose
chapters → then the data files. The data files are derived; if you find a data file
contradicting a prose chapter or the standard, flag it as a guide defect rather than
applying it.

## 2. Mode A — Check (review without editing)

Produce findings; do not change the text.

1. **Mechanical pass.** Apply every `regex` rule in `style-rules.yaml` and every
   `deprecated_terms` / `normative_force` / `voice` entry in `substitutions.yaml`. Each hit
   is a candidate finding.
2. **Heuristic pass.** For each `heuristic` rule, read the relevant span and judge: view vs.
   viewpoint swaps (`AD-VOC-002`), agentless passive (`AD-EXP-001`), definition form
   (`AD-EXP-003`), and the conformance heuristics (`AD-CONF-*`).
3. **Checklist pass.** Walk [`prose-checklist.md`](../checklists/prose-checklist.md); if the
   document claims to be an AD, also walk
   [`conformance-checklist.md`](../checklists/conformance-checklist.md); for a finished
   document or set, walk [`review-checklist.md`](../checklists/review-checklist.md).
4. **Suppress false positives.** A rule may legitimately not apply (e.g. "you" inside a
   directly quoted stakeholder concern, or "model" referring to a domain model that is
   genuinely the EoI). When you suppress a hit, say why.
5. **Report** in the finding format of §5.

## 3. Mode B — Correct (edit to conform)

1. **Run Mode A first** to know what is wrong.
2. **Apply error-severity fixes** — deprecated terms, normative-force words, first/second
   person. These are mechanical where `replace_with` is given; where it is `null`, follow the
   `action` and rewrite, preserving meaning.
3. **Apply warning-severity fixes** unless context justifies keeping the text; if you keep
   it, note why.
4. **Preserve meaning and facts.** Never invent architecture content to satisfy a rule. If a
   requirement is unclear ("must be fast"), do not guess a number — flag it as
   `AD-EXP-006` for the author to supply.
5. **Do not over-correct.** Change what violates a rule; leave conforming text alone. Do not
   restructure a document in Correct mode unless a conformance section is genuinely absent —
   that is Author mode.
6. **Re-run Mode A** on your output; iterate until no error-severity findings remain.
7. **Report** what you changed, grouped by rule id, and what you deliberately left.

## 4. Mode C — Author (write a new AD or section)

1. **Start from the template** in
   [`../resources/templates/`](../resources/templates/) that matches the artifact (full AD,
   viewpoint, or decision record).
2. **Write in the single voice** from the outset — impersonal, declarative, third person;
   normative force only via shall/should/may. Do not draft loosely and clean up later; draft
   in voice.
3. **Use only the controlled vocabulary**; identify EoI-local terms on first use in
   genus–differentia form.
4. **Satisfy the coverage obligations as you write** — every concern framed by a viewpoint,
   every view governed by one viewpoint, every decision paired with rationale.
5. **Ask, don't invent, for missing facts.** If you lack a stakeholder, a concern, a
   quantity, or a rationale, mark it `<TO SUPPLY: …>` rather than fabricating it.
6. **Self-review** with Modes A and the conformance checklist before returning.

## 5. Finding and report format

Report findings as a list, one per line, each with the rule id, location, the offending
text, and the fix. Order: errors, then warnings, then info.

```
<RULE-ID> [<severity>] <location> — "<offending text>" — <fix>
```

Example:

```
AD-VOC-001  [error]   §3, para 2   — "the system of interest" — use "the entity of interest".
AD-NORM-001 [error]   §7.1         — "the gateway must authenticate" — requirement: "shall".
AD-VOICE-001[error]   §1 overview  — "we selected" — record as a decision (ADR), impersonal.
AD-REG-001  [warning] §1 overview  — "robust, world-class" — delete; state limits/evidence.
AD-EXP-001  [warning] §7.2         — "requests are authenticated" — name the actor (active).
AD-CONF-002 [error]   document     — concern C-05 (privacy) is framed by no viewpoint.
```

Close with a one-line **verdict**: `conforming`, `conforming after listed fixes`, or
`non-conforming` (with the blocking items named). For a review of voice/consistency, use the
verdict scheme in [`review-checklist.md`](../checklists/review-checklist.md).

## 6. Hard rules — never violate

- **Never use or leave a deprecated term**: *system of interest, architecture framework,
  architecture model, correspondence rule*.
- **Never express a requirement with "must"** or with emphasis; only **shall**.
- **Never write in first or second person** in AD prose.
- **Never fabricate architecture facts** (stakeholders, concerns, quantities, rationale) to
  pass a check. Flag the gap instead.
- **Never weaken the standard's requirements**; tailoring is not permitted for a conformance
  claim.
- **When unsure whether a word is a defined term**, consult `terminology.yaml` and the
  glossary; the term bank wins over intuition.

## 7. Self-test

Before trusting your own checking, run yourself against
[`../evals/`](../evals/): each case in [`../evals/cases/`](../evals/cases/) gives flawed
input and the issues you should detect (and often a reference correction). Score yourself
with [`../evals/rubric.md`](../evals/rubric.md). If you miss expected findings or raise
findings not supported by a rule, recalibrate before reviewing real documents.
