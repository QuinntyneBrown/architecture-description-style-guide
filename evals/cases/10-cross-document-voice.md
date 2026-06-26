# Case 10 — Cross-document single voice

**Mode:** Review · **Primary dimension:** Voice consistency (across documents)

Tests the guide's defining property at the set level: do two ADs from the same entity read
as one author's work? Each document is locally clean; the faults appear only in comparison.

## Input — two excerpts from the same authoring entity

**Document A — Payment Platform AD, §7.1**

> The settlement view is governed by the settlement viewpoint (VP-SET). The Settlement
> service records each matched trade and emits a settlement event. Cf. ISO/IEC/IEEE
> 42010:2022, 6.7.

**Document B — Reporting Platform AD, §1 overview**

> This architecture description sets out the design of our next-generation reporting
> platform, a powerful and flexible solution. The settlement engine feeds the reporting
> pipeline. See 42010 §6.1 for the conformance basis.

## Expected findings (review verdict scheme)

| Dimension | Finding |
|---|---|
| Vocabulary (cross-doc) | **Term drift:** the same component is "the **Settlement service**" in A and "the **settlement engine**" in B. One concept, one word — pick one and use it in both. |
| Voice | **Register drift:** B's overview is **promotional** ("next-generation … powerful and flexible solution") and uses **first person** ("our"), where A is impersonal and factual. B must be brought to A's register. |
| Structure | **Citation style differs:** A writes "ISO/IEC/IEEE 42010:2022, 6.7"; B writes "42010 §6.1". One citation form across the set. |

Document A alone passes the prose checklist; Document B alone trips `AD-VOICE-001` ("our")
and `AD-REG-001` ("powerful"). The **cross-document** findings — term drift and citation-style
drift — are visible only when the two are compared, which is the point of this case.

## Verdict

Per [`../../checklists/review-checklist.md`](../../checklists/review-checklist.md):
**inconsistent.** The set fails the single-entity test (review-checklist §E and §F). To
reach **consistent with fixes**: unify the component name, rewrite B's overview to A's
impersonal register and remove "our," and unify the citation style.

## Notes

This case is scored with the review verdict scheme, not rule-id recall, because the faults
are relational. An agent that reviews each document in isolation and reports "both fine" (or
only catches B's local issues) misses the cross-document drift and fails the dimension.
