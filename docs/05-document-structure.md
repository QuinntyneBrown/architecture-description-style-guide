# 05 — Document Structure

This chapter turns the required content of Clause 6 into a concrete document layout. An AD
authored to this structure addresses every required content item in a fixed order, so that
any two ADs from the same entity present the same things in the same places. The template
that realizes this layout is
[`../resources/templates/architecture-description-template.md`](../resources/templates/architecture-description-template.md);
the conformance check that audits it is
[`../checklists/conformance-checklist.md`](../checklists/conformance-checklist.md).

Structure serves consistency as much as conformance: a reader who knows where *decisions*
live in one AD finds them in the same place in every AD.

---

## 5.1 The canonical section order

Each section maps to a Clause-6 required content item (see
[`01-foundations.md`](01-foundations.md) §1.6). Use these headings, in this order, with this
wording, across the document set.

| § | Heading | Clause | Purpose |
|---|---|---|---|
| 1 | Architecture description identification and overview | 6.1 | Identify the AD and its EoI; record metadata, scope, and references. |
| 2 | Stakeholders | 6.2 | Identify the stakeholders whose concerns are architecturally significant. |
| 3 | Stakeholder perspectives | 6.3 | Identify the perspectives that group concerns and organize viewpoints. |
| 4 | Concerns | 6.4 | Identify the fundamental concerns; associate each with its stakeholders. |
| 5 | Aspects | 6.5 | Identify the aspects of the entity's character used to structure concerns. |
| 6 | Architecture viewpoints | 6.6 | Include each viewpoint used; show every concern is framed. |
| 7 | Architecture views | 6.7 | Include the view(s) governed by each viewpoint. |
| 8 | View components | 6.8 | Include each view component, governed by a model kind or documented by a legend. |
| 9 | Correspondences | 6.9 | Record known inconsistencies, correspondences, and correspondence methods. |
| 10 | Architecture decisions and rationale | 6.10 | Record decisions and their rationale. |

Annexes (informative) may follow: an EoI-local glossary, the viewpoint specifications in
full, and the architecture decision records.

## 5.2 What each section contains

### 1 — Identification and overview (6.1)
Identify the AD: title, version, date, status, and the authoring entity. Identify the
**entity of interest** and state the scope and purpose of the description. List the
references, including this guide and any ADF or ADL in use. Keep the overview factual; it
is not an executive pitch.

### 2 — Stakeholders (6.2)
Identify stakeholders as **roles or classes** (operators, the certification authority,
downstream integrators), each with an identifier (e.g. `SH-01`). State what gives each its
interest in the EoI. Do not list named individuals unless an individual is genuinely the
stakeholder.

### 3 — Stakeholder perspectives (6.3)
Identify the perspectives used to group concerns and organize the viewpoints — for example
an operational perspective, a developmental perspective, a regulatory perspective. Relate
each perspective to the concerns it groups. *(New required content in 2022; do not omit
it.)*

### 4 — Concerns (6.4)
Identify each fundamental concern with an identifier (e.g. `C-04 — availability`) and a
one-line statement. Associate each concern with the stakeholders that hold it (a
many-to-many table is the natural form). Every concern listed here must be framed by at
least one viewpoint in §6.

### 5 — Aspects (6.5)
Identify the aspects of the entity's character used to structure the concerns — functional,
structural, informational, behavioural, and so on. Relate aspects to concerns
(many-to-many). *(New required content in 2022.)*

### 6 — Architecture viewpoints (6.6)
For each viewpoint, give its identifier and name, the concerns it **frames**, the
stakeholders those concerns belong to, and the model kinds or conventions it defines. Show,
by construction, that **every concern from §4 is framed by at least one viewpoint** — a
coverage table is the clearest form. Full viewpoint specifications may live in an annex
using [`../resources/templates/viewpoint-template.md`](../resources/templates/viewpoint-template.md).

### 7 — Architecture views (6.7)
For each view, name its **governing viewpoint** (exactly one), and address the concerns that
viewpoint frames. A view *adheres to* its viewpoint; if it cannot, record the deviation as
a known inconsistency in §9. One viewpoint may govern more than one view.

### 8 — View components (6.8)
Present the view components that make up each view. For each, state whether it is
**model-based** (and name the **model kind** that governs it) or **non-model-based** (and
supply its **legend**). Every figure that carries architecturally significant content is a
view component and is documented accordingly.

### 9 — Correspondences (6.9)
Three parts, in order:
- **9.1 Known inconsistencies (6.9.1)** — record the known inconsistencies and unresolved
  issues among AD elements. Silence is not conformance; if there are none known, say so.
- **9.2 Correspondences (6.9.2)** — record the relationships among AD elements
  (traceability, refinement, dependency, satisfaction, …), each as a named correspondence.
- **9.3 Correspondence methods (6.9.3)** — state the methods that govern the
  correspondences. Use *correspondence method*, never the deprecated "correspondence rule."

### 10 — Architecture decisions and rationale (6.10)
- **10.1 Decisions (6.10.1)** — record each architecture decision with an identifier (e.g.
  `ADR-007`), the choice made, and the AD elements and concerns it affects.
- **10.2 Rationale (6.10.2)** — for each decision, record the rationale: the alternatives
  considered, the basis for the choice, and the consequences accepted. Use the decision
  record template ([`../resources/templates/decision-record-template.md`](../resources/templates/decision-record-template.md)).

## 5.3 Coverage obligations the structure must satisfy

These are the cross-section invariants that make the document conform, not merely contain
sections. The conformance checklist verifies each.

- **Every concern is held by at least one identified stakeholder.** (§4 ↔ §2)
- **Every concern is framed by at least one viewpoint.** (§4 ↔ §6)
- **Every viewpoint frames at least one identified concern.** (no orphan viewpoints) (§6 ↔ §4)
- **Every view is governed by exactly one viewpoint.** (§7 ↔ §6)
- **Every view component is governed by a model kind or documented by a legend.** (§8)
- **Every architecture decision has recorded rationale.** (§10.1 ↔ §10.2)
- **Known inconsistencies are recorded, not omitted.** (§9.1)
- **Deprecated terms appear nowhere.** (the whole document)

## 5.4 Specifying a viewpoint or a model kind (Clauses 8.1, 8.2)

When the document set defines its own viewpoints or model kinds (rather than adopting an
ADF's), specify each so it could itself claim conformance:

- An **architecture viewpoint** specification (8.1) states: the concerns it frames; the
  stakeholders holding those concerns; the model kinds and conventions it defines for
  constructing and interpreting its views; and any operations on views (analysis methods,
  correspondence methods). Use
  [`../resources/templates/viewpoint-template.md`](../resources/templates/viewpoint-template.md).
- A **model kind** specification (8.2) states the conventions of the modelling: its
  metamodel or notation, its constructs, and the rules governing well-formed view
  components.

## 5.5 Scaling the structure down

Not every document is a full AD. A focused document — a single viewpoint specification, one
decision record, a description of one view — uses the relevant subset of this structure and
says so in §1. It does **not** invent a different structure. The rule is: the same headings
in the same order, present where applicable, omitted explicitly where not. A document that
claims to be a *conforming AD* includes all of §§1–10; a focused document states which
required items it does and does not address, so a reader is never misled about conformance.
