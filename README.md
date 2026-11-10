# product-thinking

A Claude Code plugin for people who aren't engineers. It takes someone with an idea (an account manager, a salesperson, a PM, a "vibe coder") and walks them Socratically from *"I want to build a thing"* to a build-ready plan, **without ever asking them a "left or right" technical question.**

AI coding tools don't stop and ask *why*. The person using them usually already has the answers in their head (who it's for, how many, whether the data persists); nothing pulls them out. This skill does, then turns those answers into the inputs an engineer needs, so the technical call gets made *for* the author, with the reason attached.

## Install

Claude Code:

```
/plugin marketplace add robertmnyborg/claude-harness
/plugin install product-thinking@claude-harness
```

Codex, Cursor, and other agents that read `SKILL.md`, via the [skills CLI](https://skills.sh):

```bash
npx skills add robertmnyborg/product-thinking
```

This repo is also its own marketplace: `/plugin marketplace add robertmnyborg/product-thinking`, then `/plugin install product-thinking@product-thinking`.

## Use it

Three ways in:

1. **Just describe your idea.** Say *"I have an idea for a tool that…"*, *"help me plan a tool"*, or *"I want to automate this process I do manually"* and the skill fires on its own. This is the main path.
2. **Type a command** (four aliases, all the same skill): `/product-thinking:help-me-build`, `:help-me-think`, `:i-have-an-idea`, `:plan-my-idea`.
3. **Pass the idea inline:** `/product-thinking:help-me-build "a tool that emails me weekly churn"`.

## How it fits

```
                    ┌─ engineering lane ─→  Engineering Handoff Inputs  →  scaffold or spec  →  build
product-thinking ──┤                          (tier · data · compute · tenancy · scale ceiling ·
   (this)          │                           ops limits · sensitivity · integrations · shared-asset ledger · owner)
                    └─ self-serve lane ──→  Build Sheet  →  the author builds & operates it themselves
                                              (ideal-state steps · approval gates · access checklist · shared-asset ledger ·
                                               run once → schedule → babysit → unattended)
```

If your engineering team has written standards (which database, which compute, which stack), the skill defers to them. It does not invent architecture rules.

## What it figures out (scaled to the tier)

One question at a time, only what matters for *your* project. A spike answers a handful; a production, customer-facing system answers all of these before engineering starts:

- **Why / outcome**: what it's for, checked back against the build.
- **Demand check**: what people do today and what it costs them, how strong the evidence of need is, one named person, the smallest demo that gets a yes, and "has anyone used it without your help?" Adapted from the forcing questions in [gstack](https://github.com/garrytan/gstack) `/office-hours`.
- **Build, borrow, or buy**: what already does this (tools you already pay for, paid products, open source), why build instead of use, whether it's part of how you win, and who keeps it running. Borrow or buy ends the session with an Adoption note. Adapted from [Tenex's build-vs-buy guide](https://tenex.co/build-vs-buy).
- **Scope**: who uses it, how many, what data, does it persist, how fresh.
- **Right-sizing**: traffic estimated bottom-up (*units × adoption × frequency*), and a **scale ceiling** so the build serves your real number of users (e.g. ~50), not a hypothetical million.
- **Operational limits**: upload caps, data retention, delete-on-request, notifications, and cost guardrails (alert vs. block).
- **Production readiness**: data sensitivity, roles (who can view/edit/delete), what it connects to, an **operational owner**, and what's out of scope for v1.
- **Shared-asset ledger**: what the tool *consumes* (is it a copy of a system of record?) and what it *produces* that someone else would read. Candidates only; it starts the reuse conversation with an engineer and never designs the API.

## Three gates: lane, tier, and depth

- **Lane = who builds and operates it.** **Self-serve** means an internal automation the author builds and runs with Claude (they're the operator, it's internal, access is an API key, failure is cheap, irreversible steps get a human approval). Self-serve skips the engineering process and ends with a **Build Sheet**: current vs. ideal steps, approval gates, access checklist, one supervised run, then a schedule and a 1–2 week babysit window. Everything else is the **engineering lane**.
- **Tier = build rigor** (`spike` / `app` / `production`): keys off scale, durability, and how load-bearing it is.
- **Depth = planning rigor.** **Depth A** (a short Product Brief) for anything with no revenue number to defend: most internal tools. **Depth B** (the full Goal Brief: outcome → thesis → milestone → metrics) only when a real business number is on the line.

## Posture

Counter-argue, never veto. Back off when the answer holds up. One question at a time. Surface and test the hidden assumption (the AI's default scale vs. your real, usually smaller, scale). It's the philosopher for the team, not the Grumpy Old Man.

## License

MIT
