# 04 — Expression

Vocabulary decides *which words*; voice decides *who speaks*. This chapter decides *how
sentences are built* — the constructions that make AD prose precise, scannable, and
uniform from one author to the next. The rules here are mechanical enough that most can be
checked by an agent against [`../resources/data/style-rules.yaml`](../resources/data/style-rules.yaml).

---

## 4.1 Sentences

**Assert one thing per sentence.** An AD sentence states a fact, a requirement, a
recommendation, or a permission — one of these, clearly.

- **Lead with the subject that acts.** Put the AD element or EoI part first, then what it
  does. ✅ "The gateway authenticates every inbound request." ❌ "Authentication of every
  inbound request is performed by the gateway."
- **Keep sentences short and declarative.** If a sentence runs past about 30 words or
  contains more than one *and*-joined clause carrying obligation, split it. One *shall* per
  sentence.
- **State the requirement, then its scope or condition** — not the reverse buried in
  subordinate clauses. ✅ "Each service shall expose health on `/healthz`." ✅ "When the
  primary is unreachable, the client shall fail over to the replica."
- **Prefer the positive form.** Say what shall happen, not what shall not, unless the
  prohibition is the point. ✅ "Access shall be denied unless the token is valid." (a
  genuine prohibition) over a tangle of double negatives.
- **Avoid agentless passive.** Passive voice hides which element acts; in an AD that is a
  defect, because the acting element is architecturally significant. Name the actor.

## 4.2 Normative statements

Normative force is carried only by the verbal forms (see
[`02-voice-and-register.md`](02-voice-and-register.md) §2.4). At the sentence level:

- **One verbal form per normative sentence.** Do not mix "shall" and "should" in a single
  clause.
- **Put the verbal form on the responsible subject.** ✅ "The scheduler shall retry a
  failed job at most three times." The subject that bears the obligation is explicit.
- **Do not dilute.** Forbidden: *shall ideally, should always, must absolutely, is required
  to try to*. A requirement is *shall*; a recommendation is *should*; nothing in between.
- **Express prohibition with "shall not."** Not "must never," "cannot ever," or "is
  forbidden from."
- **Reserve "can" and "will" for fact, not obligation.** "The cache can hold 10⁶ entries"
  states capacity; it is not a requirement.

## 4.3 Definitions

When an AD defines an EoI-local term, follow the standard's definitional form so that local
definitions sit continuously with the standard's own.

- **Genus–differentia, noun phrase, no leading article, no terminal period.**
  ✅ *settlement window* — interval during which matched trades are cleared and recorded
  ❌ *A settlement window is the interval during which trades get cleared.*
- **Define the term, do not describe around it.** State what it *is*, in its category, with
  what distinguishes it.
- **Do not define a term by example alone.** Examples may follow the definition, marked as
  examples; they do not replace it.
- **Define once, at first use or in the glossary**, then use the term unchanged.

## 4.4 Lists

Lists are heavily used in ADs — for stakeholders, concerns, requirements, decisions. Make
them parallel and consistent.

- **Make every item grammatically parallel.** All noun phrases, or all *shall* clauses, or
  all imperative-free declaratives — not a mixture.
- **Use a lead-in that the items complete grammatically.** ✅ "Each service shall:" followed
  by items each beginning with a verb ("expose…", "log…", "emit…").
- **Choose ordered vs. unordered deliberately.** Numbered lists imply sequence or
  precedence; bulleted lists imply none. Do not number a set with no order.
- **Keep one item to one idea.** If an item contains a buried second requirement, split it.
- **Punctuate consistently** within a document: either every item ends with no terminal
  punctuation (for short phrases) or every full-sentence item ends with a period. Do not
  mix.

## 4.5 Cross-references and traceability

ADs are dense webs of references — concerns to viewpoints, views to viewpoints, decisions
to the elements they affect, correspondences among elements. Reference precisely.

- **Reference AD elements by their identifier and name**, not by position. ✅ "the security
  viewpoint (VP-SEC)" ❌ "the viewpoint described above."
- **Cite the standard consistently**: *42010:2022, 6.6* — one form throughout a document
  set.
- **Record relationships as correspondences where the standard expects them**, rather than
  asserting them only in prose. A traceability claim between two AD elements is a
  correspondence (3.11), governed by a correspondence method (6.9.3).
- **Reference decisions by record.** Tie rationale and affected elements to an architecture
  decision record (e.g. "ADR-007"), not to "the decision we discussed."

## 4.6 Numbers, units, and quantities

- **State quantities; do not gesture at them.** ✅ "retains events for 90 days" ❌ "retains
  events for a while."
- **Use SI units and explicit units of measure**, with a space between number and unit
  ("200 ms", "10 GB"). Be consistent in unit choice across a document set.
- **Spell out a number that opens a sentence**; use numerals otherwise. Prefer rewriting so
  the sentence does not open with a large number.
- **Give ranges and bounds explicitly** for capacities and limits ("between 100 and 500
  concurrent sessions"; "at most three retries").

## 4.7 Tense, mood, and agreement (sentence level)

- **Present tense for what the architecture is**; future (*shall/will*) for what is required
  or planned; past only to record a decision already taken.
- **Declarative mood for the AD.** The imperative mood belongs to *this guide* and to
  procedural instructions, not to an architecture description.
- **Subject–verb agreement with the real subject**, not an intervening noun. ✅ "The set of
  services scales independently." (subject: *set*) — or rewrite for clarity.

## 4.8 Diagrams, captions, and legends

Text and figures must agree, and figures must be self-describing.

- **Every figure has a number and a caption**; the caption names what the figure shows in
  the same terms the prose uses. Reference figures by number, not "the figure below."
- **A non-model-based view component is documented by a legend** (3.19); supply it. A
  model-based view component states the model kind that governs it.
- **The prose introduces and interprets every figure.** A figure never carries
  architecturally significant content that the text does not also state — a reader (or
  agent) checking requirements reads the text.
- **Caption phrasing is uniform** across a document set: one pattern, e.g. "Figure N —
  *[view name]*: *[what it shows]*."

## 4.9 Markup and formatting (for documents authored in Markdown)

- **Headings follow the Clause-6 structure** (see [`05-document-structure.md`](05-document-structure.md)),
  in the same order and wording across the document set.
- **Use code formatting for identifiers, paths, endpoints, and field names** (`/healthz`,
  `order_id`), not for emphasis.
- **Do not use bold or italics to carry normative force** — that is the job of *shall*,
  *should*, *may*. Emphasis is for the occasional defined term on first mention, nothing
  load-bearing.
- **Tables for structured correspondences** — stakeholder-to-concern, concern-to-viewpoint,
  decision-to-affected-element — render the relationships the model expects, and read
  consistently across documents.

## 4.10 A sentence-level before/after

> ❌ It's very important that all of the various services are able to leverage the message
> bus in order to communicate asynchronously, and authentication is performed before
> requests are processed, which is obviously critical for security.

Three faults: vague intensifiers and hype (*very important, various, leverage, obviously
critical*); buried and unattributed obligation; agentless passive (*authentication is
performed*).

> ✅ Each service communicates asynchronously over the message bus. The gateway shall
> authenticate every request before any service processes it. *Concern addressed:* security
> (C-04), framed by the security viewpoint (VP-SEC).

The requirement is now a single *shall* on a named actor; the fact is stated plainly; and
the security concern is tied to its identifier and viewpoint rather than asserted with
emphasis.
