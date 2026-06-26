# Conformance Checklist — Required Content (Clause 6)

A document-level check that an AD addresses every required content item of ISO/IEC/IEEE
42010:2022, Clause 6, and satisfies the cross-section coverage obligations. Use it before
an AD claims conformance. Rule identifiers refer to
[`../resources/data/style-rules.yaml`](../resources/data/style-rules.yaml).

> **Conformance is all-or-nothing.** The standard permits no tailoring of its requirements
> when a conformance claim is made. A document that omits a required item does not conform;
> a focused document that is not a full AD must say so and state which items it does not
> address. `AD-CONF-001`

---

## A. Required content present *(each item is mandatory for a conforming AD)*

- [ ] **6.1 Identification and overview** — AD title, EoI identified, version, date,
  status, authoring entity, scope, references.
- [ ] **6.2 Stakeholders** — identified as roles/classes, each with an interest in the EoI.
- [ ] **6.3 Stakeholder perspectives** — identified and related to the concerns they group.
  *(New in 2022; commonly omitted — check explicitly.)*
- [ ] **6.4 Concerns** — identified, each associated with the stakeholders that hold it.
- [ ] **6.5 Aspects** — identified and related to concerns. *(New in 2022; commonly
  omitted.)*
- [ ] **6.6 Architecture viewpoints** — each viewpoint included, with the concerns it frames
  and the stakeholders holding them.
- [ ] **6.7 Architecture views** — the view(s) governed by each viewpoint included; each
  adheres to its governing viewpoint.
- [ ] **6.8 View components** — included, each governed by a model kind or documented by a
  legend.
- [ ] **6.9.1 Known inconsistencies** — recorded, or explicitly stated as none known.
- [ ] **6.9.2 Correspondences** — relationships among AD elements recorded.
- [ ] **6.9.3 Correspondence methods** — the methods governing the correspondences stated.
- [ ] **6.10.1 Architecture decisions** — recorded with identifiers and affected elements.
- [ ] **6.10.2 Architecture rationale** — recorded for every decision.

## B. Cross-section coverage obligations *(structure must conform, not merely contain)*

- [ ] **Every concern is held by ≥1 identified stakeholder.** (§4 ↔ §2)
- [ ] **Every concern is framed by ≥1 viewpoint.** No unframed concern. `AD-CONF-002`
- [ ] **Every viewpoint frames ≥1 identified concern.** No orphan viewpoints. (§6 ↔ §4)
- [ ] **Every view is governed by exactly one viewpoint.** `AD-CONF-004`
- [ ] **Every view component is governed by a model kind or documented by a legend.**
  `AD-CONF-005`
- [ ] **Every architecture decision has recorded rationale.** `AD-CONF-003`
- [ ] **Known inconsistencies are recorded, not silently omitted.** `AD-CONF-006`
- [ ] **No deprecated terms anywhere in the document.** `AD-VOC-001`

## C. Conformance claim itself

- [ ] **The conformance claim names the standard and edition** — "Conforms to ISO/IEC/IEEE
  42010:2022, Clause 6."
- [ ] **No requirement has been tailored, dropped, or weakened.**
- [ ] **If the document is not a full AD**, it states which conformance target it addresses
  (AD / ADF / ADL / viewpoint / model kind) and which required items it does and does not
  cover.

## D. Other conformance targets *(only if the document specifies them)*

- [ ] **Architecture viewpoint (8.1)** — specifies framed concerns, holding stakeholders,
  model kinds/conventions, operations on views, and governed views. (See
  [`../resources/templates/viewpoint-template.md`](../resources/templates/viewpoint-template.md).)
- [ ] **Model kind (8.2)** — specifies the modelling conventions, constructs, and
  well-formedness rules.
- [ ] **ADF (7.1)** / **ADL (7.2)** — specifies the framework's / language's required
  elements per its clause.

---

### Reporting

Report as a conformance table: each Clause-6 item marked **present / partial / absent**,
with the location or the gap. A single **absent** required item, or any failed coverage
obligation in §B, is a non-conformance.
