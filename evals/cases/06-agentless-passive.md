# Case 06 — Agentless passive and imprecise reference

**Mode:** Correct · **Primary dimension:** Expression & structure

Tests naming the acting AD element (active voice), referencing by identifier, and
quantifying limits.

## Input

> Requests are authenticated before being routed. As shown in the diagram above, messages
> are retried until they succeed. The queue is configured for high throughput.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-EXP-001` | warning | "Requests are authenticated … messages are retried" — agentless passive; name the element that acts |
| `AD-EXP-005` | warning | "the diagram above" — reference by identifier and name, not position |
| `AD-EXP-006` | info | "configured for high throughput" — quantify the throughput |

## Reference output

> The gateway authenticates each request before routing it. As shown in Figure 4 (the
> deployment view), the broker retries a failed message up to three times before moving it to
> the dead-letter queue. The queue sustains up to `<N>` messages per second. *(Replace `<N>`
> with the measured limit; do not invent one.)*

## Notes

The point of the active-voice rule in an AD is that *which element acts* is architecturally
significant. "Requests are authenticated" hides whether the gateway, a sidecar, or each
service authenticates — the reader cannot verify the security concern. The retry count and
throughput are unbounded gestures in the input; the agent quantifies what is known and flags
what is not.
