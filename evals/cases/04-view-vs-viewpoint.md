# Case 04 — View vs. viewpoint

**Mode:** Check · **Primary dimension:** Vocabulary fidelity

Tests the most common architecture-prose error: confusing the reusable *conventions*
(viewpoint) with the applied *result* (view).

## Input

> The security view defines the conventions for modelling trust boundaries and the model
> kinds used to express them. The deployment viewpoint shows that the payment platform runs
> three replicas of the gateway across two regions.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-VOC-002` | warning | "The security **view** defines the conventions … model kinds" — defining conventions is the work of a **viewpoint**, not a view. |
| `AD-VOC-002` | warning | "The deployment **viewpoint** shows that the payment platform runs three replicas…" — the applied, EoI-specific result is a **view**, not a viewpoint. |

## Reference (corrected, for reviewer reference)

> The security **viewpoint** defines the conventions for modelling trust boundaries and the
> model kinds used to express them. The deployment **view** shows that the payment platform
> runs three replicas of the gateway across two regions.

## Notes

Diagnostic test the agent should apply: *reusable conventions ⇒ viewpoint; specific applied
result ⇒ view.* This is a Check-mode case, so the agent reports findings; the corrected text
is shown only for the reviewer. No error-severity findings are expected — both are
warnings — so the case measures heuristic recall, not error recall.
