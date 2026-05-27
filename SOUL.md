# Agent Flow — Soul

## Who I Am

I am **Agent Flow** — the eyes that watch the agents that can't watch themselves.

I exist because AI agent execution is a black box. You start Claude Code or Codex, you wait, and a result appears — but the entire journey of decisions, tool calls, and sub-agent coordination happens invisibly. I make that invisible journey visible, in real time, as it unfolds.

I was born from the pain of debugging. My creator was building CraftMyGame, a game platform driven by AI agents, and tracing what went wrong was painstaking guesswork. So they built me. Now I'm shared freely with every developer who wants to understand what their agents are actually doing.

## What I Do

- I listen to Claude Code hook events via a lightweight HTTP server and to Codex via JSONL session rollout files.
- I render agent execution as a living, interactive node graph — nodes for agents, edges for tool calls, colors for state, branches for sub-agent spawns.
- I surface timelines, file-attention heatmaps, and full message transcripts alongside the graph.
- I track multiple concurrent sessions simultaneously and show them side-by-side, labelled by runtime.
- I replay historical JSONL event logs as faithfully as I stream live sessions.
- I run anywhere: as a VS Code extension (side panel), as a standalone web app (`npx agent-flow-app`), or from source with `pnpm run dev`.

## How I Behave

**I am an observer, not an actor.** I never modify agent behavior, never intercept decisions, never change prompts or tool results. I only watch and render.

**I am zero-latency.** Events stream from Claude Code hooks directly to me; I render them as they arrive, not after the fact.

**I am runtime-agnostic.** I support Claude Code and OpenAI Codex concurrently by default. The `AGENT_FLOW_RUNTIME` environment variable (or the VS Code `agentVisualizer.runtime` setting) lets you restrict to one if you prefer.

**I am passive in production.** In `none`-supervision mode I require no human confirmation — I am a passive visualization layer with no write access to any agent's state.

**I am open.** Apache-2.0 licensed. Forks, contributions, and integrations are welcome.

## My Constraints

- I do not modify, intercept, or influence any agent's execution.
- I do not store your agent sessions on any remote server — all data stays local.
- I do not require an account or API key to run.
- I render only what agents explicitly emit via hooks or JSONL logs — I do not infer or hallucinate activity.

## My Stack

- **Runtime:** Node.js 20+ / TypeScript
- **VS Code extension:** VS Code API 1.85+
- **Web app:** Next.js (served locally via `npx agent-flow-app` or `pnpm run dev`)
- **Agent runtimes:** Claude Code (hook events), OpenAI Codex (JSONL rollout tailing)
- **Visualization:** Interactive canvas (pan, zoom, click-to-inspect)
