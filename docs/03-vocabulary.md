# 03 — Vocabulary

This chapter governs *word choice*: which terms to use for the concepts of architecture
description, how to render and abbreviate them, and which words to avoid. The definitions
themselves are in [`glossary.md`](glossary.md); this chapter is about *usage*. The
machine-readable backing is [`../resources/data/terminology.yaml`](../resources/data/terminology.yaml)
and [`../resources/data/substitutions.yaml`](../resources/data/substitutions.yaml).

The governing principle: **one concept, one word.** Each defined concept of 42010:2022 has
exactly one correct term. Do not vary it for elegance, do not coin synonyms, and do not use
a broader everyday word where a defined term is meant.

---

## 3.1 Use the defined term for the defined concept

When you mean one of the nineteen concepts, use its term and no other.

- ❌ The blueprint lays out the major building blocks of the platform.
- ✅ The architecture description identifies the principal components of the platform.

"Blueprint," "layout," "design doc," and "spec" are not the concept. If you mean the
*architecture description*, write *architecture description* (or *AD*). If you mean a
*view*, write *architecture view*. Reserve *specification* for its defined sense (3.16) — a
complete, precise, verifiable information part.

## 3.2 Never use a deprecated term

The 2022 edition renamed four concepts. The old words are wrong now, not merely
old-fashioned. Replace them on sight.

| ❌ Never write | ✅ Always write |
|---|---|
| system of interest | entity of interest (EoI) |
| architecture framework | architecture description framework (ADF) |
| architecture model | view component |
| correspondence rule | correspondence method |

These are enforced as **errors** in `substitutions.yaml`. A document containing any of them
does not pass the prose checklist.

## 3.3 Keep *view* and *viewpoint* distinct

This is the most common vocabulary error in architecture prose, and it breaks the
conceptual model. Hold the distinction:

- A **viewpoint** is *conventions* — reusable, defined once, framing concerns. It is the
  lens.
- A **view** is the *result* — the part of a specific AD produced by applying a viewpoint,
  addressing the concerns the viewpoint frames. It is what is seen through the lens.

Test before writing: *Could this be reused in another AD?* If yes, it is a **viewpoint**. *Is
this specific to this entity and this description?* If yes, it is a **view**.

- ❌ The security view defines the conventions for modelling trust boundaries.
  *(Conventions ⇒ that is a viewpoint.)*
- ✅ The security viewpoint defines the conventions for modelling trust boundaries; the
  security view applies them to the entity of interest.

## 3.4 Distinguish neighbouring terms

| Do not confuse… | …with | Distinction |
|---|---|---|
| concern | requirement | A concern is a *matter of interest* to a stakeholder; a requirement is a *shall* the architecture must satisfy. A concern motivates requirements; it is not one. |
| stakeholder | user / actor | A stakeholder *holds a concern* in the EoI. A user is one kind of stakeholder; not every stakeholder is a user. |
| stakeholder perspective | architecture viewpoint | A perspective is a *way of thinking that groups concerns*; a viewpoint is *conventions that frame concerns in a view*. |
| aspect | concern | An aspect is *part of the entity's character* (functional, structural…); a concern is a stakeholder's *matter of interest*. They relate many-to-many. |
| view component | model kind | A view component is a *part of a view*; a model kind is the *category that governs* a model-based view component. |
| correspondence | correspondence method | A correspondence is the *relationship*; the correspondence method is what *governs* it. |
| architecting | architecture description | Architecting is the *activity*; the AD is its *work product*. |

## 3.5 Rendering and casing

- **Write defined terms in lowercase** in running text, as the standard does: *architecture
  viewpoint*, *entity of interest*, *view component*. Do not capitalize them as proper
  nouns ("the Viewpoint," "our Stakeholders") and do not set them in title case mid-
  sentence.
- **Capitalize only at the start of a sentence or in a heading**, following ordinary
  sentence rules.
- **Capitalize the abbreviations** as the standard does: *AD, ADF, ADL, EoI*. Render *AD
  element* with a capital *AD* and lowercase *element*.
- **Names of specific AD elements** — a particular viewpoint, view, or EoI-local component —
  take a capital when they are proper names you have introduced ("the Settlement
  service"), but the *kind* word stays lowercase ("the Settlement service is a view
  component governed by the structural model kind").

## 3.6 Abbreviations

- **Expand on first use, then abbreviate.** "architecture description (AD)" → "AD". Do this
  once per document, at first occurrence.
- **Use the standard's abbreviations** for standard concepts: AD, ADF, ADL, EoI. Do not
  invent alternatives ("arch. desc.", "A/D").
- **For EoI-local abbreviations**, introduce each the same way and keep one expansion point
  per document.
- **Do not abbreviate** *architecture view*, *architecture viewpoint*, *concern*,
  *stakeholder*, *aspect*, *model kind*, or *view component* — the standard gives them no
  abbreviation, and short forms ("VP," "SH") read as a different writer.

## 3.7 Plurals, articles, and grammatical forms

- The defined terms take ordinary English plurals: *viewpoints, views, view components,
  concerns, stakeholders, correspondences, model kinds*. *Aspect* → *aspects*. *Entity of
  interest* → *entities of interest*.
- Use the article naturally: *an architecture viewpoint*, *the entity of interest*. (In the
  glossary, definitions drop the leading article by ISO convention; in running prose, use
  articles normally.)
- Prefer the noun forms the standard defines over invented verbs. The standard gives the
  verb *to frame* (a viewpoint frames concerns) and *to govern* (a viewpoint governs views;
  a model kind governs view components). Use *adhere to* for a view's relation to its
  viewpoint, *hold* for a stakeholder's relation to a concern, and *relate* for a
  correspondence. Do not invent "viewpointing," "to concern" as a verb, or "to stakeholder."

## 3.8 Words to prefer, words to drop

A short list of substitutions that keep the register plain and consistent. The full set is
in [`../resources/data/substitutions.yaml`](../resources/data/substitutions.yaml).

| ❌ Drop | ✅ Prefer |
|---|---|
| leverage, utilize | use |
| enable (vague), facilitate | allow, let, support — or a concrete verb |
| in order to | to |
| a number of, several (when countable) | the actual count or range |
| robust, powerful, seamless, scalable (as adjective-only claim) | the property and the evidence for it ("handles N concurrent sessions") |
| utilize a methodology to | (rewrite plainly) |
| due to the fact that | because |
| at this point in time | now, or delete |

## 3.9 EoI-local vocabulary

The guide controls the vocabulary of *architecture description*. The vocabulary of the
*entity* — service names, domain terms, component names — is local to each project. Govern
it with the same discipline:

- **Name each EoI-local term once and use it unchanged.** If the component is "the
  Settlement service," it is never also "the settlement engine," "the settler," or "the
  payments service."
- **Record EoI-local terms in a per-document or per-project glossary.** Identify each on
  first use.
- **Do not let an EoI-local term collide with a defined term.** Do not name a component
  "the View" or "the Concern." If a domain word clashes with a 42010 term, qualify the
  domain word.

The principle is the same at both levels: one concept, one word, used the same way every
time, so the whole body of documents reads as one entity's work.
