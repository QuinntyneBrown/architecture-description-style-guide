<!--
  Architecture Description (AD) template — conforming to ISO/IEC/IEEE 42010:2022, Clause 6.
  Replace every <PLACEHOLDER>. Keep the section headings, order, and wording.
  Write all prose in the guide's single voice (docs/02-voice-and-register.md):
  impersonal, declarative, third person; normative force only via shall/should/may.
  Italic "Guidance:" notes are instructions to the author — delete them before publishing.
  Identifiers shown (SH-, C-, A-, VP-, V-, VC-, COR-, ADR-) are conventions; keep them stable.
-->

# Architecture Description — <ENTITY OF INTEREST NAME>

## 1. Identification and overview *(6.1)*

| Field | Value |
|---|---|
| AD title | <TITLE> |
| Entity of interest (EoI) | <NAME AND ONE-LINE IDENTIFICATION> |
| Version | <X.Y> |
| Date | <YYYY-MM-DD> |
| Status | draft \| under review \| approved |
| Authoring entity | <ORGANIZATION / BODY> |
| Conformance | Conforms to ISO/IEC/IEEE 42010:2022, Clause 6. |

**Scope and purpose.** This architecture description (AD) expresses the architecture of
<EoI>. It addresses the concerns of the stakeholders identified in §2 and is intended for
<the stable audience>. <State what is in scope and what is out of scope.>

**References.** ISO/IEC/IEEE 42010:2022; this style guide; <any ADF or ADL in use>; <related
ADs>.

*Guidance: state facts only. This overview is not an executive pitch; no marketing
adjectives, no first person.*

## 2. Stakeholders *(6.2)*

| ID | Stakeholder (role/class) | Interest in the EoI |
|---|---|---|
| SH-01 | <role/class> | <what gives this stakeholder an interest, right, share, or claim> |
| SH-02 | <role/class> | <...> |

*Guidance: identify stakeholders as roles or classes, not named individuals, unless an
individual genuinely is the stakeholder.*

## 3. Stakeholder perspectives *(6.3)*

| ID | Perspective | Concerns it groups |
|---|---|---|
| P-01 | <e.g. operational> | C-…, C-… |
| P-02 | <e.g. regulatory> | C-… |

*Guidance: new required content in 2022. A perspective is a way of thinking that groups
concerns and organizes the viewpoints; it is not a viewpoint.*

## 4. Concerns *(6.4)*

| ID | Concern | Held by | Perspective | Statement |
|---|---|---|---|---|
| C-01 | <e.g. availability> | SH-01, SH-03 | P-01 | <one-line statement of the matter of interest> |
| C-02 | <...> | SH-02 | P-02 | <...> |

*Guidance: every concern listed here is framed by at least one viewpoint in §6.*

## 5. Aspects *(6.5)*

| ID | Aspect | Concerns it relates to |
|---|---|---|
| A-01 | <e.g. functional> | C-01, C-04 |
| A-02 | <e.g. informational> | C-02 |

*Guidance: new required content in 2022. Aspects are parts of the entity's character;
aspects and concerns relate many-to-many.*

## 6. Architecture viewpoints *(6.6)*

For each viewpoint, give its identifier and name, the concerns it frames, the stakeholders
holding those concerns, and the model kinds or conventions it defines. Full specifications
may appear in Annex B using the viewpoint template.

| ID | Viewpoint | Frames concerns | For stakeholders | Model kinds / conventions |
|---|---|---|---|---|
| VP-SEC | Security viewpoint | C-04, C-07 | SH-02, SH-05 | <model kinds> |
| VP-INFO | Information viewpoint | C-02 | SH-03 | <model kinds> |

**Concern coverage.** *Guidance: show every concern in §4 is framed by at least one
viewpoint.*

| Concern | Framed by |
|---|---|
| C-01 | VP-… |
| C-02 | VP-INFO |

## 7. Architecture views *(6.7)*

### 7.1 <View name> *(governed by VP-… )*

This view adheres to the <name> viewpoint and addresses the concerns that viewpoint frames
(<C-…>). <State the architecture as seen through this viewpoint, in declarative prose.>

*Guidance: each view names exactly one governing viewpoint. If the view cannot adhere to
its viewpoint, record the deviation as a known inconsistency in §9.1.*

### 7.2 <View name> *(governed by VP-… )*
<...>

## 8. View components *(6.8)*

| ID | View component | In view | Model-based? | Governed by model kind / legend |
|---|---|---|---|---|
| VC-01 | <name> | 7.1 | model-based | <model kind> |
| VC-02 | <name> | 7.2 | non-model-based | legend in Fig. N |

*Guidance: every architecturally significant figure is a view component and is documented
here — by its governing model kind or by a legend.*

## 9. Correspondences *(6.9)*

### 9.1 Known inconsistencies *(6.9.1)*
<List the known inconsistencies and unresolved issues among AD elements. If none are
known, state: "No inconsistencies among AD elements are known at this version.">

### 9.2 Correspondences *(6.9.2)*

| ID | Relates | Type | Governed by method |
|---|---|---|---|
| COR-01 | C-04 ↔ V-7.1 | satisfaction | M-01 |
| COR-02 | VC-01 ↔ VC-02 | dependency | M-01 |

### 9.3 Correspondence methods *(6.9.3)*

| ID | Method | Governs |
|---|---|---|
| M-01 | <how correspondences are established and checked> | COR-01, COR-02 |

*Guidance: use "correspondence method", never the deprecated "correspondence rule".*

## 10. Architecture decisions and rationale *(6.10)*

Recorded as decision records (see decision-record-template.md). Summary index:

| ID | Decision | Affects | Concerns | Rationale |
|---|---|---|---|---|
| ADR-001 | <the choice made> | VC-01, V-7.1 | C-04 | §B / record |
| ADR-002 | <...> | <...> | <...> | <...> |

*Guidance: every decision in §10 has recorded rationale (alternatives, basis,
consequences). No decision is left without rationale.*

---

## Annex A (informative) — EoI-local glossary
<Define each EoI-local term once, in genus–differentia form (noun phrase, no leading
article, no terminal period).>

## Annex B (informative) — Viewpoint specifications
<Full specifications of any viewpoints this AD defines, per viewpoint-template.md.>

## Annex C (informative) — Architecture decision records
<Full decision records, per decision-record-template.md.>
