# Prose Checklist — Vocabulary, Voice, and Expression

A line- and sentence-level check for any AD prose. Run it whenever text is written or
edited. Each item cites the rule it enforces (see
[`../resources/data/style-rules.yaml`](../resources/data/style-rules.yaml)) so findings can
be reported with a stable identifier.

**How to use it.** Read the prose once per group below. A `[ ]` that cannot be checked is a
finding; record it as `RULE-ID — location — what is wrong — fix`. Errors block; warnings
should be fixed unless context justifies them; info items are preferences.

---

## A. Vocabulary (errors block)

- [ ] **No deprecated 42010 terms.** None of: *system of interest*, *architecture
  framework*, *architecture model*, *correspondence rule*. `AD-VOC-001`
- [ ] **Defined concepts use their defined term.** No *blueprint*, *design doc*,
  *architecture document* where a 42010 term is meant. `AD-VOC-001`, wrong-term rules
- [ ] **view vs. viewpoint correct.** Conventions ⇒ *viewpoint*; applied result ⇒ *view*.
  `AD-VOC-002`
- [ ] **No bare "model" as an AD element.** Use *view component* governed by a *model
  kind*. `AD-VOC-003`
- [ ] **Neighbouring terms not confused** — concern/requirement, stakeholder/user,
  perspective/viewpoint, aspect/concern, correspondence/correspondence method. (glossary
  §"do not confuse")
- [ ] **Defined terms lowercase** in running text (except sentence start / heading).
  `AD-VOC-004`
- [ ] **Abbreviations expanded on first use**, then used in short form (AD, ADF, ADL, EoI,
  and EoI-local). `AD-VOC-005`
- [ ] **EoI-local terms named once and used unchanged**; no drift between synonyms for the
  same component. (03-vocabulary §3.9)

## B. Voice (errors block)

- [ ] **No first person** — no *we, our, us, I*. `AD-VOICE-001`
- [ ] **No second person** — no *you, your*; the reader is not addressed. `AD-VOICE-002`
- [ ] **No self-production reference** — the AD does not say it "was generated" or "will
  now describe." `AD-VOICE-003`
- [ ] **No rhetorical questions.** `AD-VOICE-004`
- [ ] **Third-person declarative throughout**; the subject is the EoI, an AD element, or
  the architecture. (02-voice §2.3)
- [ ] **Decisions recorded, not narrated** — preferences and feelings do not appear; the
  deciding body may be named only in a decision record. (02-voice §2.1)

## C. Normative force (errors block)

- [ ] **Requirements use "shall"; recommendations "should"; permissions "may."** No *must,
  need to, has to, is required to* for obligation. `AD-NORM-001`
- [ ] **No diluted/inflated forms** — no *shall ideally, should always, must absolutely,
  shall try to*. `AD-NORM-002`
- [ ] **Emphasis is not obligation** — no *it is critical/essential that* standing in for a
  requirement. `AD-NORM-003`
- [ ] **One verbal form per normative sentence.** `AD-NORM-004`
- [ ] **Prohibitions use "shall not."** (04-expression §4.2)

## D. Register (warnings)

- [ ] **No hype adjectives** — *robust, seamless, powerful, cutting-edge, world-class,
  best-in-class, state-of-the-art*. `AD-REG-001`
- [ ] **No vague intensifiers/fillers** — *very, really, quite, simply, obviously, of
  course, basically, essentially, arguably*. `AD-REG-002`
- [ ] **No empty openers** — *it should be noted that, it is important to…, as mentioned
  above, in order to*. `AD-REG-003`
- [ ] **No hype verbs** — *leverage, utilize, synergy* → plain verbs. `AD-REG-004`
- [ ] **No vague quantifiers** where a number is knowable — *a number of, several, many,
  various*. `AD-REG-005`

## E. Expression (warnings / info)

- [ ] **No agentless passive** — the element that acts is named. `AD-EXP-001`
- [ ] **Sentences assert one thing**; long, multi-clause obligation sentences split.
  `AD-EXP-002`
- [ ] **Local definitions in genus–differentia form** — noun phrase, no leading article, no
  terminal period. `AD-EXP-003`
- [ ] **Lists parallel and complete the lead-in.** `AD-EXP-004`
- [ ] **Cross-references by identifier and name**, not by position ("above/below").
  `AD-EXP-005`
- [ ] **Quantities stated, not gestured at**; units explicit and consistent. `AD-EXP-006`
- [ ] **Figures numbered and captioned**; the prose introduces and interprets each;
  view-component figures state their model kind or legend. (04-expression §4.8)
- [ ] **Identifiers, paths, endpoints in code formatting**, not used for emphasis.
  (04-expression §4.9)

---

### Finding format

```
AD-NORM-001 — §7.2, para 3 — "the gateway must authenticate" — requirement: use "shall".
AD-REG-001 — §1, overview — "robust, world-class platform" — delete; state the tolerated
             failure modes and measured limits, or remove the claim.
```
