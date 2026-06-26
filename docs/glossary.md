# Glossary — Canonical Terms

The controlled vocabulary of the guide: the nineteen terms defined in Clause 3 of
ISO/IEC/IEEE 42010:2022, followed by the related concepts that are *not* defined terms and
the deprecated words they replace.

**How to read each entry.** The definition is given in the standard's genus–differentia
form — a noun phrase, no leading article, no terminal period. `[verbatim]` marks wording
quoted from the standard; `[paraphrase]` marks this guide's wording. Usage notes are this
guide's, not the standard's. The machine-readable form of this glossary is
[`../resources/data/terminology.yaml`](../resources/data/terminology.yaml); the two must
agree.

> When a document under this guide uses one of these terms, it carries the meaning given
> here and no other. Do not narrow, broaden, or substitute a synonym.

---

## The nineteen defined terms (Clause 3)

### architecting *(3.1)*
> conceiving, defining, expressing, documenting, communicating, certifying proper
> implementation of, maintaining and improving an architecture throughout the life cycle of
> an entity of interest — `[verbatim]`

**Use it for** the *activity*, not its work products. The work product is an
*architecture description*; the activity that produces and sustains it is *architecting*.

### architecture *(3.2)*
> fundamental concepts or properties of an entity in its environment and governing
> principles for the realization and evolution of this entity and its related life cycle
> processes — `[verbatim; SOURCE: 42020:2019, 3.3, modified]`

**Use it for** the intangible subject. An architecture is *expressed by* an AD; it is never
itself a document. Do not write "the architecture document" — write "the architecture
description" or "the AD."

### architecture description *(3.3)* — **AD**
> work product used to express an architecture — `[verbatim]`

**Use it for** the tangible deliverable this guide governs. Introduce the abbreviation
*(AD)* on first use, then use *AD*. An AD is an *information part*.

### architecture description element *(3.4)* — **AD element**
> identified or named part of an architecture description — `[verbatim]`

**Use it for** any named constituent of an AD: stakeholders, concerns, stakeholder
perspectives, aspects, viewpoints, views, view components, model kinds, correspondences,
correspondence methods, ADLs, and ADFs. An AD may be treated as an AD element within
another AD (this supports correspondences across alternative descriptions).

### architecture description framework *(3.5)* — **ADF**
> conventions, principles and practices for the description of architectures established
> within a specific domain of application or community of stakeholders — `[verbatim]`

**Use it for** a domain framework such as RM-ODP, UAF, NAF, or GERAM. **Replaces the
deprecated term "architecture framework."** An ADF typically supplies predefined
viewpoints, perspectives, aspects, and model kinds.

### architecture description language *(3.6)* — **ADL**
> means of expression, with syntax and semantics, consisting of a set of representations,
> conventions, and associated rules intended to be used to describe an architecture —
> `[verbatim]`

**Use it for** a description language such as AADL, ArchiMate, UML, SysML, or the UAF
Profile. An ADL may define one or more model kinds and/or viewpoints.

### architecture view *(3.7)*
> information part comprising portion of an architecture description — `[verbatim]`

**Use it for** the part of an AD that addresses the concerns its governing viewpoint
frames. A view *adheres to* exactly one governing viewpoint and *comprises* view
components. Distinguish *view* (the result) from *viewpoint* (the conventions); see the
usage note under **architecture viewpoint**.

### architecture viewpoint *(3.8)*
> set of conventions for the creation, interpretation and use of an architecture view to
> frame one or more concerns — `[verbatim]`

**Use it for** the conventions, not the result. To *frame* concerns means "to shape,
compose, give expression to" them — stating the problem, as opposed to *addressing* it in a
view. A viewpoint *frames* one or more concerns and *governs* one or more views. The
recurring error is to swap *view* and *viewpoint*: a viewpoint is reusable conventions; a
view is the applied result in a specific AD.

### aspect *(3.9)*
> part of an entity's character or nature — `[verbatim]`

**Use it for** a facet of the entity such as its functional, structural, or informational
character. Aspects and concerns relate many-to-many. *(Newly defined in 2022.)* Prefer
*aspect* alone; "architecture aspect" is informal.

### concern *(3.10)*
> matter of relevance or importance to a stakeholder — `[verbatim; SOURCE: 42020:2019,
> 3.8, notes modified]`

**Use it for** an interest held by a stakeholder — for example performance, security,
modifiability, cost, or regulatory compliance. A concern is *held by* one or more
stakeholders and is *framed by* one or more viewpoints. Every concern identified in an AD
must be framed by at least one viewpoint.

### correspondence *(3.11)*
> identified or named relationship between two or more architecture description elements —
> `[verbatim]`

**Use it for** a recorded relationship among AD elements — equivalence, composition,
refinement, consistency, traceability, dependency, constraint, satisfaction, or
obligation. A correspondence *relates* two or more AD elements and is *governed by* a
correspondence method.

### entity of interest *(3.12)* — **EoI**
> subject of an architecture description — `[verbatim]`

**Use it for** the thing the AD describes — an enterprise, organization, solution, system,
subsystem, process, product, service, software or hardware item, product line, family of
systems, or system of systems. **Replaces the deprecated term "system of interest."** Use
*entity of interest* when speaking generically; name the specific entity (e.g. "the payment
platform") once it has been identified.

### environment *(3.13)*
> context of surrounding things, conditions, or influences upon an entity — `[verbatim]`

**Use it for** the setting in which the EoI exists — its operational, business,
developmental, technical, and regulatory surroundings.

### information part *(3.14)*
> separately identifiable body of information that is produced, stored, and delivered for
> human and machine use — `[verbatim]`

**Use it for** an identifiable unit of recorded information. An AD and each architecture
view are information parts. *(Newly defined in 2022.)*

### model kind *(3.15)*
> category of model distinguished by its key characteristics and modelling conventions —
> `[verbatim]`

**Use it for** a category such as a functional, activity, structural, use-case,
geopolitical, analytic, or economic model kind. A model kind *governs* model-based view
components. Note: only *model kind* is defined — speak of a *view component governed by a
model kind*, not of "a model" as a stand-alone AD element.

### specification *(3.16)*
> information part that identifies, in a complete, precise and verifiable manner, the
> requirements, design, behaviour, or other expected characteristics of an entity —
> `[verbatim; SOURCE: 15289:2019, 3.1.26, modified]`

**Use it for** a complete, precise, verifiable information part. Reserve the word for this
sense; do not use "specification" loosely to mean any document. *(Newly defined in 2022.)*

### stakeholder *(3.17)*
> role, position, individual, organization, or classes thereof, having an interest, right,
> share, or claim, in an entity of interest — `[verbatim]`

**Use it for** any holder of a concern in the EoI. Identify stakeholders as roles or
classes (e.g. "operators," "the certification authority") rather than named persons, unless
a named individual is genuinely the stakeholder. A stakeholder *holds* one or more
concerns.

### stakeholder perspective *(3.18)*
> way of thinking about an entity of interest, especially as it relates to concerns —
> `[verbatim]`

**Use it for** a grouping of concerns that organizes the viewpoints of an AD. *(Newly
defined in 2022.)* Distinguish *stakeholder perspective* (a way of thinking that groups
concerns) from *architecture viewpoint* (conventions that frame concerns in a view).

### view component *(3.19)* — **architecture view component**
> separable portion of one or more architecture views that is governed by the applicable
> model kind or legend — `[verbatim]`

**Use it for** a separable part of a view. A model-based view component is *governed by* a
model kind; a non-model-based view component is *documented by* a legend (an informal
documentation of conventions). **Replaces the deprecated term "architecture model."**

---

## Related concepts that are *not* Clause-3 terms

Use these as ordinary concepts. Do not treat them as controlled vocabulary, and do not
imply they carry a Clause-3 definition.

### architecture decision
A choice made during architecting that affects one or more AD elements and pertains to one
or more concerns. **Required content** of an AD (Clause 6.10.1), and a concept in the
model, but **not a Clause-3 defined term**. Record decisions explicitly; do not bury them
in narrative.

### architecture rationale
The justification for an architecture decision — the reasoning, alternatives considered,
and basis for the choice. **Required content** (Clause 6.10.2), **not a Clause-3 defined
term**. Pair every recorded decision with its rationale.

### correspondence method
The mechanism that governs correspondences (Clause 6.9.3). **Replaces the deprecated term
"correspondence rule."** Not a Clause-3 defined term, but the correct 2022 word.

### legend
An informal documentation of the conventions of a non-model-based view component. Not a
Clause-3 defined term; used in the definition of *view component* (3.19).

### system
An *example* of an entity of interest, not a defined term. Use *entity of interest* for
the generic subject of an AD; use *system* only when the EoI is in fact a system and you
have established that.

### model
Not a defined term. Only *model kind* is defined. Avoid "model" as a free-standing noun for
an AD element; prefer *view component* (the part) governed by a *model kind* (the
category).

---

## Deprecated terms — never use in a document under this guide

| ❌ Deprecated (pre-2022 / wrong) | ✅ Use instead | Defined at |
|---|---|---|
| system of interest | entity of interest (EoI) | 3.12 |
| architecture framework | architecture description framework (ADF) | 3.5 |
| architecture model | view component | 3.19 |
| correspondence rule | correspondence method | 6.9.3 |
| architecture document, architecture doc | architecture description (AD) | 3.3 |
| viewpoint (when a *view* is meant), or *view* (when a *viewpoint* is meant) | the correct one of architecture view (3.7) / architecture viewpoint (3.8) | 3.7, 3.8 |

These substitutions are enforced mechanically by
[`../resources/data/substitutions.yaml`](../resources/data/substitutions.yaml).
