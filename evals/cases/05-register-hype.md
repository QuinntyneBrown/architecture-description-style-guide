# Case 05 — Register, hype, and fillers

**Mode:** Correct · **Primary dimension:** Expression & register

Tests removal of marketing adjectives, vague intensifiers, empty openers, and hype verbs,
without losing the underlying facts.

## Input

> It should be noted that the platform is a robust, world-class, seamless solution that
> leverages a really powerful event bus. The architecture utilizes a number of services that
> obviously scale very well.

## Expected findings

| Rule | Severity | Finding |
|---|---|---|
| `AD-REG-003` | warning | "It should be noted that" — empty opener; delete |
| `AD-REG-001` | warning | "robust, world-class, seamless … powerful" — quality claims with no fact |
| `AD-REG-004` | info | "leverages / utilizes" → "uses" |
| `AD-REG-005` | info | "a number of services" — give the count if knowable |
| `AD-REG-002` | warning | "really … obviously … very well" — intensifiers/fillers |

## Reference output

> The platform uses an event bus for asynchronous communication. The architecture comprises
> <N> services, each independently deployable. *(Capacity and scaling limits stated with
> figures where known; the hype claims are removed because no fact supported them.)*

## Notes

The reference deliberately shows that some content **disappears**: "robust, world-class,
seamless, powerful, scales very well" asserted quality without evidence, so the correct fix
is to state the actual property and its measure or to remove the claim — not to find a
fancier synonym. If a real number is unknown, the agent marks `<N>` / `<TO SUPPLY>` rather
than inventing one.
