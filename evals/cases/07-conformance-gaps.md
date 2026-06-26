# Case 07 — Conformance gaps

**Mode:** Check · **Primary dimension:** Conformance content

Tests detection of missing Clause-6 content and failed coverage obligations. The input is an
AD outline (abbreviated) that claims conformance.

## Input

> **Architecture Description — Payment Platform** *(claims conformance to 42010:2022)*
>
> **§1 Identification and overview.** Title, EoI, v1.0, approved.
> **§2 Stakeholders.** SH-01 operators, SH-02 compliance officer.
> **§3 Concerns.** C-01 availability (SH-01); C-04 auditability (SH-02); C-05 privacy (SH-02).
> **§4 Architecture viewpoints.** VP-AVAIL frames C-01; VP-AUDIT frames C-04.
> **§5 Architecture views.** Availability view (VP-AVAIL); audit view (VP-AUDIT).
> **§6 View components.** Listed, each with a model kind.
> **§7 Architecture decisions.** ADR-001 (active-active, rationale given); ADR-002 (chose
> Kafka).
>
> *(No further sections.)*

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-CONF-001` | error | Missing required content: **stakeholder perspectives (6.3)**, **aspects (6.5)**, and **correspondences (6.9)** including known inconsistencies and methods. |
| `AD-CONF-002` | error | **C-05 (privacy)** is identified but framed by **no viewpoint** — no VP frames it. |
| `AD-CONF-003` | error | **ADR-002** records a decision ("chose Kafka") with **no rationale**. |
| `AD-CONF-006` | warning | No statement of **known inconsistencies (6.9.1)** — silence is not conformance. |

## Notes

This is the conformance dimension's core case. The agent must cross-check sections, not just
read them in isolation: C-05 appears in §3 but in no viewpoint in §4 (`AD-CONF-002`); §6.3,
6.5, and 6.9 are simply absent (`AD-CONF-001`); ADR-002 has a decision but no rationale
(`AD-CONF-003`). Because the document **claims conformance**, every one of these is blocking
except the known-inconsistencies warning. An agent that reports "looks complete" fails the
case outright.
