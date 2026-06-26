<!--
  Architecture viewpoint specification — conforming to ISO/IEC/IEEE 42010:2022, Clause 8.1.
  A viewpoint is reusable CONVENTIONS that frame one or more concerns and govern one or
  more views. Specify it so it could itself claim conformance.
  Write in the guide's single voice; delete italic "Guidance:" notes before publishing.
-->

# Architecture viewpoint — <VIEWPOINT NAME> (VP-<ID>)

## Overview
The <name> viewpoint establishes the conventions for the creation, interpretation, and use
of <name> views. It frames the concerns identified below and governs the views listed in
§Governed views.

## Concerns framed
*Guidance: a viewpoint frames one or more concerns. List them; a viewpoint that frames no
identified concern is an orphan and shall be removed or repurposed.*

| Concern | Statement |
|---|---|
| C-<id> | <the matter of interest this viewpoint frames> |

## Stakeholders
The stakeholders holding the framed concerns:

| Stakeholder | Concern(s) |
|---|---|
| SH-<id> | C-<id> |

## Model kinds
*Guidance: state each model kind this viewpoint defines, with its modelling conventions. A
model-based view component built under this viewpoint is governed by one of these model
kinds.*

| Model kind | Conventions / notation | Governs view components of type |
|---|---|---|
| <name> | <metamodel, notation, well-formedness rules> | <...> |

## Conventions for non-model-based components
*Guidance: where a view component is not model-based, state the legend conventions used to
document it.*

## Operations on views
*Guidance: state the methods that apply to views governed by this viewpoint — analysis
methods, consistency checks, and the correspondence methods used to relate this view's
elements to others.*

| Operation | Purpose |
|---|---|
| <analysis/consistency/correspondence method> | <what it establishes or checks> |

## Governed views
*Guidance: a viewpoint governs one or more views (a 2022 change from the 2011 one-to-one
rule). List the views in the AD that this viewpoint governs.*

| View | In AD section |
|---|---|
| V-<id> <name> | §7.<n> |

## Source
<If this viewpoint is adopted or adapted from an ADF or a published viewpoint catalogue,
identify the source. Otherwise: "Defined for this entity of interest.">
