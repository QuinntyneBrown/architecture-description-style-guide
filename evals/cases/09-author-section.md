# Case 09 — Author a section from a brief

**Mode:** Author · **Primary dimension:** All + rewrite axes

Tests authoring conforming prose from raw facts, in the single voice, without fabricating
what the brief does not supply.

## Authoring brief (the input given to the agent)

Write the **Concerns (§4)** and **one viewpoint entry (§6)** of an AD for a telemetry
ingestion service ("the entity of interest"). Facts supplied:

- Stakeholders already identified: operators (SH-01), data scientists (SH-02), the data
  protection officer (SH-03).
- Concerns to record: ingest throughput (operators); query latency (data scientists);
  personal-data handling (data protection officer).
- One viewpoint to record: an information viewpoint that frames the personal-data handling
  concern, for the data protection officer. It defines a data-flow model kind.
- The throughput target and the retention period are **not yet decided**.

## Reference output (one acceptable form)

> **§4 Concerns**
>
> | ID | Concern | Held by | Statement |
> |---|---|---|---|
> | C-01 | ingest throughput | SH-01 | the rate at which the entity of interest accepts and durably records telemetry events. Target: `<TO SUPPLY: events/s>`. |
> | C-02 | query latency | SH-02 | the time from query submission to first result for analytical queries over ingested telemetry. |
> | C-03 | personal-data handling | SH-03 | the lawful collection, minimization, and retention of personal data within telemetry. Retention period: `<TO SUPPLY>`. |
>
> **§6 Architecture viewpoints (entry)**
>
> | ID | Viewpoint | Frames | For stakeholders | Model kinds |
> |---|---|---|---|---|
> | VP-INFO | information viewpoint | C-03 | SH-03 | data-flow model kind |
>
> The information viewpoint establishes the conventions for describing how personal data
> flows through, and is retained within, the entity of interest. It frames the personal-data
> handling concern (C-03) and defines a data-flow model kind that governs the view
> components of the information view.

## Scoring focus

- **Correctness preserved / no fabrication (cardinal):** the undecided throughput target and
  retention period are marked `<TO SUPPLY>` — **not** invented. Inventing a number fails the
  case.
- **Output conformance:** every concern is associated with a stakeholder; C-03 is framed by
  VP-INFO; the viewpoint frames an identified concern (no orphan).
- **Voice match:** impersonal, declarative, third person; defined terms used correctly;
  genus–differentia-style concern statements; no hype, no first/second person.

## Notes

There is no single correct wording; any output that records the supplied facts, frames C-03,
flags the two undecided values, and reads in the single voice passes. The trap is the two
missing facts — a fabricating agent will quietly fill in "1,000,000 events/s" or "90 days."
