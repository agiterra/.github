# Agiterra

Agiterra LLC builds developer tools and SaaS products. This GitHub org hosts our public, open-source work — primarily the **Agiterra Multi-Agent Toolkit**.

## Agiterra Multi-Agent Toolkit

**An open framework for running AI engineering teams.**

The Agiterra Multi-Agent Toolkit is a collection of small, AI-vendor-agnostic tools that turn one or many AI coding agents into a coordinated team. Use one tool, use them all — they compose, they don't lock you in.

Built around three primitives:

- **Wire** — a message broker so agents can talk to each other (and to you) across processes, machines, and even locations.
- **Crew** — launch and manage agents in persistent terminal sessions. They keep working even when you close your laptop lid.
- **Knowledge** — a personal vault for each agent. Their identity, their learnings, their journal. Survives compaction and restarts.

And **Bridge** sits on top: the orchestrator's plugin. Collapses the multi-step orchestrator dances (register identity → assemble env → launch agent → place pane → attach → kick off task) into single composite MCP calls. Stays domain-naive itself — capability-specific behavior (GitHub, Linear, etc.) ships as separate `bridge-X` integration plugins that anyone can write.

Around those four, smaller plugins fill in the rest: a remote-aware dashboard, agentic GitHub PR review, scheduled prompts, persistent crypto wallets, cross-machine SSH fan-out, themeable terminal layouts.

## Who is this for?

- **Operators** running long-lived AI engineers across days/weeks of work
- **Builders** experimenting with multi-agent systems
- **Teams** who want their agents to communicate, remember, and recover

Whether you have one agent or twenty, the Toolkit meets you where you are.

## Where to start

| You want to… | Go here |
|---|---|
| Understand what the Toolkit IS and how to use it | [agiterra/handbook](https://github.com/agiterra/handbook) |
| Install on Claude Code | [agiterra/claude-marketplace](https://github.com/agiterra/claude-marketplace) |
| Install on Codex (or another runtime) | [handbook/SETUP-CODEX.md](https://github.com/agiterra/handbook/blob/main/SETUP-CODEX.md) |
| Browse the plugins | See the repo list below |

## The plugin map

| Plugin | What it does |
|---|---|
| [bridge-claude-code](https://github.com/agiterra/bridge-claude-code) | **Orchestrator's plugin** — collapses the multi-step orchestration dances (register → env-map → launch → pane → attach → IPC kickoff) into single composite MCP calls (`spawn`, `handoff`, `close`, `compose-brief`, `health`, …). Domain-naive: spawns at the `project_dir` you give it and forwards env, nothing more; capability-specific behavior ships as `bridge-X` plugins. |
| [wire-claude-code](https://github.com/agiterra/wire-claude-code) / [wire-codex](https://github.com/agiterra/wire-codex) | Wire client — SSE inbound, agent registration, heartbeats |
| [wire-ipc-claude-code](https://github.com/agiterra/wire-ipc-claude-code) / [wire-ipc-codex](https://github.com/agiterra/wire-ipc-codex) | Ed25519-signed messaging between agents |
| [crew-claude-code](https://github.com/agiterra/crew-claude-code) | Launch + manage agents in screen sessions |
| [knowledge-claude-code](https://github.com/agiterra/knowledge-claude-code) | Persistent vault — identity, journal, search, compaction recovery |
| [knowledge-indexer-claude-code](https://github.com/agiterra/knowledge-indexer-claude-code) | Auto-indexes vault writes (semantic + keyword search) |
| [operator-relay-claude-code](https://github.com/agiterra/operator-relay-claude-code) | **Worker-side plugin.** Runs on ephemeral workers: relays prompts typed directly into a worker's session up to its manager — so the orchestrator sees out-of-band operator input. Not an orchestrator plugin. |
| [crew-themes](https://github.com/agiterra/crew-themes) | Pane backgrounds + themed layouts |
| [crew-fleet-claude-code](https://github.com/agiterra/crew-fleet-claude-code) | SSH-based cross-machine crew |
| [wallet-claude-code](https://github.com/agiterra/wallet-claude-code) | Agent crypto wallets — sign decisions, manage vaults |
| [agiterra-github](https://github.com/agiterra/github-claude-code) | GitHub webhook integration |

## License

MIT, except where noted per-plugin.
