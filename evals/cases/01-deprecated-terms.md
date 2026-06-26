# Case 01 — Deprecated 42010 terms

**Mode:** Correct · **Primary dimension:** Vocabulary fidelity

Tests whether the agent detects and replaces every deprecated 2011 term with its 2022
equivalent.

## Input

> The architecture framework adopted for the system of interest defines three viewpoints.
> Each architecture model in the deployment view is governed by a structural model kind.
> Consistency between elements is maintained by a correspondence rule recorded in §9.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-VOC-001` | error | "architecture framework" → architecture description framework (ADF) |
| `AD-VOC-001` | error | "system of interest" → entity of interest (EoI) |
| `AD-VOC-001` | error | "architecture model" → view component |
| `AD-VOC-001` | error | "correspondence rule" → correspondence method |

All four are error-severity; missing any one fails the case (error recall < 1.0).

## Reference output

> The architecture description framework (ADF) adopted for the entity of interest (EoI)
> defines three viewpoints. Each view component in the deployment view is governed by a
> structural model kind. Consistency between elements is maintained by a correspondence
> method recorded in §9.

## Notes

No architecture facts change — only vocabulary. An agent that rewrites the meaning, or that
"corrects" the legitimate terms *viewpoints*, *deployment view*, *structural model kind*,
loses precision.
