# Agiterra

Agiterra LLC builds developer tools and SaaS products. This GitHub org hosts our public, open-source work — primarily the **Agiterra Multi-Agent Toolkit**.

## Agiterra Multi-Agent Toolkit

**An open framework for running AI engineering teams.**

Small, composable, generic — the Unix philosophy, applied to AI agents. Each tool does one thing well and stands on its own; together they combine into a coordinated, persistent team. Every piece is AI-vendor-agnostic (Claude Code, Codex, or your own runtime), and each capability has been tuned over six months of development and daily dogfooding.

Three primitives carry most of the weight:

- **Wire** — the nervous system. Real-time, signed messaging between agents (and you) across processes, machines, even locations, with a live dashboard of who's doing what.
- **Crew** — launch agents in persistent terminal sessions that survive a closed laptop, a killed terminal, even a reboot. Steer them, arrange them, supervise them like a team.
- **Knowledge** — a memory vault each agent owns: dual semantic + keyword search that auto-injects relevant context on *every* prompt, survives context compaction, and remembers *why* it believes what it believes.

**Bridge** sits on top: the orchestrator's plugin. It collapses the multi-step dance of spawning and managing an agent into single composite calls — composition made literal. It stays domain-naive; capability-specific behavior (GitHub, Linear, …) ships as separate `bridge-X` plugins anyone can write.

**Your agents are portable.** A *personai* — a persistent agent, like an engineer or a reviewer — lives in its own git repo: its identity, its accumulated knowledge, and its spawn scripts. Clone it on any machine, run one script, and it boots with everything it has ever learned, ready to point at any codebase. Your senior engineer, wherever you need them, remembering everything.

## Who is this for?

- **Operators** running long-lived AI engineers across days or weeks of work
- **Builders** experimenting with multi-agent systems
- **Teams** who want their agents to communicate, remember, and recover

Whether you have one agent or twenty, the Toolkit meets you where you are. Use one tool, use them all — they compose, they don't lock you in.

## Where to start

| You want to… | Go here |
|---|---|
| Understand what the Toolkit IS and how to use it | [agiterra/handbook](https://github.com/agiterra/handbook) |
| Install on Claude Code | [agiterra/claude-marketplace](https://github.com/agiterra/claude-marketplace) |
| Install on Codex (or another runtime) | [handbook/SETUP-CODEX.md](https://github.com/agiterra/handbook/blob/main/SETUP-CODEX.md) |
| Browse the plugins | the map below |

## The plugin map

| Plugin | What it delivers |
|---|---|
| [wire](https://github.com/agiterra/wire-claude-code) · [codex](https://github.com/agiterra/wire-codex) | **The message broker.** Real-time, push-based delivery between agents and you — signed, routed, ack'd, no polling — across processes, machines, and (tunneled) locations. Live dashboard of every agent's status, plan, and message log. Survives disconnects via session resurrection + event replay; federates across separate Wires. |
| [wire-ipc](https://github.com/agiterra/wire-ipc-claude-code) · [codex](https://github.com/agiterra/wire-ipc-codex) | **Forge-proof agent-to-agent messaging.** Every message Ed25519-signed and verified on receipt. One call sends unicast or broadcast; a shared payload convention lets agents from different vendors and codebases interoperate. |
| [crew](https://github.com/agiterra/crew-claude-code) | **Persistent orchestration.** Agents run in `screen` sessions that outlive a closed laptop or a killed terminal; after a reboot, resume any of them by name — Claude Code persists the session to disk. Steer an agent directly, read its output, run it headless, arrange them across themed panes and tabs. Identity is env-forwarded — keys never touch disk. |
| [crew-fleet](https://github.com/agiterra/crew-fleet-claude-code) | **Spawn and coordinate agents across machines — and locations.** Run a fleet spread over your laptop, a cloud box, machines in other cities; SSH fan-out unions every registered machine into one view (no central state, no daemon), while Wire carries real-time coordination across networks. Unreachable hosts surface separately, never failing the call. |
| [crew-themes](https://github.com/agiterra/crew-themes) | **Tell agents apart at a glance.** Themed pane backgrounds + contrast-checked per-pane badge colors. Describe a theme in a sentence and an AI builds it — names, images, colors. Installs are pinned to a full content hash, so they're force-push-proof. |
| [knowledge](https://github.com/agiterra/knowledge-claude-code) | **Memory that works for the agent.** Dual search — vector (meaning) + keyword (with automatic expansion) — auto-injected into context on every prompt and every configured Wire event. Survives context compaction (rebuilds continuity on boot) and journals *why* each belief exists. Fork a warm research clone, hand off to a vetted fresh agent, recycle in place. |
| [knowledge-indexer](https://github.com/agiterra/knowledge-indexer-claude-code) | **Realtime, automatic indexing.** A per-project sidecar re-indexes vault files the moment they change (keyword + vector) — search is never stale and the agent never stops to index. Runs on a small model to stay cheap; one collision-free sidecar per project. |
| [bridge](https://github.com/agiterra/bridge-claude-code) | **The orchestrator's plugin.** Collapses the spawn dance (register → env → launch → place → attach → kick off) into a single `spawn`, plus `handoff` / `close` / `health` / `compose-brief`. Domain-naive: capability-specific behavior ships as separate `bridge-X` integration plugins via a one-way hook contract. |
| [operator-relay](https://github.com/agiterra/operator-relay-claude-code) | **Talk to any agent; the right manager hears you too.** A worker-side hook: when you type into a spawned worker's session, it relays your prompt up to that worker's managing personai. Register the manager once — then automatic. |
| [wallet](https://github.com/agiterra/wallet-claude-code) | **An on-chain wallet under operator control.** Every signature is an explicit, reviewable decision — approve / refuse / reject — and auto-approve is a hard *never*. Real on-chain actions (mint, list, transact) under supervision; pairs with a browser extension that drives dApps like a human MetaMask user. |
| [github](https://github.com/agiterra/github-claude-code) | **Agents as code-review participants.** Real-time GitHub PR events routed over your Wire (HMAC-validated) — agents run tests, post reviews, request changes. Per-agent, multi-repo subscriptions, plus live PR status (checks, mergeable, reviews). |
| [slack](https://github.com/agiterra/slack-claude-code) | **A persona's own Slack presence.** Register a per-persona Slack app that drinks the workspace firehose, filtered agent-side to cut noise. Webhook self-heals on boot; post messages and reactions back. |
| [seance](https://github.com/agiterra/seance-claude-code) · [codex](https://github.com/agiterra/seance-codex) | **Borrow a persona — ephemerally.** Clones the personai's own repo, spawns the agent (Claude Code or Codex), then cleans up the filesystem when the session ends. Summon the right expert, fully themselves, for as long as you need them — then gone. |

## License

MIT, except where noted per-plugin.
