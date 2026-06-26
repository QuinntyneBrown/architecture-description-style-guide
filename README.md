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
| Use it with a local model (Ollama) in a web IDE | [`docs/using-with-ollama.md`](docs/using-with-ollama.md) · [`resources/ollama/context-pack.md`](resources/ollama/context-pack.md) |
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
│   ├── glossary.md                 Canonical term definitions with clause references
│   └── using-with-ollama.md        Local-model (Ollama) + web-IDE workflow
├── resources/
│   ├── data/
│   │   ├── terminology.yaml         Machine-readable term bank
│   │   ├── substitutions.yaml       Deprecated/forbidden → preferred replacements
│   │   └── style-rules.yaml         Lint-style rules an agent can apply mechanically
│   ├── templates/
│   │   ├── architecture-description-template.md   Clause-6 conforming AD skeleton
│   │   ├── viewpoint-template.md                  Architecture viewpoint specification
│   │   └── decision-record-template.md            Architecture decision + rationale
│   └── ollama/                     For local models (no file access — bundle the rules)
│       ├── context-pack.md         THE file you upload: all rules in one self-contained doc
│       ├── system-prompt.md        Short system prompt for Open WebUI / Continue / Modelfile
│       └── Modelfile               Build a custom "ad-style" model that knows the guide
├── checklists/
│   ├── prose-checklist.md          Vocabulary, voice, and expression checks
│   ├── conformance-checklist.md    Clause-6 required-content checks
│   └── review-checklist.md         Whole-document single-voice review
├── evals/
│   ├── README.md                   How the evals work and how to run them
│   ├── rubric.md                   Scoring rubric across five dimensions
│   ├── cases.yaml                  Index of eval cases
│   ├── cases/                      Individual cases: flawed input → reference output
│   └── ollama-smoke-test.md        One-minute go/no-go for a local model
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

## Practical usage — driving an agent with the guide

You do **not** upload the guide each time. A coding agent (Claude Code in the web IDE, an
IDE extension, or the CLI) works against a **repository**, so the reliable pattern is:
*make the guide readable in the repo, then point the agent at one entry file* —
[`agents/AGENT-INSTRUCTIONS.md`](agents/AGENT-INSTRUCTIONS.md). The agent loads the term
bank, substitutions, rules, and checklists itself, exactly as that file instructs.

### Getting the guide in front of the agent

**If your document lives in this repo** (or you add this repo's files to your project):
nothing to upload — the agent reads the files directly. This is the recommended setup.

**If your document lives in a different project**, make the guide available, easiest first:

1. **Copy the essentials in.** Add these to your project: `agents/AGENT-INSTRUCTIONS.md`,
   `resources/data/terminology.yaml`, `resources/data/substitutions.yaml`,
   `resources/data/style-rules.yaml`, and the checklist(s) you want
   (`checklists/prose-checklist.md`, and `conformance-checklist.md` for whole documents).
2. **Add this repo as a subfolder or git submodule** of your project.
3. **Paste as a fallback.** If you cannot add files, paste
   [`checklists/prose-checklist.md`](checklists/prose-checklist.md) and the deprecated-terms
   table from [`docs/glossary.md`](docs/glossary.md) into the chat with your text. This
   works but is heavier — you re-paste every time, and the agent cannot consult the full
   rules — so prefer (1) or (2).

> **In the web IDE specifically:** the agent operates on the connected GitHub repo. Put the
> guide files in that repo (setups 1–2 above), open or paste your document, and prompt as
> below. There is no separate "upload a checklist" step — referencing the files in the repo
> is what replaces it.

### Example 1 — Fix the overview paragraph of a document *(the common case)*

This is the scenario most people start with. Mode: **Correct**.

Prompt to the agent:

> Using the style guide in this repo, start from `agents/AGENT-INSTRUCTIONS.md` and run
> **Correct mode** on the overview paragraph below. Apply all error-severity fixes, apply
> warnings unless context forbids it, list every change by rule id, and flag any missing
> fact with `<TO SUPPLY>` rather than inventing it. Return the rewritten paragraph plus the
> change list.
>
> ```
> We built a really robust, world-class settlement platform that leverages an event-driven
> design. The system of interest must process trades quickly, and as you can see it scales
> very well.
> ```

What you get back (shape, per `AGENT-INSTRUCTIONS.md §5`):

> **Rewritten:**
> "The architecture is an event-driven settlement platform. The entity of interest settles
> trades within `<TO SUPPLY: latency target>`."
>
> **Changes:**
> ```
> AD-VOICE-001 [error]   "We built"            — first person; stated impersonally.
> AD-VOC-001   [error]   "system of interest"  — deprecated; "entity of interest".
> AD-NORM-001  [error]   "must process"        — requirement: "shall settle … within <target>".
> AD-REG-001   [warning] "robust, world-class" — hype with no fact; removed.
> AD-REG-002   [warning] "really … very well"  — intensifiers; removed.
> AD-VOICE-002 [error]   "as you can see"       — reader address; removed.
> AD-REG-004   [info]    "leverages"           — "uses" (here: "event-driven design").
> ```
> *Flagged:* the latency target was asserted vaguely ("quickly") and is left as `<TO SUPPLY>`.

Note the agent does **not** guess a latency number — it flags the gap. That is the correct
behaviour (`AGENT-INSTRUCTIONS.md §6`).

### Example 2 — Check a paragraph without changing it

Mode: **Check**. Use this to see findings before deciding what to edit.

> Using the style guide (`agents/AGENT-INSTRUCTIONS.md`), run **Check mode** on the text
> below — report findings as `rule-id [severity] location — "text" — fix`, but do not edit.
> [paste text]

### Example 3 — Write a new section from facts

Mode: **Author**. Supply the facts; the agent writes in the single voice.

> Using the style guide, **Author** the Concerns (§4) section of an AD. Stakeholders:
> operators (SH-01), the data protection officer (SH-03). Concerns: ingest throughput
> (operators); personal-data retention (SH-03). The retention period is undecided. Use the
> template in `resources/templates/architecture-description-template.md`, write in the
> guide's voice, and mark anything undecided `<TO SUPPLY>` — do not invent values.

### Example 4 — Review a whole document for conformance and voice

Mode: **Check** + the checklists.

> Using the style guide, review `docs/architecture-description.md` against
> `checklists/conformance-checklist.md` and `checklists/prose-checklist.md`. Produce a
> conformance table (each Clause-6 item present / partial / absent) and a findings list, then
> a one-line verdict.

### Example 5 — Make a set of documents sound like one author

Mode: **Review** across files.

> Using the style guide and `checklists/review-checklist.md`, review these documents
> together for single-voice consistency: [list the files]. Report term drift, register
> drift, and citation-style differences across them, and give the review verdict.

### Tips for reliable results

- **Always name the entry file** — "start from `agents/AGENT-INSTRUCTIONS.md`" — so the
  agent loads the rules instead of relying on memory.
- **State the mode** — Check, Correct, or Author. They produce different outputs.
- **Tell it not to fabricate.** The instruction to flag gaps with `<TO SUPPLY>` is built into
  the guide, but restating it in the prompt is cheap insurance.
- **Trust the term bank over the agent's intuition** — if a fix looks wrong, check it against
  [`docs/glossary.md`](docs/glossary.md); the glossary and standard govern.
- **Iterate in Correct mode** — ask the agent to re-run Check on its own output until no
  error-severity findings remain.

## Using this repo with a local model (Ollama + web IDE)

The setups above assume an agent that can **read this repository**. A local model run by
[Ollama](https://ollama.com/) — driven from a web IDE like
[Open WebUI](https://openwebui.com/) or an editor extension — **cannot**: it is a chat model
with no file access, so it only knows what is in its context window.

So the workflow is different in exactly one way: **you put the rules into the model's
context.** This repo ships a single self-contained bundle for that —
[`resources/ollama/context-pack.md`](resources/ollama/context-pack.md) — which flattens
every rule, the vocabulary, the conformance checklist, and the output format into one file.

> **What do I upload with my prompt?** Just one file: **`resources/ollama/context-pack.md`**.
> Attach it (or paste it), then paste your text with a mode word — `CHECK`, `CORRECT`, or
> `AUTHOR`. You do **not** upload the 30 separate files; the pack is the whole guide,
> flattened.

**Simplest one-off workflow (Open WebUI):**

1. `ollama pull qwen2.5:14b` *(or any capable instruction model — 8B works, 14B+ is better)*.
2. Start a chat, **attach `resources/ollama/context-pack.md`**.
3. Paste your text with a mode word, e.g.:
   > `CORRECT` mode, per the attached style guide pack. Rewrite the overview paragraph below;
   > list what you changed; flag missing facts with `<TO SUPPLY>`, don't invent them.
   >
   > *[paste your paragraph]*

**Simplest recurring workflow (upload nothing per prompt):** bake the pack into a custom
model once — either as an Open WebUI "Model" with the pack attached as knowledge, or with the
generator one-liner that builds a self-contained `ad-style` model. Both are in
[`docs/using-with-ollama.md`](docs/using-with-ollama.md), along with model recommendations,
a short [system prompt](resources/ollama/system-prompt.md), a
[`Modelfile`](resources/ollama/Modelfile), and troubleshooting.

**Check your model first.** Local models vary; run the one-minute
[`evals/ollama-smoke-test.md`](evals/ollama-smoke-test.md) — four tiny cases with obvious
answers — to see whether yours is reliable enough before trusting it on real documents.

*Local models are great for fast, private, paragraph-level Check/Correct. For whole-document
conformance across many files, or scoring against the [evals](evals/), use a file-reading
agent (Claude Code) — same rules, longer reach.*

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
