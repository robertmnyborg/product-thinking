# Goal Brief template

Fill this through conversation, not as a form. Every section has a job; if you can't fill one honestly, that gap is the next thing to work, not a blank to leave.

Keep the writing plain: lead with the claim, state the bet plainly, no hedging.

---

**Owner:** <name + team>   ·   **Target:** <date>   ·   **Status:** Proposed | Committed | Done

## Demand note

- **Status quo + cost:** <what they do today, even badly; hours/week and who spends them>
- **Evidence rung:** <mentioned once | asked more than once | keeps a workaround running | would scramble if it vanished>
- **Named person:** <one person, what they lose without this, heard directly or relayed>
- **Build, borrow, or buy:** <verdict · options checked by name (tools you already pay for, paid, open source) · why each doesn't fit · owner who keeps it running>

## Why this matters

<2–4 sentences. State the bet behind the work as a belief, and tie it to a hard business outcome: name the dollar figure, the KPI, the segment. The reader should finish this paragraph knowing what breaks if this work doesn't happen.>

> <Optional: the single sharpest sentence of the whole brief, pulled out as a quote.>

The path to **<outcome, e.g. $2M incremental revenue>** runs through **<the mechanism>**.

## Our thesis

We're betting this chain holds. We're naming it now so we can check our assumptions against reality when this wins or fails:

1. <First link: a falsifiable belief about the world.>
2. <Second link: what becomes true because of (1).>
3. <Third link: ...down toward the outcome.>
4. <Final link: why this is a durable advantage / why it produces the outcome.>

<Each link must be something reality could break. If a link is "we build a good feature," it's not a thesis link, it's a task. Cut it.>

## The milestone

A **<one measurable milestone>** by **<date>**.

> Before you write this line: is it a **lever you control** or an **outcome you don't**? Win rate, revenue, and cycle time are outcomes: many things move them. The milestone must be the lever this work most directly drives (often your thesis's "leading signal"). If you wrote an outcome here, move it down to "Outcomes we watch" and put the lever here.

**Definition:** <Define the terms precisely. What exactly counts? What exactly doesn't?>

This is the right milestone for three reasons:

- **We can measure it directly:** <how we see it: the actual signal, not a proxy we hope correlates.>
- **It's the lever we most influence:** <what we control here, vs. what we don't.>
- **Everything else builds on it:** <what hitting this unlocks next.>

## What "<X>" has to mean

To avoid hitting the number without driving the value, the goal is defined tightly:

- **<Right unit>, not <gameable unit>.** <e.g. distinct sessions, not raw fetches.>
- **<In-scope subset> only.** <e.g. active pages only; exclude the things that can't produce value.>
- **Spread, not piled.** <Breadth requirement so the win isn't concentrated on a handful of items.>
- **Read off a clean baseline.** <Measured against one clean period, not a near-zero base that inflates the multiplier.>

## How we measure it

A small family of metrics, each catching a specific failure mode:

- **<Metric 1>:** <what it is>. **Goal: <target>.** <the failure it catches>
- **<Metric 2>:** <what it is>. **Target: <target>.** <the failure it catches>
- **<Metric 3, breadth>:** <what it is>. Catches the "all the value on a few items" failure.
- **<Metric 4, depth>:** <what it is>. Catches the "happened once, never again" failure.
- **Outcomes we watch (not targets):** <the downstream business signals that tell us the milestone is translating into real value.>

**Where:** <dashboard / source>, refreshed <cadence>, reviewed <cadence>.

## Where we focus to move it

- **<Lever 1 (precondition)>:** <the thing that has to be true first.> <evidence it's working / in progress.>
- **<Lever 2 (what gets used)>:** <the thing that drives the metric once the precondition holds.>

---

## Scope (for the engineering handoff; fills during Phases 3–4)

*Not part of the published Goal Brief. This is the bridge to the engineering plan.*

- **Users:** who / how many.
- **Data + sources:** what information, from where, persistence, freshness.
- **Load + reliability:** how often, how fast, how reliable.
- **Technical direction (decided, with reasons):** <the destination-based calls made FOR the author, each with its why, sourced from your team's standards where they exist.>
- **Open questions for engineering (the genuine left/right forks):** <named, not resolved; engineering owns these.>

## Engineering Handoff Inputs (always fill)

Each row is a product-language answer that engineering consumes as a decision-input. Fill every row; a blank row is a missing input to surface, not a gap to leave.

| Handoff Input | Value | Feeds |
|---|---|---|
| **Tier**: spike / app / production | <from Phase 0> | build rigor, scaffold choice |
| **Data workload**: writes app state / reads analytics / stores events | <from Phase 3> | database choice |
| **Compute shape**: request / scheduled job / long-running service / pipeline | <from Phase 3> | compute choice |
| **Tenancy**: personal / team / org / external | <from Phase 3> | auth scope, data isolation |
| **Durability + freshness** | <from Phase 3> | tier + database choice |
| **Scale ceiling (do not over-build)** | <real N, e.g. "~50 users, hundreds/week"> | right-sizing: build for this, not millions |
| **Operational limits & retention** | <upload cap+types / retention window / delete = soft or hard / rate & context limits / cost alert-vs-block / notifications> | storage, delete handling, validation, monitoring |
| **Data sensitivity & access** | <PII/customer/financial? + roles: who views/edits/deletes> | auth, access control, compliance |
| **Integrations / source of truth** | <existing systems it reads/writes; system of record> | integration design (often a fork) |
| **Shared-asset ledger**: consumes / produces, candidates only | <one row per asset: direction · kind (source of truth / capability / event) · system of record or named second consumer (or "none known") · exists today? · question for the engineer> | the engineer conversation on API/service shape; re-read before the next durable build in this domain |
| **Operational owner** | <who owns/operates post-launch; who's paged> | go-live readiness gate |
| **Scope contract**: timeline + user ceiling + phase ladder | <e.g. "2 weeks, 5–10 users; Phase 1 can't-do: manual user mgmt, no scale-out, no non-critical bug fixes, brief deploy downtime OK"> | the enforceable scope doc; what phase 2 graduates |
| **Decided direction + tradeoffs (with the why)** | <from Phase 4: the pick AND why not the bigger option> | carried into the build/spec |
| **Risk trade-offs for a stakeholder (decided or pending)** | <functionality-vs-risk calls only, each "A gives X, risks Y / B gives Z, costs W" + lean> | stakeholder decisions; implementation choices stay with the engineer |
| **Genuine engineering forks (unresolved)** | <marked, not resolved> | engineering discussion |

**Handoff (route by tier):** spike → build on your team's standard starting point. app (single-team internal tool) → build it, then harden it as it gets used; write a pitch-size spec the moment it needs anything from engineering. production / cross-team / customer-facing → an engineering spec (your org's process, or `spec-driven-development`), written by the engineer, carrying the why forward.

---

> **Depth A (tool/spike) note:** skip "Our thesis", "The milestone", "What X has to mean", "How we measure it", and "Where we focus". Those are Depth B. A Depth A artifact is just **Why this matters** (2–3 plain sentences) + **Scope** + the **Engineering Handoff Inputs** block. Don't make a five-person tool carry a revenue chain.
