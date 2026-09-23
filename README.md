# sipa-vultr-agent-rush-prep

**Vultr: Agent Rush Hackathon entry — prep stage.**

Built for [Vultr: Agent Rush](https://lablab.ai/ai-hackathons/vultr-hackathon)
— a hybrid hackathon with an online build phase and a live on-site day in
Salt Lake City, UT for approved participants (travel/accommodation not
covered).

## Status: requirements are real now (as of 2026-09-23)

The TBA period is over. The challenge, prize pool, technical requirements
and submission rules are all published. Full plan: see the [prep plan
artifact](https://claude.ai/artifact/QJ2w7wasRhtSatddgpioDS).

Confirmed live:
- **Online build: 2026-11-03 to 2026-11-08**
- **On-site phase: 2026-11-08**, Salt Lake City, UT (selected participants only, travel/accommodation not covered)
- **Prize pool: $9,000 cash + $5,000 in Vultr credits** (1st $5,000+$3,000cr / 2nd $3,000+$1,000cr / 3rd $1,000+$1,000cr)
- **$200 free Vultr credits per participant** (coupon code still TBA)
- Main challenge: **"Blast Radius Zero: Safe Agent Execution on Vultr"** — a web-based agent that performs real work (code execution or browser automation) with every action contained in a sandbox running on Vultr

## Mandatory technical anchors

- **Vultr VM backend** — required, Vultr is the central control/orchestration layer, not just hosting
- **Vultr Serverless Inference** — required for all agent LLM calls, OpenAI-compatible at `https://api.vultrinference.com/v1`
- **Sandbox boundary** — required, container or throwaway instance, never inside the app process (Docker recommended; OpenSandbox/gVisor/E2B cited as starting points)
- Vultr API (spin up + destroy a throwaway instance per task) — optional

## The angle

Picks up exactly where this README's prior version predicted: the
Vultr-sandboxing angle pairs with `sipa-gpu-guard`'s usage/budget/gate
pattern, adapted from AMD ROCm to Vultr's API — plus `sipa-trace` logging
every sandboxed action as a hash-chained audit card. The hackathon's own
"containment-first" framing (an agent that only chats is a demo; an agent
that executes safely is a product) is the same thesis this team applies
everywhere else, just pointed at Vultr's sandbox primitives instead of a
generic one.

One explicit submission requirement worth flagging here since it's easy to
miss mid-build: the demo video must show **"one containment moment"** — the
sandbox actually absorbing something unsafe (an `rm -rf`, an infinite loop,
a hostile web page). This has to be staged/captured deliberately, not left
to chance.

## Team

Aelin AquaSoul — team **SIPA_OS** (`sipaos`) on lablab.ai. Benjamin
(`BenjaminJKHong`) confirmed on the team 2026-09-17, added as a
collaborator on this repo.

## License

Apache 2.0
