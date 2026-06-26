# Case 02 — Normative force

**Mode:** Correct · **Primary dimension:** Normative correctness

Tests whether the agent reserves obligation for *shall/should/may* and refuses
emphasis-as-requirement.

## Input

> The gateway must authenticate every request. Services need to emit a heartbeat every 10 s.
> The cache shall ideally be invalidated on write. It is critical that audit logs are
> retained, and they may be exported on demand.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-NORM-001` | error | "must authenticate" → "shall authenticate" |
| `AD-NORM-001` | error | "need to emit" → "shall emit" (it is a requirement) |
| `AD-NORM-002` | error | "shall ideally be invalidated" → recommendation: "should be invalidated" |
| `AD-NORM-003` | warning | "It is critical that … retained" — emphasis is not obligation; if required, "shall be retained" |

The trailing "may be exported on demand" is **correct** (a permission); flagging it is a
false positive.

## Reference output

> The gateway shall authenticate every request. Services shall emit a heartbeat every 10 s.
> The cache should be invalidated on write. Audit logs shall be retained; they may be
> exported on demand.

## Notes

The agent must decide, per clause, whether the obligation is a requirement (*shall*) or a
recommendation (*should*). "shall ideally" is the trap: an obligation diluted by an adverb is
a recommendation, so the fix is *should*, not *shall*.
