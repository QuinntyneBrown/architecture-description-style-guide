# 01 — Foundations

This chapter states what the guide rests on: the standard, the model of concepts it
defines, the vocabulary it controls, and the content it requires of a conforming
architecture description. Everything else in the guide — the voice, the word rules, the
checklists, the evals — derives from what is recorded here. Read this first.

> **Source of authority.** ISO/IEC/IEEE 42010:2022, *Software, systems and enterprise —
> Architecture description* (second edition, 2022-11). It is the joint ISO/IEC/IEEE
> successor to ISO/IEC/IEEE 42010:2011 and to IEEE Std 1471-2000. Throughout this guide it
> is cited as **42010:2022**, with clause numbers where useful, e.g. *(42010:2022, 3.8)*.

---

## 1.1 What the standard governs — and what it does not

42010:2022 specifies **requirements for the structure and expression of an architecture
description (AD)**. It governs the *description*, not the *architecture* and not the
*entity*. Three boundaries follow from this, and the guide observes all three.

- **An architecture is not an AD.** An architecture is intangible and abstract — the
  fundamental concepts, properties, and governing principles of an entity. An AD is a
  tangible work product that *expresses* an architecture. The guide is a guide to writing
  ADs; it never instructs the reader on what an architecture *should be*.
- **The standard does not prescribe process, method, notation, tool, or format.** It says
  what an AD must *contain* and how its concepts must *relate*, not how to produce it.
  This guide adds house conventions for vocabulary and expression on top of those
  requirements; it does not invent new requirements.
- **The standard applies to many kinds of entity.** Software, systems, enterprises,
  systems of systems, product lines, services, business domains, and more. The single
  term for the subject of an AD is the **entity of interest (EoI)**.

## 1.2 The conceptual model

The defined terms of 42010:2022 form a connected model. An author who holds this model in
mind will reach for the right word automatically, because each term names one node in it.
The relationships below use the standard's own verbs and cardinalities.

```
                          expresses
   architecture  ◄─────────────────────────  architecture description (AD)
        │                                            │ comprises
        │ is the architecture of                     ▼
        ▼                                       AD elements
   entity of interest ──── situated in ───► environment

   stakeholder  ──── holds ────►  concern  ◄──── frames ────  architecture viewpoint
        (many-to-many)              ▲                                │ governs
                                    │ refine (many-to-many)          ▼
                                  aspect                      architecture view
                                                                    │ comprises
                                                                    ▼
                                                              view component
                                                                    │ governed by
                                                                    ▼
                                                       model kind  or  legend

   correspondence  ──── relates (2..*) ────►  AD elements
        │ governed by
        ▼
   correspondence method
```

Read the model as a set of sentences. Each is a sentence the guide expects to see written
correctly in an AD:

- An **AD** *expresses* an **architecture**; one architecture may be expressed by one or
  more ADs.
- An **architecture** is *the architecture of* an **entity of interest**, which is
  *situated in* an **environment**.
- An **AD** *comprises* **AD elements** — the named parts of the description (stakeholders,
  concerns, perspectives, aspects, viewpoints, views, view components, correspondences, and
  more). An AD may itself be treated as an AD element within another AD.
- A **stakeholder** *holds* one or more **concerns**; a concern may be held by more than one
  stakeholder. The relation is many-to-many.
- An **architecture viewpoint** *frames* one or more **concerns**. To *frame* a concern is
  "to shape, compose, give expression to" it — the work of stating the problem, as distinct
  from *addressing* it in a view.
- An **architecture viewpoint** *governs* one or more **architecture views**. (This is a
  2022 change: in 2011 a viewpoint governed exactly one view per AD.) Each **architecture
  view** is governed by exactly one viewpoint.
- An **architecture view** *comprises* **view components**. Each **view component** is
  *governed by* a **model kind** (when it is model-based) or *documented by* a **legend**
  (when it is not).
- An **aspect** is part of the entity's character; aspects and concerns relate
  many-to-many.
- A **correspondence** *relates* two or more **AD elements** and is *governed by* a
  **correspondence method**.
- **Architecture decisions** *pertain to* concerns and *affect* AD elements; **architecture
  rationale** *justifies* decisions. (These are concepts and required content, not Clause-3
  defined terms — see §1.4.)

## 1.3 The controlled vocabulary — 19 defined terms

Clause 3 of 42010:2022 defines exactly **nineteen** terms. These are the controlled
vocabulary of the guide. Use them precisely; do not coin synonyms for them; do not use a
broader word where one of these is meant. Their canonical definitions, marked verbatim or
paraphrased and with clause numbers, are in [`glossary.md`](glossary.md); the
machine-readable form is in [`../resources/data/terminology.yaml`](../resources/data/terminology.yaml).

| Clause | Term | Abbrev. |
|---|---|---|
| 3.1 | architecting | |
| 3.2 | architecture | |
| 3.3 | architecture description | AD |
| 3.4 | architecture description element | AD element |
| 3.5 | architecture description framework | ADF |
| 3.6 | architecture description language | ADL |
| 3.7 | architecture view | |
| 3.8 | architecture viewpoint | |
| 3.9 | aspect | |
| 3.10 | concern | |
| 3.11 | correspondence | |
| 3.12 | entity of interest | EoI |
| 3.13 | environment | |
| 3.14 | information part | |
| 3.15 | model kind | |
| 3.16 | specification | |
| 3.17 | stakeholder | |
| 3.18 | stakeholder perspective | |
| 3.19 | view component | |

### Terms renamed or introduced in 2022 — and the deprecated words to avoid

The second edition changed several terms. Documents written under this guide use the
2022 term and never its predecessor. These substitutions are enforced by
[`../resources/data/substitutions.yaml`](../resources/data/substitutions.yaml).

| Deprecated (pre-2022) | Use instead (42010:2022) | Why |
|---|---|---|
| system of interest | **entity of interest (EoI)** | Generalized so the standard applies beyond systems — to software, enterprises, products, services, and domains. |
| architecture framework | **architecture description framework (ADF)** | Distinguishes an ADF from other architecting frameworks (e.g. evaluation frameworks in 42030). |
| architecture model | **view component** | A view's parts may be model-based *or* not; "view component" covers both. A model-based view component is governed by a model kind. |
| correspondence rule | **correspondence method** | Renamed; a correspondence method governs correspondences. |

Terms **newly defined** in 2022 (use them where they apply): *aspect* (3.9), *stakeholder
perspective* (3.18), *architecture description element* (3.4), *information part* (3.14),
*specification* (3.16).

## 1.4 Words that are *not* controlled terms

Some words that recur in ADs are deliberately **not** defined terms in Clause 3. Treat
them as ordinary concepts or as named content items, not as part of the controlled
vocabulary, and do not capitalize or over-formalize them.

- **architecture decision** and **architecture rationale** — required *content* of an AD
  (Clause 6.10), and concepts in the model, but not Clause-3 terms.
- **system** — an *example* of an entity of interest, not a defined term. The standard
  "takes no position on what constitutes an entity." Prefer **entity of interest** when you
  mean the subject of the AD generically; use *system* only when the EoI genuinely is a
  system and you have said so.
- **model** — only **model kind** is defined. Speak of a *view component* governed by a
  *model kind*, not of "a model" as a free-standing AD element.

## 1.5 Conformance — the five targets

42010:2022 defines **five** things that can claim conformance, each against its own
requirements clause. The guide's checklists are organized around these.

| Conformance target | Requirements in |
|---|---|
| Architecture description (AD) | Clause 6 |
| Architecture description framework (ADF) | Clause 7.1 |
| Architecture description language (ADL) | Clause 7.2 |
| Architecture viewpoint | Clause 8.1 |
| Model kind | Clause 8.2 |

The standard states that **tailoring is neither required nor permitted** when a claim of
conformance is made. A document that claims to conform must meet the requirements as
written; it may not drop or weaken them. The guide reflects this: the conformance
checklist treats every required content item as mandatory.

## 1.6 Required content of a conforming AD — Clause 6

To claim conformance, an AD must address each of the following. This list is the spine of
the document-structure chapter ([`05-document-structure.md`](05-document-structure.md)) and
of the conformance checklist ([`../checklists/conformance-checklist.md`](../checklists/conformance-checklist.md)).

| Clause | Required content |
|---|---|
| 6.1 | **Architecture description identification and overview** — identify the AD and its EoI; record version, date, status, scope, authorship, and references. |
| 6.2 | **Identification of stakeholders** — the stakeholders whose concerns are architecturally significant. |
| 6.3 | **Identification of stakeholder perspectives** — the perspectives used to group concerns and organize viewpoints. *(New in 2022.)* |
| 6.4 | **Identification of concerns** — the concerns held to be fundamental, each associated with the stakeholders that hold it. |
| 6.5 | **Identification of aspects** — the aspects of the entity's character used to structure concerns. *(New in 2022.)* |
| 6.6 | **Inclusion of architecture viewpoints** — each viewpoint used; every identified concern is framed by at least one viewpoint. |
| 6.7 | **Inclusion of architecture views** — the view(s) governed by each viewpoint; each view adheres to its governing viewpoint. |
| 6.8 | **Inclusion of view components** — each governed by its model kind or documented by a legend. |
| 6.9 | **Recording of architecture correspondences** — 6.9.1 known inconsistencies among AD elements; 6.9.2 correspondences; 6.9.3 correspondence methods. |
| 6.10 | **Recording of architecture decisions and rationale** — 6.10.1 decisions; 6.10.2 rationale. |

> **A note on completeness.** The exact normative "shall" wording of Clauses 6–8 is in the
> purchased standard. The *list of required items* above is faithful to the standard's
> structure; the short descriptions are this guide's paraphrase. Where an AD must quote a
> requirement as normative, quote the standard, not this guide.

## 1.7 How the standard writes — and why this guide imitates it

The register of 42010:2022 is itself a model for AD prose. The guide adopts it
deliberately so that documents sound continuous with the standard they conform to:

- **Normative force is carried only by verbal forms.** *Shall* states a requirement;
  *should* states a recommendation; *may* states a permission; *can* states possibility.
  Nothing else carries obligation.
- **The register is impersonal and precise.** The standard states facts and requirements
  about artifacts. It does not address the reader as "you," does not speak as "we," and
  does not exhort.
- **Normative and informative text are separated.** Requirements live in normative
  clauses; explanation, history, and examples live in informative annexes and notes.
- **Definitions follow a fixed form.** Each is a noun phrase in genus–differentia form,
  with no leading article and no terminal period, e.g. *architecture viewpoint* = "set of
  conventions for the creation, interpretation and use of an architecture view to frame one
  or more concerns."

The next chapter turns this register into the single voice every document under the guide
must share.
