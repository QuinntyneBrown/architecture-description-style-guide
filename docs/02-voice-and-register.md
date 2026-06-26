# 02 — Voice and Register

The purpose of this chapter is the purpose of the whole guide: that every architecture
description produced under it reads as though **one entity wrote it for one audience**. A
reader should not be able to tell, from voice alone, that two ADs were written by different
people, with different tools, in different years. This chapter defines that single voice.

Vocabulary (chapter 3) makes documents use the *same words*. This chapter makes them *sound
the same* — same speaker, same listener, same bearing.

---

## 2.1 The speaker: one impersonal entity

An AD is spoken by **the description itself**, as an institutional work product — not by a
named author, not by a team, and not by a software tool. The speaker is impersonal,
authoritative, and consistent. It is the same speaker as the standard the AD conforms to.

Three rules fix the speaker.

1. **No first person.** Do not write *we*, *our*, *I*, or *the team*. The AD does not have a
   personality; it has authority.
   - ❌ We chose an event-driven design because we wanted loose coupling.
   - ✅ The architecture adopts an event-driven design to achieve loose coupling between
     services. *(The decision and its rationale are recorded, not narrated.)*

2. **No second person.** Do not address the reader as *you*. State facts about the EoI and
   its description, not instructions to a reader.
   - ❌ You can see in the deployment view that each service runs in its own container.
   - ✅ In the deployment view, each service runs in its own container.

3. **No tool or process self-reference.** The AD does not mention how it was produced, what
   generated it, or what it "will now describe."
   - ❌ This section was generated to describe the data view.
   - ✅ The data view addresses the concerns of data stewardship and retention.

The single exception is a recorded **architecture decision and rationale** (Clause 6.10),
where the *deciding body* may be named as a matter of record — "The architecture board
selected option B." Even there, prefer the impersonal record over narration of feelings or
preferences.

## 2.2 The audience: one informed, non-specialist stakeholder

Write for a single, stable reader: a **stakeholder who is professionally literate but not
assumed to be a specialist in the entity of interest**. This reader can follow technical
prose, knows the vocabulary of architecture description, and needs to locate concerns,
decisions, and rationale quickly — but should not be required to already know the system to
understand the document.

This fixes the level of explanation:

- **Define what is local, assume what is standard.** Assume the reader knows what an
  *architecture viewpoint* is (it is defined by the standard); do not assume the reader
  knows what *the settlement engine* is (it is local to this EoI) — identify it on first
  use.
- **Expand every abbreviation on first use**, then use the short form: "architecture
  description (AD)", thereafter "AD". This applies to both standard abbreviations and
  EoI-local ones.
- **Do not write to two audiences at once.** Do not mix an executive summary's register
  into a structural view, or drop to a tutorial register mid-document. One reader, one
  level, throughout.
- **Never condescend and never mystify.** No "simply," no "obviously," no "of course"; and
  no unexplained jargon used to impress. The reader is a peer.

## 2.3 The register: declarative, present, precise

The register is the constant texture of the prose. Hold it steady across every section and
every document.

| Dimension | The single setting | Example |
|---|---|---|
| **Mood** | Declarative. State what is, what shall be, what is recommended. Imperative is for *this guide*, not for an AD. | ✅ "Each service exposes a versioned API." ❌ "Expose a versioned API for each service." |
| **Tense** | Present, for what the architecture *is*. Use future (*shall*/*will*) only for what is required or planned; past only to record a decision already made. | ✅ "The gateway authenticates every request." |
| **Person** | Third person throughout. The subject is the EoI, an AD element, or the architecture. | ✅ "The architecture separates command and query responsibilities." |
| **Voice** | Active where a real actor exists in the architecture; otherwise a plain declarative subject. Avoid agentless passive that hides *which element acts*. | ✅ "The scheduler assigns each job to a worker." ❌ "Each job is assigned." *(by what?)* |
| **Stance** | Neutral and factual. The AD asserts; it does not sell, hedge, or apologize. | ✅ "The design accepts higher write latency to guarantee durability." |
| **Distance** | Impersonal. No rhetorical questions, no direct address, no exhortation. | — |

## 2.4 Normative force lives only in verbal forms

This is the register's load-bearing rule, inherited directly from the standard. **The
degree of obligation in a statement is carried only by its verbal form** — never by tone,
emphasis, or adjectives.

| Verbal form | Meaning | Use for |
|---|---|---|
| **shall** | requirement | a constraint the architecture or its realization must satisfy |
| **should** | recommendation | a preferred choice that may be departed from with reason |
| **may** | permission | an option that is allowed |
| **can** | possibility or capability | what is possible, not what is required |
| **will** | a statement of fact about the future | planned or expected behaviour, with no obligation |

Consequences for the writer:

- **Do not use "must," "need to," "have to," or "is required to"** to express a
  requirement. Use **shall**. One word carries requirement, everywhere, so that a reader
  (or an agent) can find every requirement by finding every *shall*.
- **Do not strengthen prose with emphasis to imply obligation.** "It is *critical* that the
  cache be invalidated" is not a requirement. "The cache shall be invalidated on write" is.
- **Do not weaken a requirement into a hope.** If it is required, write *shall*. If it is
  not, do not pretend with "should ideally" or "must try to."

## 2.5 The words that erode a single voice

The following habits make a document sound like a different writer from one paragraph to
the next. The guide forbids them outright. They are enforced as warnings in
[`../resources/data/style-rules.yaml`](../resources/data/style-rules.yaml).

- **Filler intensifiers** — *very, really, quite, extremely, highly, significantly* (as a
  vague booster), *robust, powerful, seamless, cutting-edge, world-class, best-in-class,
  state-of-the-art*. They assert quality without stating a fact.
- **Marketing and hype** — *leverage* (use *use*), *utilize* (use *use*), *enable* (when
  *allow* or a concrete verb is meant), *facilitate, synergy, holistic, next-generation*.
- **Hedges that dodge commitment** — *arguably, basically, essentially, sort of, kind of, in
  some sense, more or less, it could be argued.* An AD commits; it does not muse.
- **Conversational connectives** — *so,* *well,* *now,* *actually,* *of course,* at the
  start of a sentence; rhetorical questions.
- **Vague quantifiers** — *several, many, a number of, some, various* where a count, range,
  or "each/all/none" is meant and knowable.
- **Empty openers** — *It should be noted that, It is important to understand that, As we
  can see, In order to* (use *to*). Delete them; state the fact.

## 2.6 What a single voice looks like — a worked contrast

The same content, first written so that voice drifts and obligation is unclear, then
written in the guide's single voice.

> ❌ **Drifting voice.** We decided to go with a microservices approach since it's a really
> robust, industry-standard pattern that you'll find scales well. It should be noted that
> services need to talk over HTTP. Basically each one has its own database, which is
> obviously important for decoupling. The system of interest leverages an API gateway.

> ✅ **Single voice.** The architecture decomposes the entity of interest into independently
> deployable services. Each service owns its data store; no service accesses another's
> store directly. Services shall communicate over HTTP. An API gateway mediates all
> external requests. *Rationale:* independent data ownership is adopted to decouple the
> services' release cycles; the cost — eventual consistency across stores — is accepted (see
> ADR-007).

Note what changed: *we decided* became a recorded architecture and an ADR reference; the
deprecated *system of interest* became *entity of interest*; *leverages* became *mediates*;
the unclear "need to" became a *shall*; the intensifiers, hedges, and empty opener were
deleted; the reader is no longer addressed; and the decision is paired with its rationale.

## 2.7 Consistency across a set of documents

Single voice is not only a within-document property. A *set* of ADs from the same entity
must agree on the choices the standard leaves open. Fix these once, in a project's local
profile, and apply them everywhere:

- **Term casing and abbreviation** — pick one rendering of each EoI-local term and one
  expansion point for each abbreviation, and keep it across documents.
- **Heading scheme** — the same section names and order, drawn from the Clause-6 structure
  in [`05-document-structure.md`](05-document-structure.md).
- **Decision-record format** — one template for every architecture decision (see
  [`../resources/templates/decision-record-template.md`](../resources/templates/decision-record-template.md)).
- **Reference style** — one way of citing the standard, viewpoints, and other ADs.
- **Diagram captions and legends** — one phrasing pattern for captions and one convention
  for legends.

The review checklist ([`../checklists/review-checklist.md`](../checklists/review-checklist.md))
includes a cross-document pass for exactly these.
