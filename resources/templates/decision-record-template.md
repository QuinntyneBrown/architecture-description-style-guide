<!--
  Architecture decision record — satisfies ISO/IEC/IEEE 42010:2022, Clause 6.10
  (6.10.1 decision, 6.10.2 rationale). One record per decision.
  Write in the guide's single voice: impersonal, declarative, third person.
  The deciding body MAY be named as a matter of record; do not narrate preferences.
  Delete italic "Guidance:" notes before publishing.
-->

# ADR-<NNN> — <SHORT DECISION TITLE>

| Field | Value |
|---|---|
| Status | proposed \| accepted \| superseded by ADR-<NNN> \| deprecated |
| Date | <YYYY-MM-DD> |
| Deciding body | <architecture board / role> |
| Affects (AD elements) | <VC-…, V-…, VP-…> |
| Concerns | <C-…> |

## Decision *(6.10.1)*
The architecture <states the choice as a fact>. *Guidance: one decision per record, stated
declaratively. Use 'shall' where the decision imposes a requirement on the realization.*

## Context
<The situation that required a decision: the framed concerns, constraints, and forces in
play. State facts about the EoI and its environment; no first person.>

## Alternatives considered *(part of 6.10.2 rationale)*

| Option | Summary | Why not selected |
|---|---|---|
| A | <...> | <...> |
| B *(selected)* | <...> | — |
| C | <...> | <...> |

## Rationale *(6.10.2)*
The selected option is adopted because <the basis for the choice, tied to the framed
concerns>. <State the reasoning factually.>

## Consequences
<The consequences accepted, positive and negative. State trade-offs plainly: "The design
accepts <cost> to obtain <benefit>." Record new concerns or inconsistencies the decision
introduces.>

## Correspondences
*Guidance: record the relationships this decision creates or relies on as correspondences
(6.9.2), governed by a correspondence method (6.9.3).*

| Relates | Type |
|---|---|
| ADR-<NNN> ↔ C-<id> | satisfaction |
| ADR-<NNN> ↔ VC-<id> | constraint |
