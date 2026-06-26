# Evals

A suite for measuring how well an agent applies this guide — to **check**, **correct**, and
**author** architecture description prose. The cases are deliberately small and targeted so a
failure points at one rule or one dimension.

---

## Layout

```
evals/
├── README.md     this file
├── rubric.md     how to score (five dimensions + rewrite axes)
├── cases.yaml    machine-readable index: every case with its scoring key
└── cases/        one Markdown file per case (input, expected findings, reference output)
```

Each case has two halves that must agree:

- An entry in [`cases.yaml`](cases.yaml) — the **scoring key**: case id, mode, the
  `expected_findings` (rule ids the agent must raise), and, for correction/authoring cases, a
  pointer to the reference output. A harness reads this.
- A file in [`cases/`](cases/) — the **human-readable case**: the input prose (or authoring
  brief), the expected findings with explanation, and the reference correction where one
  exists. A reviewer reads this.

## How to run a case

1. Give the agent the case **input** and the relevant **mode** (Check / Correct / Author),
   with the guide loaded per [`../agents/AGENT-INSTRUCTIONS.md`](../agents/AGENT-INSTRUCTIONS.md).
   Do **not** show it the expected findings.
2. Capture the agent's findings (and rewritten text, for Correct/Author).
3. Score against the key in `cases.yaml` using [`rubric.md`](rubric.md): compute
   recall/precision per dimension, judge any rewrite, and assign the per-case verdict.
4. Aggregate across the suite; watch error-severity recall most closely.

## What the suite covers

| Case | Mode | Primary dimension exercised |
|---|---|---|
| `01-deprecated-terms` | Check/Correct | Vocabulary fidelity |
| `02-normative-force` | Check/Correct | Normative correctness |
| `03-voice-person` | Check/Correct | Voice consistency |
| `04-view-vs-viewpoint` | Check | Vocabulary fidelity |
| `05-register-hype` | Check/Correct | Expression & register |
| `06-agentless-passive` | Check/Correct | Expression & structure |
| `07-conformance-gaps` | Check | Conformance content |
| `08-clean-passes` | Check | False-positive control (all dimensions) |
| `09-author-section` | Author | All dimensions + rewrite axes |
| `10-cross-document-voice` | Review | Voice consistency (across documents) |

`08-clean-passes` is the control: the input conforms, and the correct number of findings is
**zero**. An agent that raises findings on it is over-triggering and loses precision across
the suite.

## Extending the suite

Add a case by writing both halves: a `cases/NN-name.md` file and a matching `cases.yaml`
entry. Keep each case focused on one fault family so the score is diagnostic. When a real
document exposes a fault the suite does not cover, distil it into a new case. If a case
reveals that **no rule catches a real fault**, fix the guide (`style-rules.yaml` /
`substitutions.yaml` / a prose chapter) first, then add the case.
