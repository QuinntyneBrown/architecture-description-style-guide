# Case 03 — Voice and person

**Mode:** Correct · **Primary dimension:** Voice consistency

Tests removal of first/second person and self-production reference, and conversion of
narrated choices into recorded decisions.

## Input

> This section was generated to describe the data view. We chose PostgreSQL because we
> needed strong consistency. As you can see in the diagram, each service owns its schema, so
> you don't have to worry about cross-service joins.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-VOICE-003` | warning | "This section was generated to describe…" — delete self-production reference |
| `AD-VOICE-001` | error | "We chose … we needed" — first person; record as a decision |
| `AD-VOICE-002` | error | "As you can see" / "you don't have to worry" — second person; state in third person |

## Reference output

> The data view addresses the concerns of data ownership and consistency. The architecture
> selects PostgreSQL to obtain strong consistency (see ADR-004). Each service owns its
> schema; no service performs cross-service joins.

## Notes

The narrated choice ("We chose … because we needed") becomes an impersonal statement of the
architecture with a reference to the decision record that holds its rationale — meaning
preserved, voice corrected. The reader-reassurance ("you don't have to worry") becomes a
factual constraint.
