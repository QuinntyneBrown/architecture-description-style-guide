# Case 08 — Clean text (false-positive control)

**Mode:** Check · **Primary dimension:** All (precision control)

The input conforms to the guide. The correct number of findings is **zero**. This case
measures the agent's precision: an agent that raises findings here is over-triggering.

## Input

> The availability view is governed by the availability viewpoint (VP-AVAIL), which frames
> the availability concern (C-01) held by the operators (SH-01). The entity of interest runs
> as an active-active deployment across two regions. The gateway routes each request to the
> nearest healthy region. When a region becomes unreachable, the gateway shall fail over to
> the remaining region within 30 s. Each region may serve read traffic independently;
> writes are serialized through the primary region. This trade-off is recorded in ADR-001,
> with rationale: active-active is adopted to meet C-01; the cost — higher write latency — is
> accepted. The deployment view comprises two view components, each governed by the
> structural model kind.

## Expected findings

**None.** `expected_finding_count: 0`.

## Why it passes

- Vocabulary: *view*, *viewpoint*, *concern*, *stakeholder*, *entity of interest*, *view
  component*, *model kind* all used correctly; no deprecated terms.
- Voice: third person throughout; no first/second person; the decision is recorded, not
  narrated.
- Normative force: *shall* for the failover requirement; *may* for the read-traffic
  permission; plain present tense for facts.
- Register: no hype, no fillers; the trade-off is stated plainly with its accepted cost.
- Expression: actors named (*the gateway*); failover quantified (30 s); decision referenced
  by identifier (ADR-001).

## Notes

The one near-miss is "writes are serialized through the primary region" — passive, but the
acting element (the primary region) is named in the same clause, so it is **not** an
`AD-EXP-001` violation. An agent that flags it has misread the rule (which targets
*agentless* passive). Flagging it costs precision.
