# Architecture Description Style Guide

A style guide for the **vocabulary and expression** of architecture description (AD)
documents, grounded in **ISO/IEC/IEEE 42010:2022**, *Software, systems and enterprise —
Architecture description*.

The guide exists so that every AD produced under it — regardless of author, tool, or
date — reads as though it were **written by one entity for one audience**. It supplies
the controlled vocabulary, the register, the sentence-level conventions, and the
document structure that make a set of independently authored documents sound like a
single, deliberate body of work.

It is written to be used by humans **and** by coding agents. The prose chapters state the
rules; the machine-readable resources, checklists, and evals let an agent *apply* those
rules — to check an existing document, correct it, or author a new one — and let a
maintainer *measure* how well it did.

---

## What this is for

| You want to… | Start here |
|---|---|
| Understand the standard this guide rests on | [`docs/01-foundations.md`](docs/01-foundations.md) |
| Learn the single voice every document must share | [`docs/02-voice-and-register.md`](docs/02-voice-and-register.md) |
| Use the right word for a concept | [`docs/03-vocabulary.md`](docs/03-vocabulary.md) · [`docs/glossary.md`](docs/glossary.md) |
| Write sentences, definitions, and lists correctly | [`docs/04-expression.md`](docs/04-expression.md) |
| Lay out a conforming AD document | [`docs/05-document-structure.md`](docs/05-document-structure.md) · [`resources/templates/`](resources/templates/) |
| Check or correct prose as an agent | [`agents/AGENT-INSTRUCTIONS.md`](agents/AGENT-INSTRUCTIONS.md) |
| Run a review by hand | [`checklists/`](checklists/) |
| Measure an agent against the guide | [`evals/`](evals/) |

## Repository map

```
.
├── README.md                       This file — front door and map
├── docs/                           The style guide proper (normative prose)
│   ├── 01-foundations.md           42010:2022 grounding: model, terms, conformance
│   ├── 02-voice-and-register.md    The single-entity voice: audience, persona, register
│   ├── 03-vocabulary.md            Controlled vocabulary and term-usage rules
│   ├── 04-expression.md            Sentence, definition, list, and reference rules
│   ├── 05-document-structure.md    How a conforming AD document is organized
│   └── glossary.md                 Canonical term definitions with clause references
├── resources/
│   ├── data/
│   │   ├── terminology.yaml         Machine-readable term bank
│   │   ├── substitutions.yaml       Deprecated/forbidden → preferred replacements
│   │   └── style-rules.yaml         Lint-style rules an agent can apply mechanically
│   └── templates/
│       ├── architecture-description-template.md   Clause-6 conforming AD skeleton
│       ├── viewpoint-template.md                  Architecture viewpoint specification
│       └── decision-record-template.md            Architecture decision + rationale
├── checklists/
│   ├── prose-checklist.md          Vocabulary, voice, and expression checks
│   ├── conformance-checklist.md    Clause-6 required-content checks
│   └── review-checklist.md         Whole-document single-voice review
├── evals/
│   ├── README.md                   How the evals work and how to run them
│   ├── rubric.md                   Scoring rubric across five dimensions
│   ├── cases.yaml                  Index of eval cases
│   └── cases/                      Individual cases: flawed input → reference output
└── agents/
    └── AGENT-INSTRUCTIONS.md        Operating instructions for a coding agent
```

## The three things every document must get right

1. **The right words.** Use the 19 defined terms of 42010:2022 exactly, and never their
   deprecated 2011 predecessors. *Architecture model* is now **view component**;
   *architecture framework* is now **architecture description framework (ADF)**;
   *correspondence rule* is now **correspondence method**; *system of interest* is now
   **entity of interest (EoI)**. See [`docs/03-vocabulary.md`](docs/03-vocabulary.md).

2. **The right voice.** One impersonal, precise, declarative register, addressed to the
   same audience throughout, with normative force carried only by **shall**, **should**,
   and **may**. See [`docs/02-voice-and-register.md`](docs/02-voice-and-register.md).

3. **The right contents.** An AD that claims conformance must address every required
   content item of Clause 6 — stakeholders, stakeholder perspectives, concerns, aspects,
   viewpoints, views, view components, correspondences, and decisions with rationale. See
   [`docs/05-document-structure.md`](docs/05-document-structure.md) and
   [`checklists/conformance-checklist.md`](checklists/conformance-checklist.md).

## How to use it as an agent

Read [`agents/AGENT-INSTRUCTIONS.md`](agents/AGENT-INSTRUCTIONS.md). In short: load
[`resources/data/terminology.yaml`](resources/data/terminology.yaml) and
[`resources/data/substitutions.yaml`](resources/data/substitutions.yaml) as your source of
truth for words; apply [`resources/data/style-rules.yaml`](resources/data/style-rules.yaml)
and the checklists as your review pass; and report findings in the format the agent
instructions define. When in doubt about a word, the glossary and term bank win.

## A note on authority

This guide is a **house style**; it is not the standard and does not replace it. Where it
states a fact about 42010:2022 it is faithful to the standard's public text, but the
normative requirements of the standard are the standard's own. Definitions reproduced here
are marked as verbatim or paraphrased, with their clause numbers, in
[`docs/glossary.md`](docs/glossary.md). When this guide and the standard appear to
disagree, the standard governs and this guide should be corrected.

## Conventions used throughout this guide

- The standard is cited as **42010:2022** with clause numbers, e.g. *(42010:2022, 3.8)*.
- Defined terms appear in lowercase in running text, as the standard writes them.
- Examples of AD prose are shown in the prescribed voice; the **instructional** text of
  this guide uses the imperative ("Use…", "Do not…") because it addresses an author, not a
  reader of an AD. Do not carry the guide's imperative voice into an AD.
- ✅ marks conforming examples; ❌ marks non-conforming ones.
